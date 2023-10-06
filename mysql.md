# CONSULTAS
Una consulta es una declaración que declara lo que estamos buscando, donde encontrarlo y opcionalmente como transformalos andes de qeu se devuelvan
<br>
id autocincrementar ayuda a saber cuando se creo el registro
<br>
## SELECT
Declaración SELECT , se utiliza para seleccionar datos de una base de datos.
**SELECT colum1,column2 FROM table_name;**
**SELECT column1,another_column; FROM mytable;** <br>
**SELECT** : Lista de seleccion, lista de atributos <br>
**FROM** : Origen de datos, lista de tablas. <br> 

SELECT DISTINCT : Devuelve valores distintos.<br>
**SELECT DISTINCT column1,column2 FROM table_name;** <br>
**DISTINCT** : palabra clave que eliminara ciegamente las filas duplicadas, busca valores unicos de la columna
>SELECT COUNT(DISTINCT Country) FROM Customers;

## WHERE 
Se utiliza para filtrar registros, extraer solo aquello regitros que cumpleuna condicion especifica, devuelve ciertos valores.
**SELECT column1,column2 FROM table_name WHERE condition;**
<br>
**WHERE** : Condición de Seleccion.
>SELECT * FROM Customres WHERE Country = 'Mexico';<br>
>SELECT * FROM Customers WHERE NOT city = 'Berlin'; <br>
>SELECT * FROM Customers WHERE City = 'Berlin' AND postalcode = 12209;<br>
>SELECT * FROM Customers WHERE city = 'BERLIN' OR city = 'London';<br>
>SELECT * FROM  Customers WHERE Country = 'Germany' AND city = 'Berlin';
>

>SELECT * FROM customers WHERE NOT country = 'Germany';
>
>SELECT * FROM customers WHERE NOT country = 'Germany' AND NOT Country = 'USA';
>
>SELECT * FROM Customers WHERE Country = 'Germany' AND (city = 'Berlin' OR city = 'Stuttgart');
>SELECT COUNT(Professor_Name) FROM SALARIES WHERE Salary > 1500000;<br>

>SELECT * FROM movies WHERE id = 6;<br>
>SELECT * FROM movies WHERE id BETWEEN 1 AND 5;
>SELECT * FROM movies WHERE year BETWEEN 2000 AND 2010;<br>
>SELECT * FROM movies WHERE year NOT BETWEEN 2000 AND 2010; <br>
>SELECT * FROM movies WHERE id BETWEEN 1 AND 5;<br>

Tambien se puede utilizar para crear consultas con restricciones<br>
>SELECT column,another_column FROM mytable WHERE condition AND/OR another_condition AND/OR..;<br>
La cláusula WHERE permite tambien realizar comparación de cadenas. <br>

**Operador LIKE(COMO)** : tiene la particularidad de ser CaseInsensitive,comparación de cadenas exactas, en ocaciones se usa cuando se desconoce <br>
**Operador %** : se usar para hacer coincidir una secuencia de cero o mas caracteres, si la columna de texto incluye al medio,inico o al final, es peligroso % se usa para buscar los que 
incluye el texto<br>
>SELECT * FROM movies WHERE title LIKE "%TOY STORY%"; #Buscar todas las peliculas de Toy Story <br>
>SELECT * FROM movies WHERE title LIKE "TOY STORY%"; <br>
>SELECT * FROM movies WHERE director LIKE "%John%"; #Buscar todas la peliculas con el director John Lasseter
>SELECT * FROM movies WHERE director NOT LIKE "%%";<br>
>SELECT * FROM movies WHERE title LIKE "%wall-%" <br>

**SELECT DISTINCT column, another_column FROM mytable WHERE codition;**
>
## ORDER BY
Es una palabra clave que se utiliza para ordenar el conjunto de resultados en orden ascendente o descendente.<br>
Los ordena de forma predeterminada. Para ordenar en orden descendete se utiliza DESC.
**ORDER BY** : columnas en ordenación, lista de atributos, consulta de resumen.<br>
**SELECT column1, column2 FROM table_name ORDER BY column1,column2 .. ASC|DESC** <br>
>SELECT * FROM Customers ORDER BY Country;
>
>SELECT * FROM Customers ORDER BY DESC;
>
>SELECT * FROM Customers ORDER BY Country,City;
>
>SELECT * FROM Customers ORDER BY Country, CustomerName; #Ordenar varias columnas
>
>SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC;
>
**SELECT column, another_column FROM mytable WHERE condition ORDER BY column ASC/DESC;**
<br><br>
**SELECT column, another_column FROM mytable WHERE conditon ORDER BY column ASC/DESC LIMIT num_limit OFFSET num_offset;**
<br>
**LIMIT** : Reduce el numero de filas a devolver(opcional), limita el numer ode resultados, funcionas despues que la hallan ordenado, limitar es clave de optimización. <br>
**OFFSET** : especifica desde donde empieza a contar el numero de filas. <br>
>SELECT DISTINCT director FROM movies ORDER BY director;
>
>SELECT * FROM movies ORDER BY year DESC LIMIT 4;
>
>SELECT * FROM movies ORDER BY ASC LIMIT 5;
>
>SELECT * FROM movies ORDER BY title ASC limit 5 OFFSET 5; #VER LOS SIGUIENTES 5 RESULTADOS, DESPUES DE LOS 5 PRIMEROS};
>

## REWIEW SIMPLE SELECT QUERIES(SQL BOLT)
>SELECT * FROM north_american_cities WHERE Country = "Canada";
>
>SELECT * FROM north_american_cities WHERE country LIKE "united state0 ORDER BY latitude DESC";
>
>SELECT * FROM north_american_cities WHERE longitude <= -87.69 ORDER BY longitude;
>
>SELECT * FROM nort_america_cities WHERE country = 'MEXICO' order by population DESC LIMIT 2;
>
>SELECT population,city FROM north_american_cities WHERE COUNTRY = 'United States' ORDER BY population DESC LIMIT 2 OFFSET 2;
>
## INSERT INTO (INSERTAR EN)
Insertar nuevos registros en la tabla.<br>
> Se pueden insert de 2 maneras:
> <li>INSERT INTO table_name(column1,column2,column3) VALUES(value1,value2,value3);</li>
> <li>INSERT INTO table_name VALUES (value1,value2..);</li>
<br>**INSERTAR DATOS EN COLUMNAS ESPECIFICAS** <br>
>INSERT INTO Customers (CustomerName,City, Country) VALUES('Cardinal','Stavanger','Norway');
>
## NULL Values
Null es un campo sin valor, se utiliza si el valor en el campo es opcional, es diferente a cero o de un campo que contenga espacios.<br>
**SELECT column_names FROM table_name WHERE column_name IS NULL;**
**SELECT column_names FROM table_name WHERE column_name IS NOT NULL;**
**SELECT CustomerName, ContactName Address FROM Customers WHERE Address IS NULL**
>
## UPDATE(ACTUALIZACIÓN)
Modifica registros exitentes en una tabla, pertenece a DML(Manipulación de Datos).
**UPDATE table_name SET column1 = value1, column2=value2.. WHERE condition;**
>🚩 La clausula **where** especifica que registros deben actualizarse.
>
>**SET** : En este caso se utiliza para asignar un nuevo valor a la columna.
>
>>**UPDATE Customers SET ContacName = 'Alfred Schmidt', CIty = 'Frankfurt' WHERE CUstomerID =1; #Actualiza el primer cliente con nueva persona de contacto y una nueva ciudad**
>>
>**ACTULIZAR VARIOS REGISTROS**
>>**UPDATE Customers SET PostalCOde = 00000 WHERE Country = 'Mexico'; # Se actualiza el codigo postal donde el pais sea Mexico**
>>🚩 **UPDATE Customers SET PostalCode =00000; #Se actualizan todos los registros**
>
## DELETE(BORRAR)
Elimina registros existenes de una tabla.
**DELETE FROM table_name WHERE condition;**
>
**DELETE FROM Customers WHERE CustomerName ='Slfreds Futterkiste'**
>
**DELETE FROM table_name #borra todos los registros.**
>
## LIMIT(LIMITE)
Se utiliza para especificar el número de registros a devolver, es utilis en tablas grandes con muchos registros. Devuelven una gran cantidad de registros puede afectar el rendimiento.
>
**SELECT column_name FROM table_name WHERE condition LIMIT number;**
>
**SELECT * FROM Customers LIMIT 3; #Devuelve los primeros 3 registros de la tabla**
>
**SELECT FROM Customers LIMIT 3 OFFSET 3; #Devuelve 3 registros empezando por el cuarto**
>
**SELECT * FROM Customers WHERE country ="Germay" LIMIT 3;**
>
## FUNCIONES MIN() MAX()
>MIN() : devuelve el valor mas pequeño de la columna seleccionada.
>MAX(): devuelve el valor maximo de una columna.
>
>**SELECT MAX() FROM table_name WHERE condition;**
>
>**SELECT MIN(price) AS SmallestPrice FROM Products;**
>>**AS**: Lo utiliza como una alias SmalletsPrice.
>
## FUNCIONES COUNT(), AVG(), SUM()
>**COUNT()**: Devuelve el numero de filas que coimciden con un criterio especifico, contar.
>>**SELECT COUNT(column_name) FROM table_name WHERE condition;**
>
>**AVG()**: Devuelve el valor promedio de una columna numérica
>>**SELECT AVG(column_name) FROM table_name WHERE condition;**
>
>**SUM()**: Devuelve la suma total de una columna numerica.
>>**SELECT SUM(column_name) FROM table_name WHERE condition;**
>>
>**SELECT COUNT(ProductID) FROM Products;**
>**SELECT COUNT(*) FROM Products WHERE Price = 18;**
>
>**SELECT AVG(Price) FROM Products;**
>
>**SELECT SUM(Quantity) FROM OrderDetails;**
>
## OPERADOR LIKE
Este operador de utiliza en una claúsula WHERE para buscar un patrón específico en una columna.<br>
>Hay 2 comodines que se utilizan a menudo con el operador LIKE:
>>Signo **%** representa cero, uno ovarios caracteres.
>>
>>Signo **_** representa un solo caracter.
>>
>>🚩Tambien se pueden combinar los 2 signos.
>>
>**SELECT column1,column2 FROM table_name WHERE columnN LIKE pattern;**
>> <li> 'a%' : inicia con a</li>
>>SELECT * FROM Customers WHERE CITY LIKE 'a%'
>>SELECT * FROM Customers WHERE City LIKE 'ber%';
>
>> <li> '%a' : termina con a</li>
>> <li> '%or%' : buscar valores con 'or' en cualquier posicion</li>
>>SELECT * FROM Customers WHERE CIty LIKE '%es%';
>
>> <li> '%_r%' : buscar valores con 'r' en la segunda posicion</li>
>>SELECT * FROM Customers WHERE City LIKE '_ondon';
>>SELECT * FROM Customers WHERE City LIKE 'L_n_on';
>
>> <li> '%a_%' : buscar valores que inician con 'a' que tenga 2 caracteres de longitud</li>
>> <li> 'a%o' : buscar valores que inician con 'a' y terminan con 'o'</li>
>>SELECT * FROM Customers WHERE City NOT LIKE 'a%';
>
## OPERADOR IN
<div>Permite especificar múltiples valores en la cláusula. </div>
<div>El operador IN es una abreviatura de multiples OR</div>

**SELECT column_name FROM table_name WHERE column_name IN (value1,value2);**
>
**SELECT column_name FROM table_name WHERE column_name IN (SELECT STATEMENT)**
>
>**SELECT * FROM Customers WHERE COuntry IN('Germany','France','UK') #Selecciona todos los cliente en Alemania,Francia o UK**
>
>**SELECT * FROM Customers WHERE Country NOT IN ('Germany','France','UK')**
>
>**SELECT * FROM Customers WHERE Countrty IN (SELECT Country FROM Suppliers);**
>>
## OPERADOR BETWEEN
<div>Permite seleccionar valores dentro de un rango determinado. Los valores pueden ser numeros,texto o fechas, incluye vlores inicial y final.</div>





