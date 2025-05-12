# Code, Learn & Practice("Optimización de bbdd")
 
Un instituto de enseñanza guarda los siguientes datos de sus alumnos:

- número de inscripción, comienza desde 1 cada año,
- año de inscripción,
- nombre del alumno,
- documento del alumno,
- domicilio,
- ciudad,
- provincia,
- clave primaria: número de inscripto y año de inscripción.
 <details>
 <summary>Consultas</summary>

 ``` sql

- Elimine la tabla "alumno" si existe.

DROP TABLE IF EXISTS alumno;

- Cree la tabla definiendo una clave primaria compuesta (año de inscripción y número de inscripción).

CREATE TABLE alumno (
    numero_inscripcion INT NOT NULL,
    anio_inscripcion INT NOT NULL,
    nombre VARCHAR(100),
    documento VARCHAR(20),
    domicilio VARCHAR(150),
    ciudad VARCHAR(50),
    provincia VARCHAR(50),
    PRIMARY KEY (anio_inscripcion, numero_inscripcion)
);

- Define los siguientes indices:
- Un índice único por el campo "documento" y un índice común por ciudad y provincia.

CREATE UNIQUE INDEX idx_documento ON alumno(documento);
CREATE INDEX idx_ciudad_provincia ON alumno(ciudad, provincia);

 - Vea los índices de la tabla.

SHOW INDEX FROM alumno;

- Intente ingresar un alumno con clave primaria repetida.

INSERT INTO alumno VALUES (1, 2024, 'Carlos García', '87654321', 'Calle 2', 'Rosario', 'Santa Fe');

- Intente ingresar un alumno con documento repetido.

INSERT INTO alumno VALUES (2, 2024, 'Ana Torres', '12345678', 'Calle 3', 'Mendoza', 'Mendoza');

- Ingrese varios alumnos de la misma ciudad y provincia.

INSERT INTO alumno VALUES (2, 2024, 'Luis Martínez', '22334455', 'Calle 4', 'Salta', 'Salta');
INSERT INTO alumno VALUES (3, 2024, 'María Gómez', '33445566', 'Calle 5', 'Salta', 'Salta');

- Elimina los indices creados, y muestra que ya no se encuentran

DROP INDEX idx_documento ON alumno;
DROP INDEX idx_ciudad_provincia ON alumno;

SHOW INDEX FROM alumno;
