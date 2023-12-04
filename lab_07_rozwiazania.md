````sql
#sum() , count() , inner join , left join

ZAD1.
a)   SELECT AVG(waga) FROM kreatura WHERE rodzaj="wiking" and waga is not null;;
b)  SELECT rodzaj,avg(waga) from kreatura group by rodzaj;
c)  SELECT rodzaj,avg(YEAR(CURRENT_DATE())-YEAR(dataUr)) FROM kreatura group by rodzaj;

ZAD2.
a) SELECT rodzaj,sum(waga) FROM zasob group by rodzaj;
b)  SELECT nazwa,avg(waga) FROM zasob group by nazwa having count(nazwa) >=4 and avg(waga) > 10 ;
c) 	SELECT nazwa,count(nazwa) FROM zasob group by nazwa having count(nazwa) > 1  ;

ZAD3.
a)SELECT `kreatura`.`nazwa`,CONCAT(`ekwipunek`.`idZasobu`,' , ' ,`ekwipunek`.`ilosc`) FROM kreatura,ekwipunek WHERE `kreatura`.`idKreatury` = `ekwipunek`.`idKreatury`;
b) SELECT kreatura.nazwa,zasob.nazwa FROM kreatura,zasob,ekwipunek WHERE kreatura.idKreatury = ekwipunek.idKreatury AND ekwipunek.idZasobu = zasob.idZasobu order by kreatura.nazwa desc;
c)  SELECT * FROM kreatura LEFT JOIN ekwipunek ON kreatura.idKreatury = ekwipunek.idKreatury WHERE ekwipunek.idKreatury IS NULL;

ZAD4.
a) SELECT kreatura.nazwa,zasob.nazwa from kreatura NATURAL JOIN zasob WHERE YEAR(kreatura.dataUr) between  
````
