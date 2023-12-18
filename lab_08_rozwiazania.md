````sql
ZAD1.
a) CREATE table uczestnicy SELECT * FROM wikingowie.uczestnicy;
CREATE TABLE etapy_wyprawy SELECT * FROM wikingowie.etapy_wyprawy;
CREATE TABLE sektor SELECT * FROM wikingowie.sektor;
CREATE TABLE wyprawa SELECT * FROM wikingowie.wyprawa;

b)SELECT nazwa FROM kreatura WHERE kreatura.nazwa not in(SELECT distinct kreatura.nazwa from kreatura,uczestnicy,wyprawa WHERE kreatura.idKreatury = uczestnicy.id_uczestnika);

c)

ZAD2.
a)

b)
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
