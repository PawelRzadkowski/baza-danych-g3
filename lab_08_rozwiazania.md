````sql
ZAD1.
a) CREATE table uczestnicy SELECT * FROM wikingowie.uczestnicy;
CREATE TABLE etapy_wyprawy SELECT * FROM wikingowie.etapy_wyprawy;
CREATE TABLE sektor SELECT * FROM wikingowie.sektor;
CREATE TABLE wyprawa SELECT * FROM wikingowie.wyprawa;

b)SELECT nazwa FROM kreatura WHERE kreatura.nazwa not in(SELECT distinct kreatura.nazwa from kreatura,uczestnicy,wyprawa WHERE kreatura.idKreatury = uczestnicy.id_uczestnika);

c) SELECT wyprawa.nazwa, FROM kreatura LEFT JOIN 

ZAD2.
a) SELECT wyprawa.nazwa, COUNT(uczestnicy.id_uczestnika), GROUP_CONCAT(kreatura.nazwa) AS 'imiona_uczestnikow' FROM uczestnicy LEFT JOIN wyprawa 
ON wyprawa.id_wyprawy=uczestnicy.id_wyprawy LEFT JOIN kreatura ON kreatura.idKreatury=uczestnicy.id_uczestnika GROUP BY wyprawa.nazwa;

b) SELECT etapy_wyprawy.dziennik, sektor.nazwa, wyprawa.data_rozpoczecia, wyprawa.kierownik FROM wyprawa LEFT JOIN etapy_wyprawy 
ON etapy_wyprawy.idWyprawy=wyprawa.id_wyprawy LEFT JOIN sektor ON etapy_wyprawy.sektor=sektor.id_sektora ORDER BY wyprawa.data_rozpoczecia, etapy_wyprawy.kolejnosc;

ZAD3.
a) SELECT ew.sektor ,count(ew.sektor) from etapy_wyprawy ew inner join sektor s on ew.sektor=s.id_sektora group by sektor;

b)SELECT k.nazwa,if(count(u.id_wyprawy)=0,'nie bral udzialu w wypraiwe','bral udzial w wypraiwe') as czy_wyprawa FROM kreatura k left join uczestnicy u on u.id_uczestnika=k.idKreatury group by k.nazwa;

ZAD4.
a)SELECT idWyprawy,sum(length(dziennik)) FROM etapy_wyprawy group by idWyprawy having sum(length(dziennik)) < 400;

b)SELECT u.id_wyprawy,w.nazwa,
count(id_uczestnika) ile_zle,
count(distinct id_uczestnika) ile_dobrze,
sum(e.ilosc * z.waga) suma_wagi,
sum(e.ilosc*z.waga) /count(distinct u.id_uczestnika) avg_dobre,
sum(e.ilosc * z.waga) /count(u.id_uczestnika) avg_zle
FROM uczestnicy unionINNER JOIN ekwipunek e on u.id  .....
````
