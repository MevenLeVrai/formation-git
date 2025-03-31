```SQL
CREATE DATABASE IF NOT EXISTS zoo 
CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

USE zoo;
CREATE TABLE IF NOT EXISTS chats(
id INT NOT NULL AUTO_INCREMENT,
nom VARCHAR(50) NOT NULL,
yeux VARCHAR(20) NOT NULL,
age TINYINT NOT NULL,
CONSTRAINT kp_id PRIMARY KEY (id)
)ENGINE=INNODB
```

```SQL
INSERT INTO chats (nom,yeux,age) VALUES 
("Mainecoon","marron",20),
("Siamois","bleu",15),
("Bengal","marron",18),
("ScottishFold","marron",10);
```


## Suite des chats 
```SQL
CREATE DATABASE IF NOT EXISTS spa 
CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

USE spa;
CREATE TABLE IF NOT EXISTS chats(
id INT NOT NULL AUTO_INCREMENT,
nom VARCHAR(50) NOT NULL,
age TINYINT NOT NULL,
couleur_id INT,
CONSTRAINT kp_id PRIMARY KEY (id)
)ENGINE=INNODB;

CREATE TABLE IF NOT EXISTS couleur(
id INT NOT NULL AUTO_INCREMENT,
nom VARCHAR(50),
CONSTRAINT kp_id PRIMARY KEY (id)
)ENGINE=INNODB
```

```SQL 
SELECT chats.id, chats.nom, chats.age, couleur.nom
FROM chats
INNER JOIN couleur
ON chats.couleur_id = couleur.id;
```
![[Pasted image 20250325142241.png]]
```SQL
SELECT chats.id, chats.nom, chats.age, couleur.nom
FROM chats
LEFT JOIN couleur
ON chats.couleur_id = couleur.id;
```
![[Pasted image 20250325142214.png]]
```SQL
SELECT chats.id, chats.nom, chats.age, couleur.nom
FROM chats
LEFT JOIN couleur ON chats.couleur_id = couleur.id
WHERE chats.couleur_id IS NULL;
```
![[Pasted image 20250325144142.png]]

```SQL
SELECT couleur.nom AS couleur, COUNT(chats.id) AS nb_chat
FROM couleur
INNER JOIN chats ON chats.couleur_id = couleur.id
GROUP BY couleur.nom;
```
![[Pasted image 20250325155205.png]]

```SQL
SELECT couleur.nom AS couleur, COUNT(chats.id) AS nb_chat
FROM couleur
LEFT JOIN chats ON chats.couleur_id = couleur.id
GROUP BY couleur.nom;
```
![[Pasted image 20250325154102.png]]
