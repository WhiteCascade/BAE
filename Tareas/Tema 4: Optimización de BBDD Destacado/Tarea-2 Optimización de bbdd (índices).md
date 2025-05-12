# Code, Learn & Practice("Optimización de bbdd")

Una empresa guarda los siguientes datos de sus clientes, con los siguientes campos:

- documento char (8) not null,
- nombre varchar(30) not null,
- domicilio varchar(30),
- ciudad varchar(20),
- provincia varchar (20),
- telefono varchar(11)
<details>
 <summary>Se pide:</summary>
  
  ``` sql
 - Eliminar la tabla "cliente" si existe
DROP TABLE IF EXISTS cliente;

- Crear la tabla sin clave primaria
CREATE TABLE cliente (
  documento CHAR(8)   NOT NULL,
  nombre    VARCHAR(30) NOT NULL,
  domicilio VARCHAR(30),
  ciudad    VARCHAR(20),
  provincia VARCHAR(20),
  telefono  VARCHAR(11)
) ENGINE=InnoDB;

- Añadir la clave primaria después
ALTER TABLE cliente
  ADD PRIMARY KEY (documento);

- UNIQUE INDEX en documento
CREATE UNIQUE INDEX idx_documento ON cliente(documento);

- INDEX en ciudad y provincia
CREATE INDEX idx_ciudad_provincia ON cliente(ciudad, provincia);

- Justificación:
- UNIQUE INDEX evita que dos clientes tengan el mismo documento.
- INDEX acelera las búsquedas por ciudad y provincia sin impedir duplicados.

- Ver los índices de la tabla
SHOW INDEX FROM cliente;

- Agregar UNIQUE INDEX en telefono
CREATE UNIQUE INDEX idx_telefono ON cliente(telefono);


- Eliminar los índices

DROP INDEX idx_documento ON cliente;
DROP INDEX idx_ciudad_provincia ON cliente;
DROP INDEX idx_telefono ON cliente;

- Verificar que solo queda la clave primaria

SHOW INDEX FROM cliente;

