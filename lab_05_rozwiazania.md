````sql
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

````sql
