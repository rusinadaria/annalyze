##Ex00
```sql
SELECT menu.pizza_name, menu.price, pz.name as pizzeria_name, visit_date FROM person_visits pv
JOIN person p ON pv.person_id = p.id
JOIN menu ON pv.pizzeria_id = menu.pizzeria_id
JOIN pizzeria pz ON pv.pizzeria_id = pz.id
WHERE p.name = 'Kate'AND menu.price BETWEEN 800 and 1000
ORDER BY pizza_name, price, pizzeria_name






