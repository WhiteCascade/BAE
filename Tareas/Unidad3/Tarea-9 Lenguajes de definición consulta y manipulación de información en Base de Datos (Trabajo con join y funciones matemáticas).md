# Code, Learn & Practice(Base de datos (Trabajo con expresiones regulares y funciones matemáticas")
## Descripción
**En la siguiente tarea se premia el uso de funciones matemáticas, así como la utilización de join en BBDD.**

## Realiza el listado de consultas que se encuentran en el fichero consultas-bd.


 <details>
 <summary>Consultas</summary>
   
 ``` sql
- Obtener el nombre del alumno y el nombre de la clase en la que está inscrito.

SELECT Alumnos.nombre AS alumno, Clases.nombre AS clase
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+------------------------+
| alumno |         clase          |
+--------+------------------------+
| Juan   | Matemáticas 101        |
| Juan   | Historia Antigua       |
| María  | Literatura Moderna     |
| María  | Biología Avanzada      |
| Pedro  | Química Orgánica       |
| Pedro  | Física Cuántica        |
| Laura  | Arte Contemporáneo     |
| Laura  | Inglés Avanzado        |
| Carlos | Economía Internacional |
| Ana    | Derecho Penal          |
+--------+------------------------+

- Obtener el nombre del alumno y la materia de las clases en las que está inscrito.

SELECT Alumnos.nombre AS alumno, Clases.materia
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+-------------+
| alumno |   materia   |
+--------+-------------+
| Juan   | Matemáticas |
| Juan   | Historia    |
| María  | Literatura  |
| María  | Biología    |
| Pedro  | Química     |
| Pedro  | Física      |
| Laura  | Arte        |
| Laura  | Idiomas     |
| Carlos | Economía    |
| Ana    | Derecho     |
+--------+-------------+

- Obtener el nombre del alumno, la edad y el nombre del profesor de las clases en las que está inscrito.

SELECT Alumnos.nombre AS alumno, Alumnos.edad, Clases.profesor
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+------+------------+
| alumno | edad |  profesor  |
+--------+------+------------+
| Juan   | 20   | Profesor X |
| Juan   | 20   | Profesor Y |
| María  | 21   | Profesor Z |
| María  | 21   | Profesor W |
| Pedro  | 19   | Profesor V |
| Pedro  | 19   | Profesor U |
| Laura  | 22   | Profesor T |
| Laura  | 22   | Profesor S |
| Carlos | 20   | Profesor R |
| Ana    | 19   | Profesor Q |
+--------+------+------------+

- Obtener el nombre del alumno y la dirección de las clases en las que está inscrito.

SELECT 
    Alumnos.nombre AS alumno,
    Alumnos.direccion
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id;

+--------+-----------+
| alumno | direccion |
+--------+-----------+
| Juan   | Calle A   |
| Juan   | Calle A   |
| María  | Calle B   |
| María  | Calle B   |
| Pedro  | Calle C   |
| Pedro  | Calle C   |
| Laura  | Calle D   |
| Laura  | Calle D   |
| Carlos | Calle E   |
| Ana    | Calle F   |
+--------+-----------+

- Obtener el nombre del alumno y el nombre de la clase junto con el profesor.

SELECT Alumnos.nombre AS alumno, Clases.nombre AS clase, Clases.profesor
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+------------------------+------------+
| alumno |         clase          |  profesor  |
+--------+------------------------+------------+
| Juan   | Matemáticas 101        | Profesor X |
| Juan   | Historia Antigua       | Profesor Y |
| María  | Literatura Moderna     | Profesor Z |
| María  | Biología Avanzada      | Profesor W |
| Pedro  | Química Orgánica       | Profesor V |
| Pedro  | Física Cuántica        | Profesor U |
| Laura  | Arte Contemporáneo     | Profesor T |
| Laura  | Inglés Avanzado        | Profesor S |
| Carlos | Economía Internacional | Profesor R |
| Ana    | Derecho Penal          | Profesor Q |
+--------+------------------------+------------+

- Obtener el nombre del alumno, la materia y el nombre del profesor de las clases en las que está inscrito.

SELECT Alumnos.nombre AS alumno, Clases.materia, Clases.profesor
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+-------------+------------+
| alumno |   materia   |  profesor  |
+--------+-------------+------------+
| Juan   | Matemáticas | Profesor X |
| Juan   | Historia    | Profesor Y |
| María  | Literatura  | Profesor Z |
| María  | Biología    | Profesor W |
| Pedro  | Química     | Profesor V |
| Pedro  | Física      | Profesor U |
| Laura  | Arte        | Profesor T |
| Laura  | Idiomas     | Profesor S |
| Carlos | Economía    | Profesor R |
| Ana    | Derecho     | Profesor Q |
+--------+-------------+------------+

- Obtener el nombre del alumno, la edad y la materia de las clases en las que está inscrito.

SELECT Alumnos.nombre AS alumno, Alumnos.edad, Clases.materia
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+------+-------------+
| alumno | edad |   materia   |
+--------+------+-------------+
| Juan   | 20   | Matemáticas |
| Juan   | 20   | Historia    |
| María  | 21   | Literatura  |
| María  | 21   | Biología    |
| Pedro  | 19   | Química     |
| Pedro  | 19   | Física      |
| Laura  | 22   | Arte        |
| Laura  | 22   | Idiomas     |
| Carlos | 20   | Economía    |
| Ana    | 19   | Derecho     |
+--------+------+-------------+

- Obtener el nombre del alumno, la dirección y el profesor de las clases en las que está inscrito.

SELECT Alumnos.nombre AS alumno, Alumnos.direccion, Clases.profesor
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id;

+--------+-----------+------------+
| alumno | direccion |  profesor  |
+--------+-----------+------------+
| Juan   | Calle A   | Profesor X |
| Juan   | Calle A   | Profesor Y |
| María  | Calle B   | Profesor Z |
| María  | Calle B   | Profesor W |
| Pedro  | Calle C   | Profesor V |
| Pedro  | Calle C   | Profesor U |
| Laura  | Calle D   | Profesor T |
| Laura  | Calle D   | Profesor S |
| Carlos | Calle E   | Profesor R |
| Ana    | Calle F   | Profesor Q |
+--------+-----------+------------+

- Obtener el nombre del alumno y la materia de las clases en las que está inscrito, ordenado por el nombre del alumno.

SELECT Alumnos.nombre AS alumno, Clases.materia
FROM Inscripciones
JOIN Alumnos ON Inscripciones.id_alumno = Alumnos.id
JOIN Clases ON Inscripciones.id_clase = Clases.id
ORDER BY Alumnos.nombre;

+--------+-------------+
| alumno |   materia   |
+--------+-------------+
| Ana    | Derecho     |
| Carlos | Economía    |
| Juan   | Matemáticas |
| Juan   | Historia    |
| Laura  | Arte        |
| Laura  | Idiomas     |
| María  | Literatura  |
| María  | Biología    |
| Pedro  | Química     |
| Pedro  | Física      |
+--------+-------------+

- Contar cuántos alumnos están inscritos en cada clase.

SELECT Clases.nombre AS clase, COUNT(Inscripciones.id_alumno) AS total_alumnos
FROM Clases
LEFT JOIN Inscripciones ON Clases.id = Inscripciones.id_clase
GROUP BY Clases.nombre;

+------------------------+---------------+
|         clase          | total_alumnos |
+------------------------+---------------+
| Arte Contemporáneo     | 1             |
| Biología Avanzada      | 1             |
| Derecho Penal          | 1             |
| Economía Internacional | 1             |
| Física Cuántica        | 1             |
| Historia Antigua       | 1             |
| Inglés Avanzado        | 1             |
| Literatura Moderna     | 1             |
| Matemáticas 101        | 1             |
| Química Orgánica       | 1             |
+------------------------+---------------+

``` sql
