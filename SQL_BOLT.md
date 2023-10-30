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
