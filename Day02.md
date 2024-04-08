## Exercise 00

```sql
SELECT name, rating FROM (
	SELECT * FROM pizzeria
	LEFT JOIN person_visits ON pizzeria.id = person_visits.pizzeria_id WHERE person_visits.pizzeria_id IS NULL)
as tab;	
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/1353d88b-a66d-477a-b165-b90b59cdded7)


## Exercise 01

```sql
SELECT missing_date::date
	FROM (SELECT pv.visit_date 
		  FROM person_visits pv
		  WHERE pv.person_id = '1' or pv.person_id = '2') tab
RIGHT JOIN generate_series('2022-01-01', '2022-01-10', interval '1 day') as missing_date 
						  ON tab.visit_date = missing_date
WHERE tab.visit_date IS NULL;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/46847790-a2c9-4e53-8de8-bd94a896f7b8)


## Exercise 02

```sql

```

## Exercise 03

```sql
WITH tab AS 
	(SELECT pv.visit_date 
	 FROM person_visits pv
	 WHERE pv.person_id = '1' or pv.person_id = '2')
SELECT missing_date::date
FROM generate_series('2022-01-01', '2022-01-10', interval '1 day') as missing_date 
LEFT JOIN tab ON tab.visit_date = missing_date
WHERE tab.visit_date IS NULL;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/7b1ff397-39e1-4398-9793-26a1f1ec80f5)


## Exercise 04

```sql
SELECT menu.pizza_name, pz.name as pizzeria_name, menu.price p FROM menu
JOIN pizzeria pz ON menu.pizzeria_id = pz.id
WHERE pizza_name = 'mushroom pizza'
or pizza_name = 'pepperoni pizza'
ORDER BY menu.pizza_name, pizzeria_name;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/90812b88-25e5-4eb1-ae63-2fa2e15e26b1)


## Exercise 05

```sql
SELECT name FROM person
WHERE gender='female' AND age > 25
ORDER BY name ASC;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/3a0b4c2b-65c2-43bc-ac41-6a91ac660862)

## Exercise 06

```sql
SELECT m.pizza_name, pz.name as pizzeria_name FROM person_order po
JOIN person p ON po.person_id = p.id
JOIN menu m ON po.menu_id = m.id
JOIN pizzeria pz ON m.pizzeria_id = pz.id
WHERE p.name = 'Anna' or p.name = 'Denis'
ORDER BY m.pizza_name, pz.name;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/db5597d5-609d-44ed-b707-d3f0797f982a)


## Exercise 07

```sql
SELECT pz.name FROM person_visits pv
JOIN person p ON pv.person_id = p.id
JOIN pizzeria pz ON pv.pizzeria_id = pz.id
WHERE pv.visit_date = '2022-01-08' and p.name = 'Dmitriy';
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/cdf31067-370f-45df-9ac5-07a7caa0e9c3)


## Exercise 08

```sql
SELECT name FROM person p
JOIN person_order po ON p.id = po.person_id
JOIN menu m ON m.id = po.menu_id
WHERE (p.gender='male' AND p.address='Moscow' or p.address='Samara') AND (m.pizza_name = 'mushroom pizza' or m.pizza_name = 'pepperoni pizza')
ORDER BY p.name DESC;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/6f8624fb-87de-4463-a9a6-6f2a054556ba)


## Exercise 09

```sql
SELECT name FROM person p
JOIN person_order po ON p.id = po.person_id
JOIN menu m ON m.id = po.menu_id
WHERE (p.gender='female') AND (m.pizza_name = 'cheese pizza' or m.pizza_name = 'pepperoni pizza')
ORDER BY p.name;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/3ed8fc04-88d9-4793-87f1-8646ebc4f6e9)


## Exercise 10

```sql
SELECT p1.name AS person_name1, p2.name AS person_name2, p1.address AS common_address
FROM person AS p1
JOIN person AS p2 ON p1.address = p2.address AND p1.name != p2.name
ORDER BY person_name1, person_name2, common_address;
```

![image](https://github.com/rusinadaria/annalyze/assets/112808317/52650b05-ff06-4c8d-b505-a6e3c37a0c9d)

