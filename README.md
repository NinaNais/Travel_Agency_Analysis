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


### Exploratory Data Analysis

EDA involved exploring database to answer questions, such as:

- Show all offers for 2 persons from 4-star hotels with prices applicable in June 2020
- How many purchases were made for an amount higher than the average purchase amount?
- How many hotels are there in each standard?
- Show 2 hotels with the most amenities


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

```sql

-- amount of purchases higher than the avg purchase amount--
declare @avgprice as decimal(10,2)
select  @avgprice= avg(cena)
from Zakup
select count(*)
from Zakup
where cena>@avgprice
```

```sql
--  amount of hotels in each standard--

select sh.opis,count(h.IdHotel)as Liczba_hoteli
from Hotel H 
right join StandardHotelu SH 
on h.IdStandardu=sh.IdStandardHotelu
group by sh.Opis
```

```sql
--Show 2 hotels with the most amenities--

select top 2 h.nazwa,count (distinct uh.IdUdogodnienia) as Liczba_udogodnień
from UdogodnieniaHotelu uh
inner join Udogodnienia u
on uh.IdUdogodnienia=u.IdUdogodnienia
inner join Hotel h
on uh.IdHotelu=h.IdHotel
group by h.Nazwa
order by Liczba_udogodnień desc
```

### Results/Findings


### Limitations
