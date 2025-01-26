# Tarea

## Elegí estas SGBD 
 *MySQL, MongoDB, Neo4j, Amazon RDS y Cassandra.*

## Preguntas
### MySQL
**¿Cuál es su modelo de datos principal (relacional, NoSQL, grafos, etc.)?**   

*Basado en el modelo relacional* 

**¿Cuáles son sus principales características técnicas?**  

*Soporta transacciones ACID para mantener la integridad de los datos.*  

**¿En qué casos de uso se recomienda utilizarlo?**    

*Aplicaciones web tradicionales.*

**¿Qué ventajas tiene frente a otros SGBD similares?**    

*Facilidad de uso y configuración.*  

**¿Cuáles son sus limitaciones o desventajas?**   

*Menor rendimiento en consultas complejas comparado con SGBD especializados.*

###  MongoDB
¿Cuál es su modelo de datos principal (relacional, NoSQL, grafos, etc.)?  

*Documentos (NoSQL).*

¿Cuáles son sus principales características técnicas?  

*Consultas avanzadas, índices compuestos y búsqueda basada en texto.*

¿En qué casos de uso se recomienda utilizarlo?  

*Comercio electrónico, IoT, y redes sociales.*

¿Qué ventajas tiene frente a otros SGBD similares?  

*Fácil de integrar con aplicaciones modernas.*

¿Cuáles son sus limitaciones o desventajas?  

*Consultas complejas menos eficientes comparadas con SGBD relacionales.*

### Neo4j
¿Cuál es su modelo de datos principal (relacional, NoSQL, grafos, etc.)?  

*Grafos.*

¿Cuáles son sus principales características técnicas?  

*Diseñado para trabajar con datos interconectados mediante nodos y relaciones.*


¿En qué casos de uso se recomienda utilizarlo?  

*Análisis de rutas y gráficos complejos*

¿Qué ventajas tiene frente a otros SGBD similares?  

*Rendimiento superior para análisis de relaciones y conexiones.*


¿Cuáles son sus limitaciones o desventajas?  

*No es ideal para datos tabulares o aplicaciones que no involucran relaciones complejas.*

### Amazon RDS
¿Cuál es su modelo de datos principal (relacional, NoSQL, grafos, etc.)?  

*Relacional.*

¿Cuáles son sus principales características técnicas?  

*Servicio gestionado en la nube que soporta motores como MySQL, PostgreSQL, Oracle, SQL Server, entre otros.*


¿En qué casos de uso se recomienda utilizarlo?  

*Aplicaciones en la nube que requieren alta disponibilidad.*

¿Qué ventajas tiene frente a otros SGBD similares?  

*No requiere gestión manual del hardware o mantenimiento del servidor.*

¿Cuáles son sus limitaciones o desventajas?  

*Costes recurrentes que pueden aumentar según el uso.*

### Cassandra
¿Cuál es su modelo de datos principal (relacional, NoSQL, grafos, etc.)?  

*Clave-Valor (NoSQL).*

¿Cuáles son sus principales características técnicas?  

*Alta disponibilidad y replicación automática entre nodos.*


¿En qué casos de uso se recomienda utilizarlo?  

*Aplicaciones distribuidas con altos requerimientos de disponibilidad.*

¿Qué ventajas tiene frente a otros SGBD similares?  

*Gran capacidad para manejar grandes cantidades de datos distribuidos.*


¿Cuáles son sus limitaciones o desventajas?  

*Administración y configuración más complejas que otros SGBD.*


---

## Cuadro Comparativo  
| Nombre del SGBD | Tipo | Modelo de datos |	Características principales |	Ventajas	| Limitaciones	| Casos de uso |
|-----------------| ---- | --------------- | ----------------------------| ---------| ------------- | ------------ |
| MySQL | Relacional | Relacional | Sistema Open Source y Compatible con SQL estándar. | Facilidad de uso, alta escalabilidad para aplicaciones pequeñas o medianas y Comunidad grande. | Limitada para datos no estructurados y No tan eficiente para grandes volúmenes de datos distribuido | Aplicaciones web tradicionales, sistemas de gestión empresarial, y análisis de datos estructurados. |
| MongoDB | NoSQL | Documentos (JSON) | Base de datos orientada a documentos y  Escalabilidad horizontal. | Manejo eficiente de datos no estructurados y Fácil de escalar. | Mayor consumo de almacenamiento. | Aplicaciones que manejan grandes volúmenes de datos no estructurados, como comercio electrónico o IoT. |
| Neo4j | Orientado a grafos	 | Grafos | Modelo basado en nodos y relaciones y Optimizado para grafos complejos. | Excelente rendimiento en análisis de relaciones. | No es ideal para datos tabulares o no relacionados y Costoso en comparación con otras opciones. | Análisis de redes sociales, sistemas de recomendaciones, y análisis de rutas. |
| Amazon RDS | Almacenamiento en la nube | Relacional (y más) | Servicio gestionado, compatible con varios motores (MySQL, PostgreSQL, etc.) y Escalabilidad automática. | Sin necesidad de gestión manual con su alta disponibilidad y recuperación ante desastres. | Dependencia del proveedor con costes recurrentes.  | Aplicaciones en la nube, SaaS, y sistemas con requerimientos altos de disponibilidad. |
| Cassandra | NoSQL | Clave-Valor	 | Alta tolerancia a fallos y basada en arquitectura distribuida. | Manejo eficiente de grandes volúmenes de datos y excelente para escritura intensiva. | Complejidad en su administración y menor flexibilidad en consultas complejas. | IoT, análisis en tiempo real, y aplicaciones distribuidas con alto tráfico de datos. |

---
## Conclusión

*De los SGBD que he investigado, creo que MongoDB es el más interesante porque trabaja muy bien con datos no estructurados y es flexible para hacer consultas. Es perfecto para aplicaciones modernas que necesitan escalar rápido, como tiendas online o proyectos de IoT. Además, al usar documentos JSON, resulta fácil de entender y trabajar con tecnologías actuales. Aunque ocupa más espacio que otros sistemas, sus ventajas en rendimiento y flexibilidad lo hacen ideal para proyectos que buscan adaptarse rápido a los cambios.*
