### MySql

## MySQL

Structure Query Language

## ACID

	1. Atomicity --> All or nothing.

	2. Consistency --> Transactions are valid to rules of the BD.

	3. Isolation --> Results of the transaction are as if they were done end to end. (Transactions shouldnt be dirty by external transactions)

	4. Durability --> Once a transaction is committed, it reamins so.

## DML --> Data Manipulation Language

## DDL --> Data Definition Languague

## Configurar Sql

Para la configuracion de nuestra base de datos MySql nos ayudaremos de docker, utilizaremos el siguiente comando para subir un contenedor que contenga la imagen.

		1. docker run --name mysqldb -p 3306:3306 MYSQL_ALLOW_EMPTY_PASSWORD=yes -d mysql

## Crear Base de datos

		1. CREATE DATABASE <name_DB>;		

## Crear Usuarios 

		1. CREATE USER '<user_name>'@'<host>' IDENTIFIED BY '<password>';
			Ex: CREATE USER 'sfg_dev_user'@'localhost' IDENTIFIED BY '1234';
			Ex: CREATE USER 'sfg_dev_user'@'192.168.55.55' IDENTIFIED BY '1234';		
			CREATE USER 'sfg_dev_user'@'%' IDENTIFIED BY '1234';

## Permisos De usuario

		1. GRANT SELECT ON <db_name>.* to 'sfg_dev_user'@'%';

		2. GRANT INSERT ON <db_name>.* to 'sfg_dev_user'@'%';

		3. GRANT DELETE ON <db_name>.* to 'sfg_dev_user'@'%';
		
		4. GRANT UPDATE ON <db_name>.* to 'sfg_dev_user'@'%';		


		Con los permisos anterior se le estará indicando que el suuario sfg_dev_user tendrá permisos de INSERT, SELECT, DELETE y UPDATE en todas las tablas de la base de datos <db_name>.	

