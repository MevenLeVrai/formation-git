
```SQL
CREATE DATABASE IF NOT EXISTS e_commerce;
USE e_commerce;

CREATE TABLE article (
id INT AUTO_INCREMENT,
nom VARCHAR(50) NOT NULL,
prix DECIMAL(10,2) NOT NULL,
CONSTRAINT kp_article PRIMARY KEY (id)
);

CREATE TABLE client(
id INT AUTO_INCREMENT,
nom VARCHAR(50) NOT NULL,
prenom VARCHAR(50) NOT NULL,
CONSTRAINT kp_client PRIMARY KEY (id)
);

CREATE TABLE commande(
id INT AUTO_INCREMENT,
jour DATETIME NOT NULL,
quantite INT NOT NULL,
id_article INT NOT NULL,
id_client INT NOT NULL,
CONSTRAINT fk_article FOREIGN KEY (id_article) 
	REFERENCES article(id),
CONSTRAINT fk_client FOREIGN KEY (id_client) 
	REFERENCES client(id),
CONSTRAINT kp_commande PRIMARY KEY (id)
);
```

```SQL
USE e_commerce;

INSERT INTO article (nom, prix) VALUES
('PlayStation 5', 400.00),
('X box', 350.00),
('Machine à café', 300.00),
('PlayStation 3', 100.00);

INSERT INTO client (nom, prenom) VALUES
('Brad', 'PITT'),
('George', 'Cloney'),
('Jean', 'DUJARDIN');

```

```SQL
SELECT client.prenom,client.nom,commande.jour, 
article.nom AS "Article", 
commande.quantite AS "Nombre",
article.prix AS "Prix Unitaire",
(commande.quantite * article.prix) AS "Total HT"

FROM commande 
INNER JOIN client ON commande.id_client = client.id
INNER JOIN article ON commande.id_article = article.id;
```