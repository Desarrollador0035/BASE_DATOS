# LESSON 4
1. SELECT DISTINCT (director) FROM movies ORDER BY director;
2. SELECT * FROM movies ORDER BY year DESC LIMIT 4;
3. SELECT * FROM movies ORDER BY title ASC LIMIT 5;
4. SELECT * FROM movies ORDER BY title ASC LIMIT 5 OFFSET 5;

# LESSON 5
1. SELECT * FROM north_american_cities WHERE Country = "Canada";
2. SELECT city,latitude FROM north_american_cities WHERE country LIKE "united state" ORDER BY latitude DESC";
3. SELECT * FROM north_american_cities WHERE longitude <= -87.69 ORDER BY longitude;
4. SELECT city,population FROM nort_america_cities WHERE country LIKE 'MEXICO' ORDER BY population DESC LIMIT 2;
5. SELECT population,city FROM north_american_cities WHERE COUNTRY LIKE 'United States' ORDER BY population DESC LIMIT 2 OFFSET 2;

# LESSON 6
La normalizacion minimiza los datos duplicados en cualquier tabla y permite que los datos crescan independientemente.
Cuando se utilizam multiples tablas ortogonales se hace mediante la normalizacion.
> Las tablas que comparten informacion sobre una unica entidad deben tener una clave principal que identifique esas entidad de forma unica en la base de datos.
> <b>Al utilizar la claúsula JOIN se pueden combinar datos de filasa en dos tablas separadas usando esta clave unica.</b>
<div><b>SELECT column, another_table_column,otra_columna_de_la_tabla
FROM mytable
INNER JOIN another_table
ON mytable.id = another_table.id
WHERE condition
ORDER BY column,
LIMIT num_limit OFFSET num_offset;</b></div>
<br>
> <b>INNER JOIN :</b> es un proceso que hace coincidir filas de la primera tabla y la segunda tabla que tienen la misma clave
<br>
<div> JOIN: cuando hacemos relaciones entre 2 tablas queremos recuperar datos de una tabla y llevarlo a otra</div>
<br>
<h3>Analizando las Consultas</h3><br>
1. SELECT title FROM movies JOIN boxoffice; -- Sin condicion esta repitiendo filas porque no esta haciendo relacion<BR>
2. SELECT title, movie_id FROM movies JOIN boxoffice;<BR>
3. SELECT title, movie_id FROM movies INNER JOIN boxoffice ON id = movie_id; --se hizo la relacion entre las 2 tablas<BR>
/*Seleccioname title y movie_id de la tablas movies, me traes la informacion de la tabla boxoffice donde se relaciona
id con movie_id*/<BR>
4. SELECT title,movie_id, domestic_sales,international_sales FROM movies INNER JOIN boxoffice ON id = movie_id; -- respuesta<BR>
5. # la siguiente : SELECT title, domestic_sales, international_sales FROM movies INNER JOIN boxoffice ON id = movie_id
WHERE international_sales > domestic_sales;<BR>
6. # siguiente : SELECT title,domestic_sales, international_sales FROM movies INNER JOIN boxoffice ON id = movie_id ORDER BY rating DESC;
