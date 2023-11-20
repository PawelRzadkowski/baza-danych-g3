````sql
Komendy
#SELECT * FROM postac where nazwa regexp
#SELECT * FROM postac where nazwa regexp "a"; #"[0-9]{1,2}-[0-9]{3}" [0-9] oznacza dowolna cyfre ze zbioru , [a-k] oznacza litery od a do k , [aoi] jeden ze znakow  , {} okreslenie krotnosci , {n} dokladnie n razy -
# {n,m} nie wiecej jak m razy , {m,} co najmniej m razy
#2 sposob between where data_wodowania between "1701-01-01" and "1800-12-31" between razem z warunkiem , where year(data_wodowania) date przetworzone na year
#Create table  marynarz like postac

ZAD 1.
a) SELECT * FROM postac WHERE rodzaj="wiking" and nazwa !="Bjorn" order by wiek DESC;
DELETE FROM postac WHERE id_postaci in (8,7);

b) SET foreign_key_checks= 0;
#problem 1 auto_increment
ALTER TABLE postac change id_postaci id_postaci int;
alter table walizka drop foreign key walizka_ibfk_1;
ALTER TABLE przetwory drop foreign key przetwory_ibfk_1;
ALTER TABLE przetwory drop foreign key przetwory_ibfk_2;
SET foreign_key_checks= 1;

ZAD 2.
ALTER TABLE postac ADD pesel CHAR(11) first;
UPDATE postac SET pesel="12345678901" + id_postaci;
ALTER TABLE postac add primary key(pesel);

ALTER TABLE postac modify rodzaj enum("wiking","ptak","kobieta","syrena");
INSERT into postac values("12341234123","60","Gertruda_nieszczera","syrena","768-05-05","567",NULL,NULL);

ZAD 3.
a)UPDATE postac set nazwa_statku ="czarna_perla" where nazwa LIKE "%a%" ;
b)UPDATE statek set max_ladownosc=max_ladownosc*0.7 WHERE data_wodowania >= "1701-01-01" and data_wodowania <="1800-12-31"; 
c)ALTER TABLE postac modify wiek int unsigned check (wiek < 1000);

ZAD 4.
a)ALTER TABLE postac modify rodzaj enum("wiking","ptak","kobieta","syrena","wąż");
INSERT INTO postac values("19819819816","34","Loko","wąż","1506-06-06","789","wąż morski",NULL);

b)CREATE TABLE marynarz like postac;
INSERT INTO marynarz SELECT * from postac where statek is not null;

c)ALTER TABLE marynarz ADD FOREIGN KEY(nazwa_statku) references statek(nazwa_statku);

ZAD 5.
a)UPDATE postac set nazwa_statku=NULL WHERE nazwa_statku is not null;
UPDATE marynarz set nazwa_statku=NULL WHERE nazwa_statku is not null;
b)DELETE FROM postac WHERE nazwa="Gorn";
c)ALTER TABLE postac drop FOREIGN KEY postac_ibfk_1;
ALTER TABLE marynarz drop FOREIGN KEY marynarz_ibfk_1;
DELETE FROM statek where data_wodowania LIKE "%";
d)DROP TABLE statek;
e)CREATE TABLE zwierz (
id int unsigned primary key not null auto_increment,
nazwa varchar(100),
wiek int unsigned
);
f)INSERT INTO zwierz SELECT id_postaci,nazwa,wiek FROM postac WHERE rodzaj in ("ptak","wąż"); 

````sql
