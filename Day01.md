## Task - 1

```sql
SELECT id AS object_id, name AS object_name FROM person
UNION ALL
SELECT id AS object_id, pizza_name AS object_name FROM menu
ORDER BY object_id, object_name;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/79ec73b9-13c2-4635-9996-898c7f8b5c78)

## Task - 2

```sql
SELECT name AS object_name FROM person
UNION ALL
SELECT pizza_name AS object_name FROM menu
ORDER BY object_name;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/c29e1b75-486b-4e9f-8255-60ef80ba4a45)

## Task - 3

```sql
SELECT order_date AS action_date, person_id FROM person_order
UNION ALL
SELECT visit_date AS action_date, person_id FROM person_visits
ORDER BY action_date ASC, person_id DESC;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/b99b54f8-cbaa-4c0a-8dd1-60199449ba2b)

## Task - 4

```sql
SELECT person_id FROM person_order
WHERE order_date = '2022-01-07'
EXCEPT
SELECT person_id FROM person_visits
WHERE visit_date = '2022-01-07'
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/77795f4b-ab03-4459-a999-5b71c4939896)

## Task - 5

```sql
SELECT
	person.id AS "person.id",
	person.name AS "person.name",
	person.age,
	person.gender,
	person.address,
	pizzeria.id AS "pizzeria.id",
	pizzeria.name AS "pizzeria.name",
	pizzeria.rating
FROM person
CROSS JOIN pizzeria
ORDER BY "person.id";
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/fa797286-d5c4-4666-acae-7e7ddfc5fbbb)

## Task - 6

```sql
SELECT action_date, person.name FROM (
	SELECT order_date as action_date, person_id FROM person_order
	INTERSECT
	SELECT visit_date, person_id FROM person_visits
) as tab
JOIN person ON tab.person_id = person.id;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/70b4538e-23d5-4d98-8b13-e8565616c754)

## Task - 7

```sql
SELECT 
	person_order.order_date,
	person.name || ' (age:' || person.age || ')' AS person_information
	FROM person_order
JOIN person ON person.id = person_order.person_id;
```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/7d52edd0-268f-4e7b-aae4-8c729ff905d2)

## Task - 8

```sql

SELECT 
	person_order.order_date,
	person.name || ' (age:' || person.age || ')' AS person_information
	FROM person_order
NATURAL JOIN person;

```
![image](https://github.com/rusinadaria/annalyze/assets/112808317/a8c1b0d7-eb56-4dc5-8e12-efe8d4142ff8)

## Task - 9

```sql



```

