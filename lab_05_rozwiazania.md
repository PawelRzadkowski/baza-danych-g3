````sql
ZAD 1.
a) SELECT * FROM postac WHERE rodzaj="wiking" and nazwa !="Bjorn" order by wiek DESC;
DELETE FROM postac WHERE id_postaci in (8,7);

b) SET foreign_key_checks= 0;
#problem 1 auto_increment
ALTER TABLE postac change id_postaci id_postaci int;

ZAD 2.

````sql
