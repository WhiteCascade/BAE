# Code, Learn & Practice("Simulacro consultas bbdd")
## Descripción
**Simulacro de examen**
 <details>
 <summary>Consultas</summary>

 ``` sql
-- 1. Consultas Básicas (8 consultas - 1.6 puntos)
-- Listar todos los libros disponibles

SELECT * FROM libro WHERE disponible = 1;

-- Mostrar socios de Madrid ordenados por apellido

SELECT * FROM socio WHERE ciudad = "Madrid" ORDER BY apellido1;

-- Libros publicados después de 1950

SELECT * FROM libro WHERE año_publicacion > 1950;

-- Bibliotecarios con más de 3 años de antigüedad

SELECT * FROM bibliotecario WHERE antiguedad > 3;

-- Préstamos realizados en 2023

SELECT * FROM prestamo  WHERE año_publicacion > 2023;

-- Socios sin segundo apellido

SELECT * FROM socio WHERE apellido2 IS NUll;

-- Libros del género "Realismo mágico"

SELECT * FROM libro WHERE genero = 'Realismo mágico';

-- Préstamos no devueltos (fecha_devolucion IS NULL)

SELECT * FROM prestamo  WHERE fecha_devolucion IS NULL;

-- 2. Consultas Multitabla (WHERE) (8 consultas - 2.4 puntos)
-- Préstamos con nombres de socio y libro (sin JOIN)

SELECT s.nombre, l.titulo from libro l, prestamo p, socio s where l.id = p.id_libro and s.id = p.id_socio;

-- Libros prestados a socios de Barcelona (sin JOIN)

SELECT l.* FROM libro l, socio s, prestamo p WHERE p.id_socio = s.id AND p.id_libro = l.id AND s.ciudad = 'Barcelona';

-- Socios que han tomado prestado "Cien años de soledad" (sin JOIN)

SELECT DISTINCT s.* FROM socio s, prestamo p, libro l WHERE p.id_socio = s.id AND p.id_libro = l.id AND l.titulo = 'Cien años de soledad';

-- Bibliotecarios que han gestionado préstamos (sin JOIN)



-- Préstamos con retraso (fecha_devolucion > fecha_prestamo + 14 días)

SELECT * FROM prestamo WHERE fecha_devolucion IS NOT NULL AND julianday(fecha_devolucion) - julianday(fecha_prestamo) > 14;

-- Socios que nunca han tomado prestado un libro (sin LEFT JOIN)

SELECT * FROM socio WHERE id NOT IN (SELECT id_socio FROM prestamo);

-- Libros más prestados (sin JOIN)

SELECT id_libro, COUNT(*) AS veces_prestado FROM prestamo GROUP BY id_libro ORDER BY veces_prestado DESC;

-- Autores cuyos libros han sido prestados (sin JOIN)

SELECT DISTINCT l.autor FROM libro l, prestamo p WHERE l.id = p.id_libro;

-- 3. Consultas Multitabla (JOIN) (8 consultas - 2.4 puntos)
-- Préstamos con nombres de socio y libro (JOIN)

SELECT p.id, s.nombre AS nombre_socio, l.titulo AS titulo_libro FROM prestamo p JOIN socio s ON p.id_socio = s.id JOIN libro l ON p.id_libro = l.id;

-- Libros prestados a socios de Barcelona (JOIN)

SELECT l.* FROM prestamo p JOIN socio s ON p.id_socio = s.id JOIN libro l ON p.id_libro = l.id WHERE s.ciudad = 'Barcelona';

-- Socios que han tomado prestado "Cien años de soledad" (JOIN)

SELECT DISTINCT s.* FROM prestamo p JOIN socio s ON p.id_socio = s.id JOIN libro l ON p.id_libro = l.id WHERE l.titulo = 'Cien años de soledad';

-- Bibliotecarios que han gestionado préstamos (JOIN)

No se puede realizar: no hay columna en 'prestamo' que relacione con 'bibliotecario'

-- Préstamos con datos completos (socio, libro, bibliotecario)

Incompleto: falta campo que relacione préstamo con bibliotecario

-- Socios con sus préstamos activos (JOIN)

SELECT s.*, p.* FROM socio s JOIN prestamo p ON s.id = p.id_socio WHERE p.fecha_devolucion IS NULL;

-- Libros nunca prestados (LEFT JOIN)

SELECT l.* FROM libro l LEFT JOIN prestamo p ON l.id = p.id_libro WHERE p.id IS NULL;

-- Autores con número de libros prestados (JOIN + GROUP BY)

SELECT l.autor, COUNT(p.id) AS veces_prestado FROM libro l JOIN prestamo p ON l.id = p.id_libro GROUP BY l.autor;

-- 4. Consultas Resumen (8 consultas - 2.4 puntos)
-- Número de socios por ciudad

SELECT ciudad, COUNT(*) AS total_socios FROM socio GROUP BY ciudad;

-- Promedio de antigüedad de bibliotecarios

SELECT AVG(antiguedad) AS promedio_antiguedad FROM bibliotecario;

-- Cantidad de préstamos por mes en 2023

SELECT SUBSTR(fecha_prestamo, 1, 7) AS mes, COUNT(*) AS cantidad_prestamos FROM prestamo WHERE fecha_prestamo LIKE '2023%' GROUP BY mes ORDER BY mes;

-- Libros más populares (por veces prestados)

SELECT l.titulo, COUNT(p.id) AS veces_prestado FROM libro l JOIN prestamo p ON l.id = p.id_libro GROUP BY l.titulo ORDER BY veces_prestado DESC;

-- Socios más activos (por préstamos realizados)

SELECT s.nombre, s.apellido1, COUNT(p.id) AS prestamos_realizados FROM socio s JOIN prestamo p ON s.id = p.id_socio GROUP BY s.id ORDER BY prestamos_realizados DESC;

-- Porcentaje de libros disponibles

SELECT ROUND(100.0 * SUM(CASE WHEN disponible = 1 THEN 1 ELSE 0 END) / COUNT(*), 2) AS porcentaje_disponibles FROM libro;

-- Días promedio de préstamo

-- Número de préstamos por categoría de socio

SELECT AVG(julianday(fecha_devolucion) - julianday(fecha_prestamo)) AS dias_promedio FROM prestamo WHERE fecha_devolucion IS NOT NULL;

-- 5. Subconsultas (8 consultas - 1.2 puntos)

-- Socios que han prestado libros de Gabriel García Márquez

SELECT DISTINCT s.* FROM socio s WHERE s.id IN (SELECT p.id_socio FROM prestamo p JOIN libro l ON p.id_libro = l.id WHERE l.autor = 'Gabriel García Márquez');

-- Libros con préstamos superiores al promedio

SELECT l.* FROM libro l WHERE ( SELECT COUNT(*) FROM prestamo p WHERE p.id_libro = l.id) > (SELECT AVG(cantidad) FROM (SELECT COUNT(*) AS cantidad FROM prestamoGROUP BY id_libro));

-- Socios con todos los préstamos devueltos a tiempo

SELECT s.* FROM socio s WHERE s.id NOT IN (SELECT p.id_socio FROM prestamo p WHERE fecha_devolucion IS NOT NULL AND julianday(fecha_devolucion) - julianday(fecha_prestamo) > 14

-- Bibliotecarios que no han gestionado préstamos

 No se puede realizar porque 'prestamo' no tiene relación con 'bibliotecario'

-- Socios que han prestado más libros que el promedio

SELECT s.* FROM socio s WHERE (SELECT COUNT(*) FROM prestamo p WHERE p.id_socio = s.id) > (SELECT AVG(cantidad) FROM (SELECT COUNT(*) AS cantidad FROM prestamo GROUP BY id_socio));

-- Libros disponibles que nunca han sido prestados

SELECT * FROM libro WHERE disponible = 1 AND id NOT IN (SELECT id_libro FROM prestamo);

-- Socios con préstamos en todas las categorías de libros

SELECT s.* FROM socio s WHERE NOT EXISTS (SELECT DISTINCT genero FROM libro EXCEPT SELECT DISTINCT l.genero FROM prestamo p JOIN libro l ON p.id_libro = l.id WHERE p.id_socio = s.id

-- Bibliotecarios que han gestionado préstamos de todos los socios de Madrid

No se puede realizar sin una relación entre bibliotecario y prestamo
