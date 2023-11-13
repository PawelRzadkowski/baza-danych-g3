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
````sql
ZAD1.
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

ZAD 3.
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
INSERT INTO izba values("spizarniowa","spizarnia","30","czarny","1");

ZAD4.
CREATE TABLE przetwory ( 
id_przetworu int primary key,
 rok_produkcji YEAR,
 id_wykonawcy int,
 zawartosc varchar(60),
 dodatek varchar(60) ,
 id_konsumenta int,
 FOREIGN KEY (id_wykonawcy) references postac(id_postaci),
 FOREIGN KEY (id_konsumenta) references postac(id_postaci) ); 

 ALTER TABLE przetwory alter rok_produkcji set default 1654;
 ALTER TABLE przetwory alter dodatek set default "papryczka chilli";
 INSERT INTO przetwory values(1,"2050","1","bigos",default,"3");

ZAD5.podpunkt 1
  INSERT INTO postac values(
 (NULL , "Asgard","wiking","1678-08-12",20),
 (NULL, "Khorad","wiking","1864-03-12",30),
 (NULL, "Gorn","wiking","1864-03-16",40),
 (NULL, "Diego","wiking","1864-03-22",50),
 (NULL, "Gomez","wiking","1864-03-12",60)
);

ZAD5.podpunkt 2
CREATE TABLE statek (
 nazwa_statku varchar(50) primary key,
 rodzaj_statku enum("kajak","statek","kuter","lodz"),
 data_wodowania DATE,
 max_ladownosc int unsigned
);

ZAD5.podpunkt 3
INSERT INTO statek values("swieta_anna","statek","1754-09-09","3000");
INSERT INTO statek values("czarna_perla","statek","1785-06-06","2000");

ZAD5.podpunkt 4
ALTER TABLE postac ADD funkcja varchar(70);

ZAD5.podpunkt 5
UPDATE postac set funkcja="kapitan" where id_postaci ="1";

ZAD5.podpunkt 6
ALTER TABLE postac ADD nazwa_statku varchar(50);
ALTER TABLE postac ADD FOREIGN KEY (nazwa_statku) references statek(nazwa_statku) on delete set null;

ZAD5.podpunkt 7
UPDATE postac set nazwa_statku="czarna_perla" WHERE id_postaci="1";
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=2;
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=4;
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=5;
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=6;
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=7;
UPDATE postac set nazwa_statku="swieta_anna" WHERE id_postaci=8;

ZAD5.podpunkt 8
DELETE FROM izba where adres_budynku = "spizarniowa";

ZAD5.podpunkt 9
DROP TABLE izba;
````sql
