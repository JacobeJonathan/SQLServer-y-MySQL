## Curso SQL Y Mysql
### como hacer una base de datos
- 1.-Se mira el problema a solucionar
- 2.-Encontramos entidades ejemplo:carro = rectangulos
- 2.1 atributos ejempl:color = redondeadod
- 2.2 relaciones = rombo
- 2.3 sub atributos = redondeados pequeños
- 2.4 identificamod ID Y FK = subrayamos
- 3. cardinalidades 1 a 1 1 a * o * a **
- 4.- Normalizamos 5FN
- 5..-Diagrama relacional
  - Enlace de como diseñar una base de datos ( https://jonmircha.com/bd) muy bueno
<p align="center"><img src="https://i.ibb.co/93jMYBv/img041.jpg" width="700" height="400"></p>
<p align="center"><img src="https://i.ibb.co/JrSFQbL/img042.jpg" width="400" height="700"></p>
<p align="center"  ><img src="https://i.ibb.co/4sK67Nw/img043.jpg" width="400" height="700" ></p>
<p align="center"  ><img src="https://i.ibb.co/gM3BrZ5/img044.jpg" width="400" height="700" ></p>

a normalización en las bases de datos relacionales es uno de esos temas que, por un lado es sumamente importante y por el otro suena algo esotérico. Vamos a tratar de entender las formas normales (FN) de una manera simple para que puedas aplicarlas en tus proyectos profesionales.

Primera Forma Normal (1FN)
Esta FN nos ayuda a eliminar los valores repetidos y no atómicos dentro de una base de datos.

Formalmente, una tabla está en primera forma normal si:

Todos los atributos son atómicos. Un atributo es atómico si los elementos del dominio son simples e indivisibles.
No debe existir variación en el número de columnas.
Los campos no clave deben identificarse por la clave (dependencia funcional).
Debe existir una independencia del orden tanto de las filas como de las columnas; es decir, si los datos cambian de orden no deben cambiar sus significados.
Se traduce básicamente a que si tenemos campos compuestos como por ejemplo “nombre_completo” que en realidad contiene varios datos distintos, en este caso podría ser “nombre”, “apellido_paterno”, “apellido_materno”, etc.

También debemos asegurarnos que las columnas son las mismas para todos los registros, que no haya registros con columnas de más o de menos.

Todos los campos que no se consideran clave deben depender de manera única por el o los campos que si son clave.

Los campos deben ser tales que si reordenamos los registros o reordenamos las columnas, cada dato no pierda el significado.

Segunda Forma Normal (2FN)
Esta FN nos ayuda a diferenciar los datos en diversas entidades.

Formalmente, una tabla está en segunda forma normal si:

Está en 1FN
Sí los atributos que no forman parte de ninguna clave dependen de forma completa de la clave principal. Es decir, que no existen dependencias parciales.
Todos los atributos que no son clave principal deben depender únicamente de la clave principal.
Lo anterior quiere decir que sí tenemos datos que pertenecen a diversas entidades, cada entidad debe tener un campo clave separado. Por ejemplo:
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.30.27-e38ed9bb-5d10-4f2b-acdc-fa2fa45433d3.jpg" width="700" height="300"></p>
En la tabla anterior tenemos por lo menos dos entidades que debemos separar para que cada uno dependa de manera única de su campo llave o ID. En este caso las entidades son alumnos por un lado y materias por el otro. En el ejemplo anterior, quedaría de la siguiente manera:
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.26.28-2a12f9b9-2f11-4a1d-9cb0-23c2595cc260.jpg" width="700" height="300"></p>
Tercera Forma Normal (3FN)
Esta FN nos ayuda a separar conceptualmente las entidades que no son dependientes.

Formalmente, una tabla está en tercera forma normal si:

Se encuentra en 2FN
No existe ninguna dependencia funcional transitiva en los atributos que no son clave

Esta FN se traduce en que aquellos datos que no pertenecen a la entidad deben tener una independencia de las demás y debe tener un campo clave propio. Continuando con el ejemplo anterior, al aplicar la 3FN separamos la tabla alumnos ya que contiene datos de los cursos en ella quedando de la siguiente manera.
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.27.43-92a1523a-c6fc-42e6-85fb-86dd87ee20af.jpg" width="700" height="300"></p>
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.27.52-cb96ff88-e8f4-4957-8bbb-ded1cc6cf599.jpg" width="700" height="300"></p>
Cuarta Forma Normal (4FN)
Esta FN nos trata de atomizar los datos multivaluados de manera que no tengamos datos repetidos entre rows.

Formalmente, una tabla está en cuarta forma normal si:

Se encuentra en 3FN
Los campos multivaluados se identifican por una clave única
Esta FN trata de eliminar registros duplicados en una entidad, es decir que cada registro tenga un contenido único y de necesitar repetir la data en los resultados se realiza a través de claves foráneas.

Aplicado al ejemplo anterior la tabla materia se independiza y se relaciona con el alumno a través de una tabla transitiva o pivote, de tal manera que si cambiamos el nombre de la materia solamente hay que cambiarla una vez y se propagara a cualquier referencia que haya de ella.
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.29.00-ba58de30-a08d-472a-82f9-ea478bf6fcee.jpg" width="700" height="300"></p>
<p align="center"><img src="https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202019-04-30%20a%20la%28s%29%2017.29.29-149d96f3-78e4-4a26-8c4a-0f002c81cc2f.jpg" width="700" height="300"></p>
De esta manera, aunque parezca que la información se multiplicó, en realidad la descompusimos o normalizamos de manera que a un sistema le sea fácil de reconocer y mantener la consistencia de los datos.

Algunos autores precisan una 5FN que hace referencia a que después de realizar esta normalización a través de uniones (JOIN) permita regresar a la data original de la cual partió.
<p align="center"><img src="https://i.ibb.co/6DyPVqk/img045.jpg" width="400" height="700"></p>
<p align="center"><img src="https://i.ibb.co/VHZZnLT/img046.jpg" width="400" height="700"></p>
<p align="center"><img src="https://i.ibb.co/Zf8cmgf/img047.jpg" width="400" height="700"></p>

##Rastrear cambios en una base de datos
https://www.sqlshack.com/es/como-rastrear-el-historial-de-cambios-de-datos-usando-tablas-temporales-con-versiones-del-sistema-en-sql-server-2016/
## MODOS DE AUTENTIFICACION
### Primero vemos que usuarios tenemos:
1.- Nos vamos a la carpeta databases
2.- a la carpeta login
- Por defecto ya nos viene el login sa
peor nos viene desabilitado
- lo habilitamos
-- creamos un query 
ejecutamos el siguiente codigo para habilitar:
alter login sa enable
ejecutamos el siguiente codigo para desabilitar:

### habilitar los dos metodos de autentificacion
- exiten dos tipos por windows y por usuario y contraseña
- clic derecho en desktop...
- propiedades
- seguridad
- en autentificacion de servidor
- clic en windows y modo de autentificacion

### cambiando contraseña de autentificacion
alter login sa with password ='123456'
## CREACION DE LOGINS
### creando usuario de windows
- vemos como se llama nuestra pc: DESKTOP-ESOS2R4
- luego ejecutamos el siguiente codigo:
CREATE LOGIN [DESKTOP-ESOS2R4\Jacob] FROM WINDOWS WITH DEFAULT_DATABASE=master, DEFAULT_LANGUAGE=[español]
### creando usuario de autentificaion
CREATE LOGIN JONATHAN FROM WINDOWS WITH DEFAULT_DATABASE=master, DEFAULT_LANGUAGE=[español],
default_language=[español], check_expiration=on
- que dice el codigo creamos un usuario jonathan con paswword jonathan donde tiene que cambiar la contraseña para entrar y va estar por defecto en la 
base de datos master y la expiracion de la contraseña esta activa
## CREANDO LOGIN EN UNA BASE DE DATOS
- creando un login para la base de datos
- CREATE LOGIN JONATHAN WITH PASSWORD = 'JACOB', DEAFAULT_DATABASE=master,default_laguage=[español]
## CREANDO USUARIOS EN UNA BASE DE DATOS
- creando un usuario para ese login de arriba
CREATE user juan for login jonathan with default_schema=dbo
## ELIMINADO USUARIO 
DROP USER juan
## CREANDO BASE DE DATOS
CREATA DATABASE TIENDA
## USAR LA BASE DE DATOS
USE TIENDA
## QUE SE CONECTEN MULTIPLES USUARIOS A LA BASE DE DATOS
ALTER DATABASE tienda SET MILTI_USER

##DAR PRIVILEGIOS A LOS USUARIOS
- le damos privilegio de crear base de datos a un login: grant create any database to jonathan
bulkadmin: Este rol permite a los usuarios realizar operaciones de importación y exportación masivas de datos mediante el uso de las instrucciones BULK INSERT y OPENROWSET(BULK...).

- dbcreator: Los usuarios con este rol tienen permiso para crear, alterar, eliminar y restaurar bases de datos.

- diskadmin: Este rol permite a los usuarios administrar archivos de datos y registros de transacciones, así como realizar tareas de copia de seguridad y restauración.

- processadmin: Los usuarios con este rol pueden ver y matar los procesos de SQL Server que se están ejecutando en el sistema.

- public: El rol público es un rol especial que contiene todos los usuarios de una base de datos. Todos los usuarios son miembros implícitos del rol público y tienen los permisos asignados a este rol de manera predeterminada.

- securityadmin: Este rol proporciona a los usuarios el control sobre la administración de inicios de sesión, usuarios y roles de servidor.

- serveradmin: Los usuarios con este rol tienen permisos administrativos de nivel superior en todo el servidor. Pueden cambiar la configuración del servidor y realizar otras tareas administrativas.

- setupadmin: Este rol permite a los usuarios administrar instalaciones y desinstalaciones de SQL Server.

- sysadmin: El rol sysadmin es el rol de administrador del sistema más alto en SQL Server. Los usuarios con este rol tienen todos los permisos en el servidor y en todas las bases de datos.
## CREANDO BASE DE DATOS
create database blog = creando base de datos llamado blog
drop data base = eliminado base de datos

use master; = utilizando la base de datos

### creando otra forma base de datos con el tamaño expesifico
  
    create database sales
    on
    ( name = sales_dat,
      filename = 'c:\Program Files\.....\salesdata.mdf',
    size = 10mb,
    maxsize = 50mb,
    filegrowth = 5mb,
    )
    log on
    ( name = sales_log,
      filename = 'c:\Program Files\.....\salesdata.ldf',
    size = 5mb,
    maxsize = 25mb,
    filegrowth = 5mb,
    );
    go
  
- puede ser: kg, mb,gb,tb
- filename = en que directrio se va a guardar la base de datos
- size:en que tamaño de alamacenamiento va a comenzar
- maxsize:hasta que tamaño de almacenamiento se va a aguardar
- filegrowth: de cuanto en cuanto se va incrementar
- MDF: MDF significa "Main Database File" o "Archivo Principal de la Base de Datos". Es el archivo principal de una base de datos en SQL Server y contiene la estructura de la base de datos, así como los datos y los objetos del esquema. El archivo MDF almacena las tablas, índices, procedimientos almacenados y otros objetos de la base de datos.

- LDF: LDF significa "Log Database File" o "Archivo de Registro de la Base de Datos". Este archivo contiene el registro de todas las transacciones realizadas en la base de datos. El archivo LDF se utiliza para garantizar la integridad y la recuperabilidad de la base de datos en caso de fallos o errores. Almacena información secuencial sobre todas las transacciones realizadas, lo que permite recuperar la base de datos hasta el último punto de confirmación en caso de una falla del sistema.

## CREAR LAS COLUMNAS, ACTUALIZAR Y ELIMINAR  LAS COLUMNAS  
- ALTER TABLE venta.dbo.datos
- DROP COLUMN ciudad;

- alter table venta.dbo.datos
- add ciudad varchar(50);
### VISUALIZAMOS LOS DATOS YA ACTUALIZADOS
- select * from datos

### CONTAR CUANTOS SON DE UNA COLUMNA RESPECTIVA
- select COUNT(*) as sexo
- from datos
- Vemos que utilizamos la opcion contar donde la columna es sexo y son extraidos de la tabla datos
### CREANDO TABLA
create table genero(
id integer primary key,
genero varchar(30)
);
## CUANDO UTILIZAR DELETE Y DROP 
- 1.- DELETE: El comando DELETE se utiliza para eliminar filas específicas de una tabla en una base de datos. Puedes utilizar una cláusula WHERE para especificar las condiciones que determinarán qué filas deben ser eliminadas. Por ejemplo:

  - DELETE FROM NombreTabla WHERE Condicion;
- 2.- DROP: El comando DROP se utiliza para eliminar objetos de la base de datos, como tablas, vistas, procedimientos almacenados, etc. Cuando se ejecuta DROP en una tabla, se eliminan tanto los datos como la definición de la tabla. Por ejemplo:

  - DROP TABLE NombreTabla;
## CREANDO TABLAS
create table clientes(
id int ,
nombres nvarchar(50),
apellidos nvarchar(20),
estatura decimal(3,2),
sexo char(1),
dni char(10)

);
select * from clientes
## ALTERAR TABLAS
- agregar, quitar, renombrar columna y quitar tipo de dato
- alter table clientes add  direccion nvarchar(100)
## INSERTAR REGISTROS
- insertar a las tablas datos
- insert into empleados(id, nombres, apellidos, direccion, fecha de nacimiento)
- values (2,'jonathan', ' jacob','psje','11-09-1999')
## ACTUALIZAR REGISTROS
- comando update
- select * from tblEmpleado
- update tblEmpleado set empApellidoPaterno ='Jacobe' where IDEmpleado='1'
- update tblEmpleado set empNumSegSocial = '75171766' where IDEmpleado='1'
## ELIMAR REGISTROS
- comando delete
- delete from tblEmpleado where IDEmpleado= 9

### HASTA AQUI EMOS HECHO CRUD CREATE - INSERT READ - SELECT UPDATE - UPDATE DELETE - DELETE
## BUSQUEDA / SELECCION DE REGISTROS
- comando select
- si queremos que nos traiga todos utilizamos el *
  - select * from tblEmpleado
- si queremo que solo nos traiga algunas cosas o damos asi
  - select IDEmpleado, empNumSegSocial, empApellidoPaterno from tblEmpleado
- si queremos agregar mas especificos
  - select IDEmpleado, empNumSegSocial from tblEmpleado where empNumSegSocial='75171766'
## LLAVES PRIMARIAS
- create table usuarios(
- id int
- Nombre varchar(50),
- COSTRAINT id PRIMARY KEY(id,nombre) 
- );
- tambien alterar las tablas donde no cuentan con id
- alter table usuarios add constraint id primary key(id)
- eliminar los id
- alter table usuarios drop constraint id
## TABLA TEMPORAL
- Es una tabla que se crea en un determinado tiempo y luego deja de existir
- creando una tabla temporal:
-    use venta
-  create table #usuario(
-  	id_usuario int primary key identity,
-  	nombre varchar(10)
-  );
-  insert into #usuario(nombre) 
-  values
-  ('jonathan')
-  select * from #usuario
- si abrimos otro query o queremos hacer otra consulta ya no lo vamos a ver
## PROCESOS O PROCEDIMIENTOS ALMACENADOS
- los procedimientos almacenados de SQL sirven para encapsular y ejecutar lógica de negocio en una base de datos, proporcionando reutilización de código, mejor rendimiento, seguridad, modularidad y soporte para transacciones.

## UTILIZANDO DISTINCT 
- utilizando distinct para que nos devuelva valores unicos

## UTILIZANDO MOD
- utilizamod mod(identificador, divisor)
- mod(id,2)
- lo utilizamos si es divisible y saber si es par
## UTILIZANDO COUNT
- Utilizando count para contar el total y luego restar
- SELECT COUNT(*) - COUNT(DISTINCT CITY) AS Diferencia
- FROM STATION;
## UTILIZANDO LIKE Y OR
- consulta en SQL para obtener la lista de nombres de ciudades que terminen a,e,i,o,u
- SELECT DISTINCT CITY
- FROM STATION
- WHERE CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u';

## UTILIZANDO SUBSTRINC WHERE AND Y IN
- Consulte la lista de nombres de CIUDAD de ESTACIÓN que tienen vocales (es decir, a, e, i, o y u) como primer y último carácter. Su resultado no puede contener duplicados.
-  SUBSTRING para extraer el primer carácter
- IN Comparamos estos caracteres con la lista de vocales utilizando el operador
- SELECT DISTINCT CITY
- FROM STATION
- WHERE SUBSTRING(CITY, 1, 1) IN ('a', 'e', 'i', 'o', 'u')
-  AND SUBSTRING(CITY, -1) IN ('a', 'e', 'i', 'o', 'u');
## UTILIZANDO HAVIG PARA EL FILTRADO DE GRUPOS
- En SQL Server, la cláusula "HAVING" se utiliza junto con la cláusula "GROUP BY" para filtrar los resultados de una consulta basándose en condiciones aplicadas a los grupos resultantes.
- SELECT Producto, SUM(Total) AS TotalVentas
- FROM Ventas
- GROUP BY Producto
- HAVING SUM(Total) > 1000;
- En este ejemplo, la cláusula "GROUP BY" agrupa las filas por el campo "Producto" y la función de agregación "SUM" calcula el total de ventas para cada producto. Luego, la cláusula "HAVING" filtra los grupos y muestra solo aquellos cuyo total de ventas es superior a 1000.

## CONEXION SQL SERVER CON PYTHON
 ```py
  
  import pyodbc

try:
    connection = pyodbc.connect('DRIVER={SQL Server};SERVER=DESKTOP-I3FD54E;DATABASE=venta;UID=sa;PWD=jacob')
    # connection = pyodbc.connect('DRIVER={SQL Server};SERVER=USKOKRUM2010;DATABASE=django_api;Trusted_Connection=yes;')
    print("Conexión exitosa.")
    cursor = connection.cursor()
    cursor.execute("SELECT @@version;")
    row = cursor.fetchone()
    print("Versión del servidor de SQL Server: {}".format(row))
    cursor.execute("SELECT * FROM empleado")
    rows = cursor.fetchall()
    for row in rows:
        print(row)
except Exception as ex:
    print("Error durante la conexión: {}".format(ex))
finally:
    connection.close()  # Se cerró la conexión a la BD.
    print("La conexión ha finalizado.")
  
 ```
## CONEXION MYSQL CON PYTHON
 ```py
 import mysql.connector
from mysql.connector import Error

try:
    connection = mysql.connector.connect(
        host='localhost',
        port=3306,
        user='root',
        password='123456',
        db='django_api'
    )

    if connection.is_connected():
        print("Conexión exitosa.")
        infoServer = connection.get_server_info()
        print("Info del servidor: {}".format(infoServer))
        cursor = connection.cursor()
        cursor.execute("SELECT DATABASE()")
        row = cursor.fetchone()
        print("Conectado a la base de datos: {}".format(row))
except Error as ex:
    print("Error durante la conexión: {}".format(ex))
finally:
    if connection.is_connected():
        connection.close()  # Se cerró la conexión a la BD.
        print("La conexión ha finalizado.")
  
 ```
## CONEXION ORACLE CON PYTHON
```py
import cx_Oracle

"""
Si tienes problemas con tu base de datos en Oracle:

SQLPLUS / AS SYSDBA
Abrir conexión => ALTER PLUGGABLE DATABASE XEPDB1 OPEN;
"""

try:
    connection = cx_Oracle.connect(
        user='USUARIO',
        password='PASSWORD',
        dsn='localhost:1521/XEPDB2',  # Data Source Name
        encoding='UTF-8'
    )
    print(connection.version)
    cursor = connection.cursor()
    cursor.execute("SELECT * FROM NOMBRE_TABLA")
    rows = cursor.fetchall()
    for row in rows:
        print(row)
except Exception as ex:
    print("Error durante la conexión: {}".format(ex))
finally:
    connection.close()  # Se cerró la conexión a la BD.
    print("La conexión ha finalizado.")

```

## CONEXION POSTGRESQL CON PYTHON
```py
import psycopg2
from psycopg2 import DatabaseError

try:
    connection = psycopg2.connect(
        host='localhost',
        user='postgres',
        password='123456',
        database='universidad'
    )

    print("Conexión exitosa.")
    cursor = connection.cursor()
    cursor.execute("SELECT version()")
    row = cursor.fetchone()
    print("Versión del servidor de PostgreSQL: {}".format(row))
    cursor.execute("SELECT * FROM curso")
    rows = cursor.fetchall()
    for row in rows:
        print(row)
except DatabaseError as ex:
    print("Error durante la conexión: {}".format(ex))
finally:
    connection.close()  # Se cerró la conexión a la BD.
    print("La conexión ha finalizado.")


```
## CAMBIAR EL NOMBRE DE UNA TABLA 
- Asi cambiamos de una tabla llamado empleado a una tabla empleados ya que debe ser plural
- exec sp_rename 'dbo.empleado','dbo.empleados'
-                 antiguo      ,   nuevo


<img width="860" height="265" alt="normalizacion_tablas-5e026576-0099-4dff-b7aa-87cae77458d4" src="https://github.com/user-attachments/assets/6a5a3cff-3afc-4c12-9f53-a5f435d3fbc4" />
