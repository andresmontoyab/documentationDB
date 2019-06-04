# No Sql DB

### Index

* [NoSql](#NoSql)
* [Concepts](#Concepts)
	* [ACID](#ACID)
	* [Collections](#Schema)
	* [Documents](#Tables)
* [MongoDB](#MongoDB)


## NoSql

1. There's no schema in the noSql Database.
2. Super flexible solution.
3. There are no relations.
4. Data is typically merged/nested in a few collection.
5. Can scale in both, horizontal and vertical.
6. Grear performance for mass read & write request.
7. Bad performance for Update queries.

## Concepts

## Collections

## Documents

You can add multiples documents with different information or fields in one collection.

# MongoDB

	1. MongoDB es una base de datos orientada a documentos.

	2. Es una base de datos no Relacional.

	3. Los doucmentos MongoDB son almacenados en BSON.(Binary JSON)

## Why Use MongoDB

	1. Es bueno para "high insert System." tales como sensores de lectura, social media, sistemas de publicidad.

	2. Es bueno cuando necesitas flexibilidad en el esquema.

	3. Puede ademas soportar gran numbero de lectura por segundo.

## Why Avoid MongoDB

	1. MongoDB no tiene el concetp deo transaccion, no ACID, no bloqueo para transacciones.

	2. No es bueno para actualizaciones concurrentes.

## Terminology RDMS vs Mongo DB

	1. Database --> Database
	2. Tables	--> Collection
	3. Row		--> Document
	4. Column	--> Field
	5. Table Join --> Embedded Documents
	6. Primary Key --> Primary Key
	7. Agregattion --> Agregattion Pipeline.


## Inicializar nuestra DB mongo

Para instalar mongo utilizaremos docker y deberemos escribir el siguiente comando.

			1. docker run -p 27017:27017 -v /users/jt/dockerdata/mongo:/data/db -d mongo

## Ingresar a la consola mongo

Una vez tengamos corriendo nuestro contenedor docker deberemos ingresar a este por medio de la shell interactiva, esto con el porposito de tener acceso a la consola de mongo, para poder buscar informacion, filtrar y observar el funcionamiento de nuestra MongoDB.

			1. docker exec -it <name-container> bash --> it(iteractiva mode) 


## Querys Mongo DB


			1. show collections; --> Muestra todas las collections disponibles en la base de datos.

			2. db.<collection>.find() --> Muestra todos los elementos de una coleccion.

			3. db.<collection>.drop() --> Elimina la coleccion;						

