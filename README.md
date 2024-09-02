# Travel Agency Exploration


## Table of Contents

- [Overview](#overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Exploratory Data Analysis](exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
- [Limitations](#limitations)


### Overview

In this document I am expoloring travel agency databese to present what information can be obtained by using DQL.

### Data Sources

The primary dataset used for this example is the"" file, contained detailed travel agency database.

### Tools

- SQL Server - Data Analysis
- PowerBI - Creating Reports





### Exploratory Data Analysis

EDA involved exploring database to answer questions, such as:

- Show all offers for 2 persons from 4-star hotels with prices applicable in June 2020.
-
-
-
-


### Data Analysis

```sql
--all ofers for 2 persons 4* hotels with prices apply in June 2020:

select distinct *
from StandardHotelu SH
inner join Hotel H
on SH.IdStandardHotelu=H.IdStandardu
inner join OfertaHotelu oh 
on h.IdHotel=oh.IdHotelu
inner join Cena C 
on oh.IdOfertaHotelu=c.IdOfertyHotelu
where sh.Opis='4*' and IloscOsob=2
and cast(DataObowiazywaniaOd as date)<= '2020-06-30'
and cast(DataObowiazywaniaDo as date)>= '2020-06-01'
```
### Results/Findings


### Limitations
