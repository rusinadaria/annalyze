## Ex 00
```sql
SELECT menu.pizza_name, menu.price, pz.name as pizzeria_name, visit_date FROM person_visits pv
JOIN person p ON pv.person_id = p.id
JOIN menu ON pv.pizzeria_id = menu.pizzeria_id
JOIN pizzeria pz ON pv.pizzeria_id = pz.id
WHERE p.name = 'Kate'AND menu.price BETWEEN 800 and 1000
ORDER BY pizza_name, price, pizzeria_name;
```
![image](https://github.com/rusinadaria/sql/assets/112808317/6bce1692-b0da-46c9-9ab3-496e31327a1e)

## Ex 01
```sql
SELECT id FROM menu
EXCEPT
SELECT menu_id FROM person_order
ORDER BY id;
```
![image](https://github.com/rusinadaria/sql/assets/112808317/ce67da66-4d76-43ef-8ca5-4e9bc38ba66c)

## Ex 02
```sql
SELECT pizza_name, price, pz.name as pizzeria_name FROM menu m
JOIN pizzeria pz ON pz.id = m.pizzeria_id
LEFT JOIN person_order po ON po.menu_id = m.id
WHERE po.menu_id IS NULL
ORDER BY pizza_name, price;
```
![image](https://github.com/rusinadaria/sql/assets/112808317/622e0168-e31c-4d0e-9455-9f6fcbb7081b)

## Ex 03
```sql
SELECT pz.name as pizzeria_name FROM pizzeria pz
JOIN person_visits pv ON pv.pizzeria_id  = pz.id
JOIN person p ON p.id = pv.person_id
WHERE p.gender = 'female'
UNION ALL
SELECT pz.name as pizzeria_name FROM pizzeria pz
JOIN person_visits pv ON pv.pizzeria_id  = pz.id
JOIN person p ON p.id = pv.person_id
WHERE p.gender = 'male'
ORDER BY pizzeria_name;
```
![image](https://github.com/rusinadaria/sql/assets/112808317/d359a0c5-fb2f-45b6-a3e3-52fabe8eead0)

## Ex 04
```sql
SELECT pz.name as pizzeria_name FROM pizzeria pz
JOIN menu m ON m.pizzeria_id = pz.id
JOIN person_order po ON po.menu_id = m.id
JOIN person p ON p.id = po.person_id
WHERE p.gender = 'female'
EXCEPT
SELECT pz.name as pizzeria_name FROM pizzeria pz
JOIN menu m ON m.pizzeria_id = pz.id
JOIN person_order po ON po.menu_id = m.id
JOIN person p ON p.id = po.person_id
WHERE p.gender = 'male'
ORDER BY pizzeria_name;
```
![image](https://github.com/rusinadaria/sql/assets/112808317/3bf9615e-c85d-40c3-905e-a1905544dab1)

## Ex 05
```sql

```
