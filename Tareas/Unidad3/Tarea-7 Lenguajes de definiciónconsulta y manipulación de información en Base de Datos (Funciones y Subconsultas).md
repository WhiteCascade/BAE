# Code, Learn & Practice(Base de datos (Trabajo con expresiones regulares y funciones matemáticas")
## Descripción
**En la siguiente tarea se premia el uso de funciones matemáticas, así como la utilización de subconsultas en BBDD.**

## Realiza el listado de consultas que se encuentran en el fichero consultas-bd.


 <details>
 <summary>Consultas</summary>
   
```sql
-- Listar los coches vendidos con sus modelos y precios, junto con los nombres de los clientes que los compraron.
  -- Cosas que debo de tener en cuenta:

  Me piden los coches vendidos con su modelo, precio y el cliente que los compró.

    -- ¿Qué me están pidiendo?. ¿Qué es lo que no me han pedido?

    No me piden coches no vendidos ni más datos del cliente.

    SELECT c.modelo, c.precio, cl.nombre 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente;

-- Encontrar los clientes que han comprado coches con precios superiores al promedio de todos los coches vendidos.
  -- Cosas que debo de tener en cuenta:
    -- Precios superiores.
    -- Obtener la media. AVG(precio)

    SELECT cl.nombre, c.precio 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	WHERE c.precio > (SELECT AVG(precio) FROM coches);

-- Mostrar los modelos de coches y sus precios que no han sido vendidos aún:

  -- Cosas que debo de tener en cuenta:
    -- Coches que han sido vendidos.
    -- Quiero los coches que no han sido vendidos. NOT id_coche IN ventas

    SELECT modelo, precio 
	FROM coches 
	WHERE id_coche NOT IN (SELECT id_coche FROM ventas);

-- Calcular el total gastado por todos los clientes en coches:
  -- Cosas que debo de tener en cuenta:
    -- Me estan pidiendo la suma total de todos los coches vendidos, NO de aquellos que aún no se han vendido.

    SELECT SUM(c.precio) AS total_gastado
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche;

-- Listar los coches vendidos junto con la fecha de venta y el nombre del cliente, ordenados por fecha de venta de forma descendente:
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. 

    Obtener los coches vendidos con su fecha y el cliente que lo compró y ordenar por fecha de venta de forma descendente.

    ¿Por qué campo tengo que ordenadar. Es uno o más campos?

    Solo por la fecha_venta en orden descendente.

    SELECT c.modelo, cl.nombre, v.fecha_venta 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	ORDER BY v.fecha_venta DESC;

-- Encontrar el modelo de coche más caro.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. MAX

    Contar cuántos coches han comprado.
    SELECT modelo, precio
	FROM coches
	WHERE precio = (SELECT MAX(precio) FROM coches) LIMIT 1;

-- Mostrar los clientes que han comprado al menos un coche (un coche o más) y la cantidad de coches comprados.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. COUNT

    Obtener los clientes que han realizado compras de coches y contar cuantos compraron dichos clientes.

    SELECT cl.nombre, COUNT(v.id_coche) AS cantidad_coches
	FROM ventas v
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	GROUP BY cl.id_cliente;

-- Encontrar los clientes que han comprado coches de la marca 'Toyota':
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. Like | regexp | =. Tabla normalizada ?.

    Solo los clientes que han comprado un coche de la marca "Toyota".

    SELECT DISTINCT cl.nombre 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	WHERE c.marca = 'Toyota';

-- Calcular el promedio de edad de los clientes que han comprado coches de más de 25,000.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. 

    Calcular la edad promedio de los clientes que compraron coches con precio mayor a 25,000.

    SELECT AVG(cl.edad) AS edad_promedio
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	WHERE c.precio > 25000;

-- Mostrar los modelos de coches y sus precios que fueron comprados por clientes mayores de 30 años.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?.

    Listar los coches que han sido comprados por clientes cuya edad es mayor de 30 años.

    SELECT c.modelo, c.precio 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	JOIN clientes cl ON v.id_cliente = cl.id_cliente
	WHERE cl.edad > 30;

-- Encontrar los coches vendidos en el año 2022 junto con la cantidad total de ventas en ese año.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?.

    La cantidad de coches vendidos en 2022.

    SELECT c.modelo, COUNT(v.id_venta) AS total_ventas
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	WHERE YEAR(v.fecha_venta) = 2022
	GROUP BY c.modelo;

-- Listar los coches cuyos precios son mayores que el precio promedio de coches vendidos a clientes menores de 30 años.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. AVG

    Que Obtenga los coches con precios superiores al promedio de los coches comprados por clientes menores de 30 años.

    SELECT modelo, precio 
	FROM coches 
	WHERE precio > (
    SELECT AVG(c.precio)
    FROM ventas v
    JOIN coches c ON v.id_coche = c.id_coche
    JOIN clientes cl ON v.id_cliente = cl.id_cliente
    WHERE cl.edad < 30
);

-- Calcular el total de ventas por marca de coche, ordenado de forma descendente por el total de ventas:
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. COUNT| DESC|ASC precio

    Que ordene de mayor a menor la cantidad de ventas de las marcas de coches.

    SELECT c.marca, COUNT(v.id_venta) AS total_ventas 
	FROM ventas v
	JOIN coches c ON v.id_coche = c.id_coche
	GROUP BY c.marca
	ORDER BY total_ventas DESC;

``` 
  </details>
