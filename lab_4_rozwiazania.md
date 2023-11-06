# Tytul
## Poziom2
###### Poziom6

Lista zadań do wykonania
* todo1
* todo2
  * todo2.1

1. Rozdzial 1
2. Rozdzial 2
  2.1 Rozdzial 2.1

**Listing 1** ->pogrubienie  
_Listing2_ ->kursywa

**_Listing3_** 

Ponizej to blok kodu.  
```` sql

SELECT *  FROM osoba;
````

Kod umieszczany liniowo.Polecenie `SELECT` oznacza wybranie danych z bazy

create table postac (
id_postaci int primary key auto_increment,
nazwa varchar(40),
rodzaj enum("wiking","ptak","kobieta"),
data_ur date,
wiek int unsigned
);

show create table postac;

insert into postac values(NULL,"Bjorn","wiking","1700-10-23",323);
insert into postac values(NULL,"drozd","ptak","1999-06-01",20);
insert into postac values(NULL,"tesciowa","kobieta","966-08-08",1098);
update postac set wiek=88 WHERE nazwa="tesciowa";

CREATE TABLE walizka (
id_walizki int primary key auto_increment,
pojemnosc int unsigned,
kolor enum("rozowy","czerwony","teczowy","zolty"),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade
);

ALTER TABLE walizka alter kolor set default "rozowy"; 

INSERT INTO walizka values (NULL,10,NULL,1) , INSERT INTO walizka(pojemnosc,id_wlasciciela) values (20,3);

CREATE TABLE izba (
adres_budynku varchar(50),
nazwa_izby varchar(60),
metraz int unsigned,
wlasciciel int,
primary key(adres_budynku, nazwa_izby),
foreign key (wlasciciel) references postac(id_postaci) on delete set null
);

ALTER TABLE izba ADD kolor_izby varchar(40) after metraz;
ALTER TABLE izba alter kolor_izby set default "czarny";
INSERT INTO izba values("domowa","dom",20,default,1);

CREATE TABLE przetwory (
id_przetworu int primary key,
rok_produkcji YEAR default=1654,
id_wykonawcy int,
zawartosc varchar(60),
dodatek varchar(60) default "papryczka chilli",
id_konsumenta int,
FOREIGN KEY (id_wykonawcy) references postac(id_postaci),
FOREIGN KEY (id_konsumenta) references postac(id_postaci)
);
