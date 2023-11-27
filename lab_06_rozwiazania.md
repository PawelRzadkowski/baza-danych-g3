````sql
Zad 1.
a)CREATE TABLE kreatura SELECT * FROM wikingowie.kreatura;
CREATE TABLE ekwipunek SELECT * FROM wikingowie.ekwipunek;
CREATE TABLE zasob SELECT * FROM wikingowie.zasob;

b)SELECT * FROM zasob;

c)SELECT * FROM zasob WHERE rodzaj="jedzenie";

d)SELECT nazwa FROM kreatura WHERE idKreatury in (1,3,5) ;

ZAD 2.
a)SELECT * FROM kreatura WHERE not rodzaj="wiedzma" AND waga > 60;
b)SELECT * FROM zasob WHERE waga between 2 AND 5;
c)SELECT * FROM kreatura WHERE nazwa LIKE "%or%" AND waga between 30 AND 70;

ZAD 3.
a)SELECT * FROM zasob WHERE MONTH(dataPozyskania) between 7 AND 8;
b)SELECT * FROM zasob WHERE rodzaj is NOT NULL order by waga asc;
c)SELECT * FROM kreatura WHERE dataUr is not null order by dataUr asc LIMIT 5;

ZAD4.
a)SELECT DISTINCT rodzaj FROM zasob;
b)SELECT CONCAT(nazwa ,'' , rodzaj) FROM kreatura WHERE rodzaj LIKE "wi%";
c)SELECT waga*ilosc,idZasobu,nazwa FROM zasob WHERE YEAR(dataPozyskania) between 2000 AND 2007;

ZAD5.
a)SELECT idZasobu,nazwa,waga*ilosc*0.7,waga*ilosc*0.3 FROM zasob WHERE rodzaj="jedzenie";
b)SELECT * FROM zasob WHERE rodzaj IS NULL;
c)SELECT DISTINCT rodzaj FROM zasob WHERE nazwa LIKE "Ba%" AND nazwa LIKE "%os" order by rodzaj asc;
````
