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

Agrupaciones de elementos.

## Documents

Information that I store in the collections, usually the documents have the JSON format.

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

			2. db.<collection>.insert(info) -> Insertar informacion.

			3. db.<collection>.find() --> Muestra todos los elementos de una coleccion.

			4. db.<collection>.find({ "_id": ObjectID("1233")}) --> Buscar por id.

			5. db.<collection>.drop() --> Elimina la coleccion;		

			6. db.<collection>.update(search, newValues); --> Update Document			

			7. db.<collection>.remove(search) --> Elimina one document;	

## Identity Mongo

What happend if we insert two documents in the same collection with the same id?

		var id = ObjectID();

		db.personas.insert({
			_id: id,
			nombre:"Andres"
		});

		db.personas.insert({
			_id: id,
			nombre:"Felipe"
		});

In the above code mongo is going to fail, because mongo is not able to insert more than one document with the same "_id".


## Example

		var searchOne = {_id: ObjectId("53324f968779e42")};
		var searchTwo = {_id: ObjectId("53324f978779e43")};

		db.modelosCelulares.update(searchTwo, { 
			"_id" : ObjectId("53324f968779e42"), 
			"marca" : "Motorola", 
			"modelo" : "C115", 
			"introduccion" : 2006});

		db.modelosCelulares.remove(searchOne,{
			"_id" : ObjectId("53324f968779e43"), 
			"marca" : "Nokia", 
			"modelo" : "5110", 
			"introduccion" : 1998 
			})

		db.modelosCelulares.insert({
			"marca" : "Nokia", 
			"modelo" : "5110", 
			"introduccion" : 1998 
			});

## Searching with Mongo

Search set of information.

		db.personas.find({nombre: 'Andres'});

Search with nested values.

		db.personas.find({'direccion.altura': 400});

With more than one fields.

		db.persona.find({
			nombre: 'Andres',
			'direccion.altura':400
		});

Applying set property


		db.modelosCelulares.update({},		
		{
			$set: {
			pantalla: "monocromática",
			tecnologia:"GSM"
			}
		}
		);

## Complex Search

		db.personas.find({ 'direccion:altura' : {
			$gt: 400 }});


In the following link you can find the list of Query Operator for mongo

https://docs.mongodb.com/manual/reference/operator/query-comparison/