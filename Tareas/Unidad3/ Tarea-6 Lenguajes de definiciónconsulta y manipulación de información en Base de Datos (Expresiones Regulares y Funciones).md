# Code, Learn & Practice(Base de datos (Trabajo con expresiones regulares y funciones matemáticas")
## Descripción
En la siguiente tarea se premia el uso de expresiones regulares en BBDD.

Realiza la lectura de la base de datos a través del fichero base datos de clientes.


Realiza el listado de consultas que se encuentran en el fichero consultas-bd.

 <details>
 <summary>Consultas</summary>
  
    
 ```sql 

-- Obtener todos los clientes.

 SELECT * FROM Clientes;

-- Obtener la cantidad total de productos en todos los pedidos

 SELECT SUM(cantidad) AS total_productos FROM Pedidos;

-- Obtener el precio promedio de los productos:

 SELECT AVG(precio) AS precio_promedio FROM Productos;

-- Obtener los clientes que tienen un email válido (contiene '@'):

 SELECT * FROM Clientes WHERE email LIKE '%@%';

-- Obtener el producto más caro.

 SELECT * FROM Productos ORDER BY precio DESC LIMIT 1;

-- Obtener los pedidos realizados en febrero de 2024.

 SELECT * FROM Pedidos WHERE fecha_pedido BETWEEN '2024-02-01' AND '2024-02-29';

-- Obtener la cantidad total de productos en todos los pedidos por producto.

 SELECT id_producto, SUM(cantidad) AS total_por_producto FROM Pedidos GROUP BY id_producto;

-- Obtener los clientes que han realizado más de un pedido.

 SELECT id_cliente, COUNT(id_pedido) AS total_pedidos FROM Pedidos GROUP BY id_cliente; 

-- Obtener los productos que tienen un precio registrado.

 SELECT * FROM Productos WHERE precio IS NOT NULL;

-- Obtener la fecha del primer pedido realizado:

 SELECT MIN(fecha_pedido) AS primer_pedido FROM Pedidos;

-- Obtener los productos cuyos nombres comienzan con 'A' o 'B':

 SELECT * FROM Productos WHERE nombre LIKE 'A%' OR nombre LIKE 'B%';

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.

SELECT id_cliente, SUM(cantidad) AS total_por_cliente FROM Pedidos GROUP BY id_cliente ORDER BY id_cliente;

-- Obtener los clientes que han realizado más de un pedido en febrero de 2024.

 SELECT c.id, c.nombre, c.email, COUNT(p.id_pedido) AS total_pedidos
		FROM Clientes c
		JOIN Pedidos p ON c.id = p.id_cliente
		WHERE p.fecha_pedido BETWEEN '2024-02-01' AND '2024-02-29'
		GROUP BY c.id
		HAVING COUNT(p.id_pedido) > 1;

-- Obtener los productos con precio entre 100 y 500.

 SELECT * FROM Productos WHERE precio BETWEEN 100 AND 500;

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cantidad descendente.

 SELECT id_cliente, SUM(cantidad) AS total_por_cliente FROM Pedidos GROUP BY id_cliente ORDER BY total_por_cliente DESC;

-- Obtener los clientes que tienen una 'a' en cualquier posición de su nombre.

 SELECT * FROM Clientes WHERE nombre LIKE '%a%';

-- Obtener el precio máximo de los productos.

 SELECT MAX(precio) AS precio_maximo FROM Productos

-- Obtener los pedidos realizados por el cliente con ID 1 en febrero de 2024.

 SELECT * FROM Pedidos WHERE id_cliente = 1 AND fecha_pedido BETWEEN '2024-02-01' AND '2024-02-29';

-- Obtener la cantidad total de productos en todos los pedidos por producto ordenado por total de productos descendente.

 SELECT id_producto, SUM(cantidad) AS total_por_producto FROM Pedidos GROUP BY id_producto ORDER BY total_por_producto DESC;

-- Obtener los productos que no tienen un precio registrado.

 SELECT * FROM Productos WHERE precio IS NULL;

-- Obtener la fecha del último pedido realizado.

 SELECT MAX(fecha_pedido) AS ultimo_pedido FROM Pedidos;

-- Obtener los clientes cuyo nombre tiene al menos 5 caracteres.

 SELECT * FROM Clientes WHERE LENGTH(nombre) >= 5;

-- Obtener los productos que tienen la letra 'o' en cualquier posición del nombre.

 SELECT * FROM Productos WHERE nombre LIKE '%o%';

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.

 SELECT id_cliente, SUM(cantidad) AS total_por_cliente FROM Pedidos GROUP BY id_cliente ORDER BY id_cliente;

-- Obtener los clientes cuyos nombres no contienen la letra 'i':

 SELECT * FROM Clientes WHERE nombre NOT LIKE '%i%' AND nombre NOT LIKE '%I%';

-- Obtener los pedidos realizados por el cliente con ID 2 en febrero de 2024.

 SELECT * FROM Pedidos WHERE id_cliente = 2 AND fecha_pedido BETWEEN '2024-02-01' AND '2024-02-29';

-- Obtener el precio mínimo de los productos.

 SELECT MIN(precio) AS precio_minimo FROM Productos;

-- Obtener los clientes que han realizado al menos un pedido en febrero de 2024.

 SELECT DISTINCT id_cliente FROM Pedidos WHERE fecha_pedido BETWEEN '2024-02-01' AND '2024-02-29';

-- Obtener la fecha del último pedido realizado por el cliente con ID 3.

 SELECT MAX(fecha_pedido) AS ultimo_pedido FROM Pedidos WHERE id_cliente = 3;

-- Obtener los productos que tienen una 'a' al final del nombre.

 SELECT * FROM Productos WHERE nombre LIKE '%a';

-- Obtener los clientes cuyos nombres tienen al menos 4 vocales (mayúsculas|minúsculas).

 SELECT * FROM Clientes WHERE LENGTH(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(nombre, 'a', ''), 'e', ''), 'i', ''), 'o', ''), 'u', '')) <= LENGTH(nombre) - 4;

-- Obtener los productos cuyo precio tenga al menos 4 números sin contrar los decimales.

 SELECT * FROM Productos WHERE precio >= 1000;

-- Obtener los clientes cuyos nombres tienen al menos una 'a' seguida de una 'e'.

 SELECT * FROM Clientes WHERE nombre LIKE '%ea%';

-- Obtener los productos cuyos nombres terminan con una consonante.

 SELECT * FROM Productos WHERE nombre REGEXP '[^aeiou]$';

-- Obtener los productos cuyos nombres empiezan con una vocal.

 SELECT * FROM Productos WHERE nombre LIKE 'A%' OR nombre LIKE 'E%' OR nombre LIKE 'I%' OR nombre LIKE 'O%' OR nombre LIKE 'U%';

``` 


     
  </details>
