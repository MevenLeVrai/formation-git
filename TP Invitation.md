```SQL
CREATE DATABASE IF NOT EXISTS invitation CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

USE invitation;

DROP TABLE IF EXISTS personne;

CREATE TABLE IF NOT EXISTS personne (
    pers_id INT NOT NULL AUTO_INCREMENT,
    pers_prenom VARCHAR(100),
    pers_nom VARCHAR(100),
    pers_age INT,
    pers_inscription DATE,
    pers_statut TINYINT,
    pers_type ENUM('non membre', 'membre'),
    pers_description TEXT,
    pers_salaire INT,
    CONSTRAINT kp_id PRIMARY KEY (pers_id)
);

INSERT INTO personne 
(pers_prenom, pers_nom, pers_age, pers_inscription, pers_statut, pers_type, pers_description, pers_salaire) 
VALUES 
('Brad', 'PITT', 60, '1970-01-01', 1, 'non membre', 'lorem ipsum', 2000000),
('George', 'CLONEY', 62, '1999-01-01', 1, 'membre', 'juste beau', 4000000),
('Jean', 'DUJARDIN', 51, '1994-01-01', 0, 'membre', 'brice de nice', 1000000);



```

```SQL
SELECT * FROM personne;
```
![[Pasted image 20250325132630.png]]