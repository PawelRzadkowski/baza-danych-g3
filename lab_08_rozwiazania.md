````sql
ZAD1.
a) CREATE table uczestnicy SELECT * FROM wikingowie.uczestnicy;
CREATE TABLE etapy_wyprawy SELECT * FROM wikingowie.etapy_wyprawy;
CREATE TABLE sektor SELECT * FROM wikingowie.sektor;
CREATE TABLE wyprawa SELECT * FROM wikingowie.wyprawa;

b)SELECT nazwa FROM kreatura WHERE kreatura.nazwa not in(SELECT distinct kreatura.nazwa from kreatura,uczestnicy,wyprawa WHERE kreatura.idKreatury = uczestnicy.id_uczestnika);

c)


````
