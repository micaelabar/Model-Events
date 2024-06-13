## 1. Obtener todos los miembros que asistieron a alguna conferencia:
 - Sentencia:
```
SELECT m.fullname, m.email, r.code, r.assisted
FROM member m
JOIN register r ON m.id = r.member_id
WHERE r.assisted = TRUE;
````
-Captura.
<imag!![Imagen de WhatsApp 2024-06-12 a las 22 04 01_a333e4bb](https://github.com/micaelabar/Model-Events/assets/148156209/a4a61b89-26d8-403a-a274-93fa2521c794)

## 2. Contar el número total de asistentes por ciudad de eventos:
 - Sentencia:
```
SELECT e.city, SUM(e.total_attendees) AS total_attendees
FROM event e
GROUP BY e.city
ORDER BY total_attendees DESC;
````
-Captura.
<imag!![Imagen de WhatsApp 2024-06-12 a las 22 04 25_095ec817](https://github.com/micaelabar/Model-Events/assets/148156209/97c09ac6-bea1-4c70-ac22-36183d1d5b8d)

## 3. Obtener los detalles de las conferencias junto con el nombre del evento al que pertenecen:
 - Sentencia:
```
SELECT c.title, c.speaker, c.hour, c.day, e.description AS event_name
FROM conference c
JOIN event e ON c.event_id = e.id;
````
-Captura.
<imag!![Imagen de WhatsApp 2024-06-12 a las 22 05 24_0aad3207](https://github.com/micaelabar/Model-Events/assets/148156209/c1f077f5-46d8-42bc-8bce-ef86b1d164bd)


## 4. Listar todos los miembros que se registraron en más de una conferencia:
 - Sentencia:
```
SELECT m.fullname, COUNT(r.conference_id) AS conference_count
FROM member m
JOIN register r ON m.id = r.member_id
GROUP BY m.id
HAVING conference_count > 1;
````
-Captura.
<imag!![Imagen de WhatsApp 2024-06-12 a las 22 07 30_98741061](https://github.com/micaelabar/Model-Events/assets/148156209/85b68a61-d2ef-437d-b681-084410780ff3)

## 5. Obtener el promedio de edad de los miembros que asistieron a conferencias:
 - Sentencia:
```
SELECT AVG(m.age) AS average_age
FROM member m
JOIN register r ON m.id = r.member_id
WHERE r.assisted = TRUE;
````
-Captura.
<imag!![Imagen de WhatsApp 2024-06-12 a las 22 06 24_e31c34e7](https://github.com/micaelabar/Model-Events/assets/148156209/7dc204bd-c753-455d-a760-01d63aec0fe9)
