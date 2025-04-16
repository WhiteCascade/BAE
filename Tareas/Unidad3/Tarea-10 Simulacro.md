# Code, Learn & Practice(Base de datos (Trabajo con expresiones regulares y funciones matemáticas")
## Descripción
**Simulacro de examen se provee de los siguientes ficheros:**

## consultas_multitabla.sql.


 <details>
 <summary>Consultas</summary>

 ``` sql
-- Consultas sobre una tabla
-- 0,2 puntos la correcta. Total = 1,4 puntos
-- ----------------------------------------

-- 1.- Devuelve un listado con todos las compras que se han realizado. Las compras deben estar ordenados
-- por la fecha de realización, mostrando en primer lugar las compras más recientes.

 SELECT * 
 FROM compra
 ORDER BY fecha DESC;

-- 2. Devuelve todos los datos de los dos compras de mayor valor.

 SELECT * 
 FROM compra
 ORDER BY total DESC
 LIMIT 2;

-- 3. Devuelve un listado con los identificadores de los consumidores que han realizado algún compra.
-- Tenga en cuenta que no debe mostrar identificadores que estén repetidos.

 SELECT DISTINCT id_consumidor 
 FROM compra;

-- 4. Devuelve un listado de todos las compras que se realizaron durante el año 2020,
-- cuya cantidad total sea superior a 500€.

 SELECT * 
 FROM compra
 WHERE fecha LIKE '2020%' AND total > 500;

-- 5. Devuelve un listado con el nombre y los apellidos de los suministradores que tienen una comisión entre 0.11 y 0.15.

 SELECT nombre, apellido1, apellido2
 FROM suministrador
 WHERE categoria BETWEEN 0.11 AND 0.15;

-- 6. Devuelve el valor de la comisión de mayor valor que existe en la tabla suministrador.

 SELECT MAX(categoria) AS max_comision
 FROM suministrador;

-- 7. Devuelve el identificador, nombre y primer apellido de aquellos consumidores cuyo segundo apellido no es NULL.
-- El listado deberá estar ordenado alfabéticamente por apellidos y nombre.

 SELECT id, nombre, apellido1
 FROM consumidor
 WHERE apellido2 IS NOT NULL
 ORDER BY apellido1, apellido2, nombre;

-- (Consultas Multitabla Where)
-- -----------------------------------------------
-- 0,3 puntos la correcta. Total =  2,1 puntos
-- -----------------------------------------------

-- 1. Devuelve un listado con el identificador, nombre y los apellidos de todos los consumidores que han realizado algún compra.
-- El listado debe estar ordenado alfabéticamente y se deben eliminar los elementos repetidos.

 SELECT DISTINCT c.id_consumidor, c.nombre, c.apellido1, c.apellido2
 FROM consumidor c, compra co
 WHERE c.id_consumidor = co.id_consumidor
 ORDER BY c.apellido1, c.apellido2, c.nombre;

-- 2. Devuelve un listado que muestre todos las compras que ha realizado cada consumidor. 
-- El resultado debe mostrar todos los datos de las compras y del consumidor. El listado debe mostrar los datos de los consumidores ordenados alfabéticamente.

 SELECT *
 FROM consumidor c, compra co
 WHERE c.id_consumidor = co.id_consumidor
 ORDER BY c.apellido1, c.apellido2, c.nombre;

-- 3. Devuelve un listado que muestre todos las compras en los que ha participado un suministrador.
-- El resultado debe mostrar todos los datos de las compras y de los suministradores.
-- El listado debe mostrar los datos de los suministradores ordenados alfabéticamente.

 SELECT *
 FROM compra co, suministrador s
 WHERE co.id_suministrador = s.id_suministrador
 ORDER BY s.apellido1, s.apellido2, s.nombre;

-- 4. Devuelve un listado que muestre todos los consumidores, con todos las compras que han realizado 
-- y con los datos de los suministradores asociados a cada compra.

 SELECT *
 FROM consumidor c, compra co, suministrador s
 WHERE c.id_consumidor = co.id_consumidor
 AND co.id_suministrador = s.id_suministrador;

-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.

 SELECT DISTINCT c.*
 FROM consumidor c, compra co
 WHERE c.id_consumidor = co.id_consumidor
 AND YEAR(co.fecha) = 2020
 AND co.cantidad BETWEEN 300 AND 1000;

-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.

 SELECT DISTINCT s.nombre, s.apellido1, s.apellido2
 FROM suministrador s, compra co, consumidor c
 WHERE s.id_suministrador = co.id_suministrador
 AND co.id_consumidor = c.id_consumidor
 AND c.nombre = 'María'
 AND c.apellido1 = 'Santana'
 AND c.apellido2 = 'Moreno';

-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.

 SELECT DISTINCT c.nombre
 FROM consumidor c, compra co, suministrador s
 WHERE c.id_consumidor = co.id_consumidor
 AND co.id_suministrador = s.id_suministrador
 AND s.nombre = 'Daniel'
 AND s.apellido1 = 'Sáez'
 AND s.apellido2 = 'Vega';

-- (Consultas Multitabla Join)
-- -----------------------------------------------
-- 0,3 puntos la correcta. Total = 2,1 puntos
-- -----------------------------------------------

-- 1. Devuelve un listado con el identificador, nombre y los apellidos de todos los consumidores que han realizado algún compra.
-- El listado debe estar ordenado alfabéticamente y se deben eliminar los elementos repetidos.

 SELECT DISTINCT c.id_consumidor, c.nombre, c.apellido1, c.apellido2
 FROM consumidor c
 JOIN compra co ON c.id_consumidor = co.id_consumidor
 ORDER BY c.apellido1, c.apellido2, c.nombre;

-- 2. Devuelve un listado que muestre todos las compras que ha realizado cada consumidor. 
-- El resultado debe mostrar todos los datos de las compras y del consumidor. El listado debe mostrar los datos de los consumidores ordenados alfabéticamente.

 SELECT *
 FROM consumidor c
 JOIN compra co ON c.id_consumidor = co.id_consumidor
 ORDER BY c.apellido1, c.apellido2, c.nombre;

-- 3. Devuelve un listado que muestre todos las compras en los que ha participado un suministrador.
-- El resultado debe mostrar todos los datos de las compras y de los suministradores.
-- El listado debe mostrar los datos de los suministradores ordenados alfabéticamente.

 SELECT *
 FROM compra co
 JOIN suministrador s ON co.id_suministrador = s.id_suministrador
 ORDER BY s.apellido1, s.apellido2, s.nombre;

-- 4. Devuelve un listado que muestre todos los consumidores, con todos las compras que han realizado 
-- y con los datos de los suministradores asociados a cada compra.

 SELECT *
 FROM consumidor c
 JOIN compra co ON c.id_consumidor = co.id_consumidor
 JOIN suministrador s ON co.id_suministrador = s.id_suministrador;


-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.

 SELECT DISTINCT c.*
 FROM consumidor c
 JOIN compra co ON c.id_consumidor = co.id_consumidor
 WHERE YEAR(co.fecha) = 2020 AND co.cantidad BETWEEN 300 AND 1000;

-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.

 SELECT DISTINCT s.nombre, s.apellido1, s.apellido2
 FROM suministrador s
 JOIN compra co ON s.id_suministrador = co.id_suministrador
 JOIN consumidor c ON co.id_consumidor = c.id_consumidor
 WHERE c.nombre = 'María' AND c.apellido1 = 'Santana' AND c.apellido2 = 'Moreno';

-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.

 SELECT DISTINCT c.nombre
 FROM consumidor c
 JOIN compra co ON c.id_consumidor = co.id_consumidor
 JOIN suministrador s ON co.id_suministrador = s.id_suministrador
 WHERE s.nombre = 'Daniel' AND s.apellido1 = 'Sáez' AND s.apellido2 = 'Vega';

-- ---------------------------
-- Consultas resumen (funciones)
-- -----------------------------------------------
-- 0,2 puntos la correcta. (1-6) 1,2 puntos
-- 0,25 puntos la correcta. (7-10) 1 punto.
-- Total = 2,2 puntos
-- -----------------------------------------------

-- 1. Calcula la cantidad media de todos las compras que aparecen en la tabla compra.

 SELECT AVG(cantidad) AS cantidad_media
 FROM compra;


-- 2. Calcula el número total de suministradores distintos que aparecen en la tabla compra.

 SELECT COUNT(DISTINCT id_suministrador) AS total_suministradores
 FROM compra;


-- 3. Calcula el número total de consumidores que aparecen en la tabla consumidor.

 SELECT COUNT(*) AS total_consumidores
 FROM consumidor;


-- 4. Calcula cuál es la mayor cantidad que aparece en la tabla compra.

 SELECT MAX(cantidad) AS max_cantidad
 FROM compra;


-- 5. Calcula cuál es el valor máximo de categoría para cada una de las ciudades que aparece en la tabla consumidor.

 SELECT ciudad, MAX(categoria) AS max_categoria
 FROM consumidor
 GROUP BY ciudad;


-- 6. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores.
-- Es decir, el mismo consumidor puede haber realizado varios compras de diferentes cantidades el mismo día.
-- Se pide que se calcule cuál es el compra de máximo valor para cada uno de los días en los que un consumidor ha realizado un compra.
-- Muestra el identificador del consumidor, nombre, apellidos, la fecha y el valor de la cantidad.

 SELECT c.id_consumidor, c.nombre, c.apellido1, c.apellido2, co.fecha, MAX(co.cantidad) AS max_cantidad
 FROM compra co
 JOIN consumidor c ON co.id_consumidor = c.id_consumidor
 GROUP BY c.id_consumidor, c.nombre, c.apellido1, c.apellido2, co.fecha;


-- 7. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores,
-- teniendo en cuenta que sólo queremos mostrar aquellas compras que superen la cantidad de 2000 €.

 SELECT c.id_consumidor, c.nombre, c.apellido1, c.apellido2, co.fecha, MAX(co.cantidad) AS max_cantidad
 FROM compra co
 JOIN consumidor c ON co.id_consumidor = c.id_consumidor
 GROUP BY c.id_consumidor, c.nombre, c.apellido1, c.apellido2, co.fecha
 HAVING MAX(co.cantidad) > 2000;


-- 8. Calcula el máximo valor de las compras realizadas para cada uno de los suministradores durante la fecha 2020-08-17.
-- Muestra el identificador del suministrador, nombre, apellidos y total.

 SELECT s.id_suministrador, s.nombre, s.apellido1, s.apellido2, MAX(co.cantidad) AS max_cantidad
 FROM compra co
 JOIN suministrador s ON co.id_suministrador = s.id_suministrador
 WHERE co.fecha = '2020-08-17'
 GROUP BY s.id_suministrador, s.nombre, s.apellido1, s.apellido2;


-- 9. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores.
-- Tenga en cuenta que pueden existir consumidores que no han realizado ninguna compra.
-- Estos consumidores también deben aparecer en el listado indicando que el número de compras realizadas es 0.

 SELECT c.id_consumidor, c.nombre, c.apellido1, c.apellido2, COUNT(co.id_compra) AS total_compras
 FROM consumidor c
 LEFT JOIN compra co ON c.id_consumidor = co.id_consumidor
 GROUP BY c.id_consumidor, c.nombre, c.apellido1, c.apellido2;


-- 10. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores durante el año 2020.

 SELECT c.id_consumidor, c.nombre, c.apellido1, c.apellido2, COUNT(co.id_compra) AS total_compras_2020
 FROM consumidor c
 LEFT JOIN compra co ON c.id_consumidor = co.id_consumidor
 WHERE YEAR(co.fecha) = 2020
 GROUP BY c.id_consumidor, c.nombre, c.apellido1, c.apellido2;


-- ---------------------
-- Subconsultas
-- -----------------------------------------------
-- 0,2 puntos la correcta (1-5).
-- 0,3 puntos la correcta (6-9).
-- Total = 2,2 puntos
-- -----------------------------------------------

--- Con operadores básicos de comparación

-- 1. Devuelve un listado con todos las compras que ha realizado Adela Salas Díaz. (Sin utilizar INNER JOIN).

 SELECT *
 FROM compra
 WHERE id_consumidor = (
 SELECT id_consumidor
 FROM consumidor
 WHERE nombre = 'Adela' AND apellido1 = 'Salas' AND apellido2 = 'Díaz');


-- 2. Devuelve la fecha y la cantidad del compra de menor valor realizado por el cliente Pepe Ruiz Santana.

 SELECT fecha, cantidad
 FROM compra
 WHERE id_consumidor = (
 SELECT id_consumidor
 FROM consumidor
 WHERE nombre = 'Pepe' AND apellido1 = 'Ruiz' AND apellido2 = 'Santana')
 ORDER BY cantidad ASC
 LIMIT 1;


-- 3. Devuelve el número de compras en los que ha participado el suministrador Daniel Sáez Vega. (Sin utilizar INNER JOIN)

 SELECT COUNT(*)
 FROM compra
 WHERE id_suministrador = (
 SELECT id_suministrador
 FROM suministrador
 WHERE nombre = 'Daniel' AND apellido1 = 'Sáez' AND apellido2 = 'Vega');


-- 4. Devuelve los datos del consumidor que realizó el compra más caro en el año 2021. (Sin utilizar INNER JOIN)

-- SELECT *
 FROM consumidor
 WHERE id_consumidor = (
 SELECT id_consumidor
 FROM compra
 WHERE YEAR(fecha) = 2021
 ORDER BY cantidad DESC
 LIMIT 1);


-- 5. Devuelve un listado con los datos de los consumidores y las compras, de todos los consumidores que han realizado un compra durante el año 2020 con un valor mayor o igual al valor medio de las compras realizadas durante ese mismo año.

 SELECT *
 FROM compra
 WHERE YEAR(fecha) = 2020
 AND cantidad >= (
 SELECT AVG(cantidad)
 FROM compra
 WHERE YEAR(fecha) = 2020);


-- 6. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando IN o NOT IN).

 SELECT *
 FROM consumidor
 WHERE id_consumidor NOT IN (
 SELECT DISTINCT id_consumidor
 FROM compra);


-- 7. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando IN o NOT IN).

 SELECT *
 FROM suministrador
 WHERE id_suministrador NOT IN (
 SELECT DISTINCT id_suministrador
 FROM compra);


-- 8. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).

 SELECT *
 FROM consumidor c
 WHERE NOT EXISTS (
 SELECT 1
 FROM compra co
 WHERE co.id_consumidor = c.id_consumidor);


-- 9. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).

 SELECT *
 FROM suministrador s
 WHERE NOT EXISTS (
 SELECT 1
 FROM compra co
 WHERE co.id_suministrador = s.id_suministrador);

 ``` 
