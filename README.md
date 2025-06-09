## Laboratorio Athena Quest


**Objetivo General:**  Aprender a usar los servicios de almacenamiento y análisis de datos en AWS, ya sea Amazon S3 y Amazon Athena para guardar datos y realizar consultas SQL que permitan explorar y analizar información 

![Arquitectura AWS](https://github.com/iscatalan/AthenaQuest/blob/main/Arquitectura%20Athena%20Quest%20(1).png)

**Introducción:**  S3 (Simple Storage Service) es un servicio de almacenamiento que permite guardar objetos de forma segura y escalable. La información se organiza en buckets y cada uno debe tener un nombre único a nivel global, es decir, no puede repetirse en ninguna otra cuenta de AWS del mundo. Además, por seguridad los buckets deben estar configurados para bloquear el acceso público, a menos que haya una necesidad muy específica. Esto evita que los datos sean visibles para cualquier persona y protege la privacidad de la información. 
Athena es un servicio de consulta que permite analizar datos directamente desde Amazon S3 usando SQL. No requiere configurar ni administrar servidores, lo que facilita hacer consultas rápidas y flexibles. Athena es ideal para explorar grandes cantidades de datos almacenados en formato CSV, JSON, Parquet, entre otros


**Tarea 1: Extraer los datos para el trabajo del laboratorio**

- Debes descargar el dataset netflix_titles.csv con temática de películas en Kaggle

Link: https://www.kaggle.com/datasets/shivamb/netflix-shows/data

**Tarea 2: Crear una nueva función Lambda**

- En Lambda, crea una nueva función y tienes que elegir “runtime” en Python
- Importante revisar que el rol IAM “LambdaExecutionRole” esté asociado a la función
- Ya creada la función, en la parte del código hay uno preconfigurado. Debes cambiarlo y colocar uno que tenga un flujo de POST y GET más una conexión con DynamoDB
- Debes probar el código en “Test Event”. Para ello creas un evento nuevo, le pones un nombre e insertas en formato JSON el tipo de solicitud que quieres probar
- Tienes que realizar el trabajo de probar con GET para ver qué “username” tienen contraseña en la tabla “Usuarios”
- También, trabajar con POST para comenzar a rellenar la tabla “UsuariosNuevos”. Puede ser username, password, país, según los atributos que quieras

**Tarea 3: Crear API Gateway**
- Debes ir a API Gateway y crear una API HTTP con el nombre que desees 
- Para tu API creada tienes que configurar rutas para GET y POST
- Tienes que integrar las rutas a la función de Lambda que ya creaste en el laboratorio. Debes realizarlo a través de “Manage integrations” y en configuraciones avanzadas cambiar el payload a 1.0 para mayor compatibilidad
- Debes ir a “Stages” configurado por default en la creación de la API. Ahí encontrarás el invoke URL para realizar tus pruebas

**Tarea 4: Probar API en el navegador y CloudShell**
 
- Para probar en GET en el navegador utiliza → invoke URL + /ruta GET + ?username=  &lt;username&gt; (sacado de tabla “Usuarios”)
- En el caso de POST, debes probarlo en el CloudShell del Management Console con los siguientes comandos:
```bash~
curl -X POST \
 invoke URL + /ruta POST \ 
 -H "Content-Type: application/json" \
 -d '{"username":"<nombre>", "<atributo que quieras agregar ": "<value>", “<atributo que quieras agregar>": "<value>"}'  
  + (los que quieras agregar) 
 
Ejemplo:   -d '{"username":"Hugo", "país":"Chile", "password":"1234"}' 
```

**(Opcional) Tarea 5: Probar el flujo de API con Postman**

- Instala Postman si es que no lo tienes, es un programa útil para el trabajo con APIs
- Luego, en API Gateway busca la URL base para Postman que está conformada por el Invoke URL del stage + /(nombre de ruta GET o Post) 
- Para el caso de GET pones el URL en Postman y lo manejas desde “Params” con “username” y value 
- Para POST utilizas el mismo URL, cambias la ruta y te diriges a body en que llenas los datos que deseas insertar en modo JSON. 

**¡Felicidades, has completado el laboratorio!**
