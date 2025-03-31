```SQL 
CREATE DATABASE IF NOT EXISTS netflix;
USE netflix;
CREATE TABLE IF NOT EXISTS film(
id INT NOT NULL AUTO_INCREMENT,
titre VARCHAR(50) NOT NULL,
sortie DATE NOT NULL,
id_categ INT ,
CONSTRAINT pk_film PRIMARY KEY (id)
);

CREATE TABLE IF NOT EXISTS categ(
id INT NOT NULL AUTO_INCREMENT,
categorie VARCHAR(50) NOT NULL,
CONSTRAINT pk_categ PRIMARY KEY (id)
);

INSERT INTO netflix.film (titre, sortie,id_categ) 
VALUES ('STAR WARS',1977-05-25,1),
('THE MATRIX',1999-06-23,1),
('PULP FICTION', 1994-10-26,2);

INSERT INTO netflix.categ (cartegorie)
VALUES ('Science Fiction'),
('Thriller')


```

```SQL
SELECT titre,sortie,categorie FROM netflix.film
INNER JOIN netflix.categ
ON categ.id = film.id_categ
WHERE categ.id = 1;
```