1) ¿Cuántas películas y series se agregaron cada año?
  
   *Respuesta:*

   SELECT 
  
   year_added_netflix,
  
   type,
  
   COUNT(*) as contenido_agregado
  
   FROM "AwsDataCatalog"."glue-db-movies"."tabla-netflix-clean"
  
   WHERE year_added_netflix IS NOT NULL
  
   GROUP BY year_added_netflix, type
  
   ORDER BY year_added_netflix asc;



   Ejemplo de la primera consulta: ![ETL](https://raw.githubusercontent.com/iscatalan/LabGlue/refs/heads/main/LabServerless%20(2).png)

   ****

2) ¿Cómo se distribuyen las películas y series por país?

   *Respuesta:*

   SELECT 
   
   country,
   
   type,
   
   COUNT(*) as total
   
   FROM "AwsDataCatalog"."glue-db-movies"."tabla-netflix-clean"
   
   WHERE country IS NOT NULL
   
   GROUP BY country, type
   
   ORDER BY total DESC

   ****

3) ¿Cuáles son las películas y series clasificadas como comedias?

   *Respuesta:*

   SELECT 
   
   title,
   
   type,
   
   country,
   
   release_year,
   
   listed_in
   
   FROM "glue-db-movies"."tabla-netflix-clean"
   
   WHERE listed_in LIKE '%Comedies%'
   
   ORDER BY release_year DESC

   ***** 
4) ¿Cómo evolucionan las tendencias de producción a lo largo del tiempo usando el año de estreno?

   *Respuesta:*

   SELECT 
   
   release_year,
   
   type,
   
   COUNT(*) AS total
   
   FROM "AwsDataCatalog"."glue-db-movies"."tabla-netflix-clean"
   
   WHERE release_year IS NOT NULL
   
   GROUP BY release_year, type
   
   ORDER BY release_year ASC;


**DESAFÍO: REALIZAR CONSULTAS Y RESPONDER LAS SIGUIENTES PREGUNTAS:**

**Directores**

5) ¿Qué directores aparecen más veces en el catálogo?

6) ¿Qué directores han producido contenido en Chile?

**Géneros** 

7) ¿Cuáles son los géneros más comunes en el catálogo?

8) ¿Cómo se distribuyen los géneros de películas y series por país?


Así, puedes seguir explorando los datos mediante consultas según las preguntas que se te ocurran


**¡Felicidades, has completado el laboratorio!**




