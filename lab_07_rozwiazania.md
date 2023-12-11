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
a) SELECT kreatura.nazwa,zasob.nazwa FROM kreatura,ekwipunek,zasob WHERE kreatura.dataUr >"1669-12-31" and kreatura.dataUr <="1679-12-31" and kreatura.idKreatury=ekwipunek.idKreatury and ekwipunek.idZasobu=zasob.idZasobu and zasob.nazwa ="jedzenie";
b) SELECT kreatura.nazwa FROM kreatura,ekwipunek,zasob WHERE kreatura.idKreatury = ekwipunek.idKreatury and ekwipunek.idZasobu = zasob.idZasobu and zasob.rodzaj="jedzenie" order by kreatura.dataUr asc limit 5;
c) SELECT CONCAT(k1.nazwa," - ",k2.nazwa) FROM kreatura k1, kreatura k2 WHERE k1.idKreatury - k2.idKreatury=5;

ZAD5.
a)SELECT kreatura.nazwa,kreatura.rodzaj,AVG(ekwipunek.ilosc * zasob.waga) FROM kreatura INNER JOIN ekwipunek on kreatura.idKreatury=ekwipunek.idKreatury INNER JOIN zasob ON zasob.idZasobu=ekwipunek.idZasobu WHERE kreatura.rodzaj not in("malpa","waz") AND ekwipunek.ilosc < 30 group by kreatura.rodzaj  ;
b)  SELECT 'najmlodsza',a.maxData,b.nazwa,a.rodzaj from (select max(dataUr) maxData, rodzaj from kreatura group by rodzaj) a, (select nazwa, dataUr from kreatura) b
 where a.maxData = b.dataUr union SELECT 'najstarsza',a.minData,b.nazwa,a.rodzaj from(select min(dataUr) minData, rodzaj from kreatura group by rodzaj) a,(SELECT nazwa,dataUr from kreatura) b WHERE a.minData=b.dataUr ;

#bez union
# SELECT 'najmlodsza',a.maxData,b.nazwa,a.rodzaj from (select max(dataUr) maxData, rodzaj from kreatura group by rodzaj) a, (select nazwa, dataUr from kreatura) b
# where a.maxData = b.dataUr union SELECT 'najstarsza',a.minData,b.nazwa,a.rodzaj from(select min(dataUr) minData, rodzaj from kreatura group by rodzaj) a,(SELECT nazwa,dataUr from kreatura) b WHERE a.minData=b.dataUr ;

````
