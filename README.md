# Fluxo-completo-de-uma-pipeline-ETL
o fluxo completo de uma pipeline ETL integrando várias ferramentas: SQLite, DBeaver, Pentaho, e Data Mining.

Primeiro Instale os softwares: MonetDb, Dbvear, Pentaho integration, Java, (Sqlite Banco)

Ligue o Servidor: Disco Local> Arquivos e Programas> Monetdb> Monetdb> e aperte em "M5server"

baixe o database sqlite de 1GB que seria o Banco de dados Com os indicators

Link pra baixar: https://www.kaggle.com/datasets/kaggle/world-development-indicators?resource=download&select=database.sqlite

Crie Duas Conexões: 

- Sqite e coloque no caminho o Banco sqlite de 1GB

- Crie o Localhost e teste

crie o datamining dentro do localhost

Escolha um Tema de Indicators no CASO meu é a pobreza = Poverty


Pesquise e Procure  e execute o Máximo de Indicators que vc conseguir pelo Sqlite Criado 

--indictors 

3 Improved sanitation facilities (% of population with access)
4 Improved sanitation facilities, rural (% of rural population with access)
5 Improved sanitation facilities, urban (% of urban population with access)
 Investment in water and sanitation with private participation (current US$)

Improved sanitation facilities (% of population with access)
Improved sanitation facilities, rural (% of rural population with access)
Improved sanitation facilities, urban (% of urban population with access)
2 Improved water source (% of population with access)
Improved water source, rural (% of rural population with access)
1 Improved water source, urban (% of urban population with access)


Depois Teste Todos os Indicators  e execute, Dessa Forma:

--poverty
select * from indicators i
where IndicatorName like '%poverty%'
GROUP BY IndicatorName 


--sanitation
select * from indicators i
where IndicatorName like '%sanitation%'
GROUP BY IndicatorName 

--improved
select * from indicators i
where IndicatorName like '%improved%'
GROUP BY IndicatorName 

Encontre 5 no Mínimo 

Depois dos indicators Estarem Funcionando 

Crie o Dataset e execute

--dataset
SELECT  
    coe.CountryName, 
    coe."Year",
    coe.Value AS 'Improved water source, urban (% of urban population with access)',
    lf.Value  AS 'Improved water source (% of population with access)',
    grn.Value AS 'Improved sanitation facilities (% of population with access)',
    agr.Value AS 'Improved sanitation facilities, rural (% of rural population with access)',
    sf.Value  AS 'Improved sanitation facilities, urban (% of urban population with access)'

FROM Indicators AS coe

INNER JOIN Indicators AS lf
    ON coe.CountryName = lf.CountryName 
   AND coe."Year" = lf."Year"

INNER JOIN Indicators AS grn
    ON lf.CountryName = grn.CountryName 
   AND lf."Year" = grn."Year"

INNER JOIN Indicators AS agr
    ON grn.CountryName = agr.CountryName 
   AND grn."Year" = agr."Year"

INNER JOIN Indicators AS sf
    ON agr.CountryName = sf.CountryName 
   AND agr."Year" = sf."Year"

WHERE 
    coe.IndicatorName = 'Improved water source, urban (% of urban population with access)'
AND lf.IndicatorName = 'Improved water source (% of population with access)'
AND grn.IndicatorName = 'Improved sanitation facilities (% of population with access)'
AND agr.IndicatorName = 'Improved sanitation facilities, rural (% of rural population with access)'
AND sf.IndicatorName = 'Improved sanitation facilities, urban (% of urban population with access)'


depois no Local host

crie a tabela dentro do Datamining e execute

create table Povertyano (
CountryName varchar (255),
"ano" Integer,
"Improved water source, urban (% of urban population with access)" Double,
"Improved water source (% of population with access)" Double,
"Improved sanitation facilities (% of population with access)" Double,
"Improved sanitation facilities, rural (% of rural population with access)" Double,
"Improved sanitation facilities, urban (% of urban population with access)" Double
)


Vá para o Spoon ele estará dentro da pasta data integration 

o Restante vai estar nesses videos de 01 a 09 partes explicando um pouco melhor, acesse o link abaixo

https://youtu.be/j6RAIShkvGw?si=S0xeIdPRc25SaI5i








  

  






