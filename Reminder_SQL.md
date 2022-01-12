# SQL

PstgreSQL`, MySQL, Oracle: SGBD - Plateform, logiciel de base de donnée, facile à installer pour apprendre SQL

SQL: Langage de programmation

- Opération de comparaison: 
`=`, `<`, `>`, `<=`, `>=`, `!=`, `<>`.
- Opération `AND` et `OR`.
- WHERE s'applique sur chaque ligne et avant l'application de GROUP BY. Alors que, HAVING crée une condition sur un groupe de lignes GROUP BY.
- `ORDER BY ACS` (default) or `DESC`.
- Count: Permet de compter le nb de ligne et retourne le nbr de valeurs différentes de null de colonne
- IN s'utilise avec `WHERE`.
- `LIKE xx%xx`: Plusieurs caractères, `xx_xx`: Un caractère.
- `colonne BETWEEN min AND max` <=> `colonne >= min AND colonne <= max` (BETWEEN plus lisible).
- UNION, même colonne dan les deux tables
- Join
    ![Join.png](Join.png)
```SQL
SELECT first_name, last_name FROM actor; 

SELECT first_name, last_name 
FROM actor
WHERE first_name = 'Nick' AND last_name = 'Stallone';

SELECT first_name, last_name 
FROM actor
ORDER BY last_name ASC, first_name DESC
LIMIT 3;

SELECT DISTINCT rating  
FROM film;

-- Nombre de ligne
SELECT COUNT(title) FROM film; 

SELECT COUNT(DISTINCT(rental_rate)) FROM film;

SELECt rental_id, customer_id, return_date FROM rental
WHERE customer_id IN (3, 6)
ORDER BY renturn_date;

-- Marche aussi, si customer_id n est pas dans le SELECT
SELECt rental_id FROM rental 
WHERE customer_id IN (3, 6)
ORDER BY renturn_date;

SELECt COUNT(title) FROM actor 
WHERE title LIKE '%Truman%';

SELECt ROUND(AVG(amount), 1) as average_amout FROM payment; 

SELECT customer_id, COUNT(*) FROM rental:
GROUP BY customer_id
ORDER BY COUNT(*) DESC;

SELECT stuff_id, COUNT(amout), SUM(amount)  FROM payment:
GROUP BY stuff_id
ORDER BY stuff_id DESC
LIMIT 3;

-- Client qui ont dépensé plus de 500 $
SELECT customer_id, COUNT(amout), SUM(amount)  FROM payment:
GROUP BY customer_id
HAVING BY SUM(amount) > 500;

-- Client qui ont dépensé plus de 500 $
SELECT rating, ROUND(AVG(rental_rate), 2)
FROM film
-- Avant GROUP BY
WHERE rating IN ('R', 'G', 'PG')
GROUP BY rating
HAVING BY AVG(rental_rate) > 2.9;

-- L acteur le plus représenté dans les films de ce magasin

SELECT a.first_name, a.last_name, SUM(f.title)
FROM acteur AS a
INNER JOIN film_actor AS fa ON a.actor_id = fa.actor_id
INNER JOIN film AS f  ON fa.film_id = f.film_id
GROUP BY a.actor_id
ORDER BY SUM(f.title) DESC;

-- Client qui ont loué au moins 38 films 

SELECT c.first_name, COUNT(r.rental_id)
FROM customer AS c
INNER JOIN rental AS r ON c.customer_id = r.customer_id 
INNER JOIN rental AS r ON c.customer_id = r.customer_id 
GROUP BY c.customer_id
HAVING COUNT(r.rental_id) >= 30

-- Quelle catégorie a le plus de location

Inventory
Rental

SELECT c.name AS category, COUNT(r.rental_id)
FROM category AS c
INNER JOIN film_category AS fc ON c.category_id = fc.category_id
INNER JOIN film AS f ON fc.film_id = f.film_id
INNER JOIN inventory AS i ON f.film_id = i.film_id
INNER JOIN rental AS r ON r.inventory_id = i.inventory_id
WHERE name not in ('ANIMATION', 'COMEDY')
GROUP BY name
ORDER BY COUNT(r.rental_id)
ORDER BY COUNT(r.rental_id) DESC;

--  Titre de film de langue anglaise qui ont eu plus de 30 location

SELECT f.title, SUM(r.rental_id)
FROM languages AS l
INNER JOIN film AS f ON f.language_id = l.language_id
INNER JOIN film AS f ON fc.film_id = f.film_id
INNER JOIN inventory AS i ON f.film_id = i.film_id
INNER JOIN rental AS r ON r.inventory_id = i.inventory_id
WHERE l.name = 'ENGLISH'
GROUP BY f.title
HAVING BY SUM(r.rental_id) >= 30;

-- Les films qui rapportent le plus
-- Revenu(film) = Prix_location * Nbr_location


SELECT title, COUNT(rental_rate) AS nb_rentals, COUNT(rental_id) * rental_rate AS revenue
FROM film as f
INNER JOIN iventory AS i ON f.film_id = i.film_id
INNER JOIN rental AS r i.inventory_id = r.iventory_id
GROUP BY title, rental_rate;
```

**Lookup** pour récupérer la valeur du dataset spécifié pour une paire nom/valeur où il y a une relation un-à-un

# Rank vs Dense Rank
Function | Rank | Dense Rank
--- | -----|-----
Example | 1 - 1 - 3 - 4 - 5 |  1 - 1 - 2 - 3 - 4  
Syntax | RANK() OVER (ORDER BY col1, col2,...) | DENSE_RANK() OVER (ORDER BY col1, col2,...)

```SQL
SELECT name, gender, salary, RANK() OVER (ORDER BY salary DESC) as rank
(ORDER BY salary DESC) AS denserank
FROM Employees
```

![Rank_Dense-RANK.png](Image/Rank_Dense-RANK.png)
![Rank_Dense-RANK_with_partition.png](Images/Rank_Dense-RANK_with_partition.png)


- CASE.. WHEN... <=> IF... ELSE...

```SQL
------------------------------------------------
--- 1. Comparer une colonne à un SET de résultat ---

CASE a --Les valeurs contenues dans la colonne 'a' sont comparé à 1, 2
    WHEN 1 THEN 'un'
    WHEN 2 THEN 'deux
    ELSE 'autre
END
-- OR

CASE 
    WHEN a=1 THEN 'un'
    WHEN a=2 THEN 'deux
    ELSE 'autre
END

------------------------------------------------------------------------------------
--- 1. Elaborer une série de conditions booléennes pour déterminer un résultat  ---

CASE a -- Comparer les valeurs numerique de la colonne A et B
    WHEN a=b THEN 'a égale à b'
    WHEN a<b THEN 'a inf à b'
    ELSE 'a sup à b'
END

--- Tableau ACHAT, Colonnes: ID, NOM, MARGE, ...
--- Requète qui va afficher un message personnalisé en fonction de la valeur de la marge.
SELECT id, nom, marge
    CASE 
        WHEN marge = 1 THEN 'prix ordinaire'
        WHEN marge > 1 THEN 'prix supérieur à la normale'
        ELSE 'Prix inférieur à la normale'
    END AS marge_description 
FROM ACHAT
-- Crer une colonne CASE...

SELECT id, nom, quantité
    CASE quantité
        WHEN 1  THEN 'Offre de -5%'
        WHEN 2  THEN 'Offre de -8%'
        ELSE '-10% pour le prochain article'
    END AS promotions
FROM ACHAT
```

## Date 

```SQL
-- DECIMAL(X, nbr_virgule)
-- DATE AAA-MM-JJ 
-- TIME HH:MM:SS
-- DATETIME AAAA-MM-JJ HH:MM:SS
-- YEAR AAAA

ts: 2020-09-23 
CAST(ts) AS DATETIME -- OR DATE
YEAR(ts) : 2020 -- OR EXTRACT(YEAR FROM ts)
MONTH(ts): 9 -- OR EXTRACT(MONTH FROM ts)
DAY(ts)  : 23 -- OR EXTRACT(DAY FROM ts)
```

Some = Any (plus grand/petit qu'au moins un)
All (plus grand/petit de tout les produits)

# Subtring(string, debut [1..N], extacted_number_charc)