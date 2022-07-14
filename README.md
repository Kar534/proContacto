# Conceptos Básicos CRM y Progración - proContacto
test practicos procontacto en palabras del común.

## Instalación Aplicativos requeridos para desarrollo
Algunas herramientas para desarrollo requieren de configuraciónes locales, se relaciona documentación de paso a paso de estas.


### ![image](https://user-images.githubusercontent.com/109252002/179038196-0967cc68-f389-44ec-8026-887bb649613b.png)  Visual Studio Code  

![image](https://user-images.githubusercontent.com/109252002/179027025-90029ef2-94d6-43c5-8d5c-b3df3520638c.png)
Visual Studio Code es un entorno de desarrollo integrado, es decir en ese mismo programa podremos editar o escribir nuestro código, compilarlo o verificar que este correcto, subirlo a nuestro ambiente de desarrollo (ejemplo nuestra organizacion Salesforce), entre otras tareas.

Instalar Visual Studio Code puede ser relativamente fácil, basicamente se descarga el instalador de la pagina https://code.visualstudio.com/Download, se instala en el computador, para el caso de desarrollo salesforce se descarga e instala Salesforce DX CLI y por último se adiciona el pack de extensiones Salesforce en Visual Studio Code, en la web es posible encontrar mucho material relacionado con estas configuraciones, se adicionan algunos links que son muy claros y sencillos para estas mismas:
 
  - https://trailhead.salesforce.com/es-MX/content/learn/projects/quickstart-vscode-salesforce
  
  - https://www.apexhours.com/how-to-setup-visual-studio-code-for-salesforce/



### ![image](https://user-images.githubusercontent.com/109252002/179037934-11f7eff9-0b5e-4098-905d-e2af86aa68db.png) Git & GitBash
![image](https://user-images.githubusercontent.com/109252002/179038664-b8b37030-6861-424a-9b00-57f4fcb231d6.png)

Git te permite tener un versionamiento de objetos o recursos, como ejemplo práctico tendremos un documento inicial que tiene 3 páginas, al ver nuevos requerimientos o necesidades que afectan este documento es posible que un usuario adicione 2 paginas mas, por lo cual tendriamos una v0 (inicial) y una versión 1 con los cambios, el versionamiento sirve por ejemplo para recuperarse a una versión anterior en caso de desestimar las necesidades que se contemplaron para la versión 1.

Debo confesar que no tengo una basta experiencia en el manejo de repositorios git, sin embargo considero que en la pagina de github hay una explicación completa relacionada con Git y su instalación, la cual comparto por medio del siguiente link:

https://github.com/git-guides/install-git


## Conceptos Protocolo HTTP - Servidores WEB
Contextualización de terminos HTTP a bajo nivel

### Servidor HTTP

Puede considerarse tanto como la maquina que contiene los archivos fuentes para desplegar una pagina o un recurso web (HTML, CSS, JS, etc) o el software que procesa las aplicaciones del lado del servidor recibiendo una petición que interpreta para encontrar los archivos correspondientes y regresando el resultado de la búsqueda junto con los datos asociados. 

En la imagen se puede ver una interación entre un usurio que consulta una página o recurso, resumiendo tendriamos:
![peticiones http paso a paso](https://user-images.githubusercontent.com/109252002/179060082-113eec38-8811-420c-b412-7fc111e786c9.jpeg)

1. El usuario solicita una conexión o un recurso al browser (ejemplo consulta la página de trailhead).
2. El browser hace una traducción de la url a petición HTTP.
3. Nuestro servidor HTTP o Web toma esa peticion HTTP y hace una busqueda para encontrar los recursos asociados (ejemplo las imagenes, textos, funciones asociadas a la página que se desea consultar.
4. El server retorna la información resultante al browser (response HTTP)
5. El browser renderiza la página o carga los recursos asociados que retorno la petición.
6. El usuario ve la página web deseada.

Es decir, que el servidor HTTP realizaría las tareas mencionadas en el punto 3 y 4, despues de tener la traducción de lo que requiere el usuario busca los elementos asociados o necesarios y retorna lo encontrado para que el usuario pueda visualizarlo.

### Verbos HTTP

Los verbos HTTP son operaciones que pueden realizarse para un recurso HTTP de un servidor web, los mas conocidos considero son :
- **GET**: utilizado para consultar un recurso y retornar la información asociada (ejemplo consultar las cuentas de tipo prospecto )
- **POST**: permite crear un recurso que pertenece a una colección de datos (ejemplo crear una cuenta en el objeto Account)
- **PATCH**: permite actualizar la información de un recurso/registro (ejemplo actualizar el estado de una cuenta)
- **DELETE**: eliminar el recurso/registro (eliminar una tarea asociada a un cliente como por ejemplo una cita o actividad)

### Request Response HTTP y Headers
Podriamos considerar que el request es la información que permite identificar que registro especifico se busca (paso 3 de la imagen de peticiones http paso a paso), mientras el response agrupa la información resultante (paso 4 de la imagen anterior), por su parte los headers son parámetros ocultos que permiten el envío/recepción de un mensaje HTTP, ejemplo Authorization, que puede permitir una conexión JWT o de otro tipo, en otras palabras los header son literales que pueden indicarle al servidor web el formato que se espera de la información o si requiere de un valor especifico por ejemplo una llave adicional para autorizar la consulta.

### QueryString
Los queryString son parametros que se adicionan a la URL (o consulta) para refinar la información resultante, por ejemplo en un formulario web se ingresa información en varios campos, al pulsar el botón de envío direcciona a una nueva página y puede que la url tenga una configuracion como: 

       http://sitioconsultado/paginadireccionada.html?parametro1=valor1&parametroN=valorN
       donde,
       ? corresponde al caracter que indica el inicio del queryString.
       parametro1, parametroN corresponde a los elementos o variables que permitiran filtrar
       valor1, valorN corresponde a la información que ingresaste en el formulario o los valores que determinan la información resultante.

### ResponseCodes
Son códigos que permiten conocer si la petición fue realizada satisfactoriamente o se presento algún problema, muchas veces se consulta una pagina web y esta demora en responder y finaliza con un codigo y mensaje de error, entre los mensajes que mas he visto y consideraría mas comunes colocaría:

- **200** : Conexión Exitosa
- **400**: Bad Request
- **401**: No Autorizado
- **500**: Error del Servidor
- **502**: Error del Gateway

## Peticiones GET vs POST
Una petición GET envían la información en la url, mientras que peticiones post (creación) requiere de adicionar información en el body del request, esto puede que suene un poco mas complejo pero es sencillo, retomando el ejemplo de la página web y el formulario:
 - Si fuera un formulario de login se estaría realizando un get o una consulta del usuario, por lo cual se enviaría la información (tal vez encriptada) en un queryString en la url.
 - Por su parte si el formulario direcciona a una página de creación se realizaría un POST y necesitaría que se indicara el recurso a utilizar (ejemplo contactos) mas un mensaje con la información ingresada.

En la siguiente imagen se muestra un ejemplo de GET y POST desde Postman
![image](https://user-images.githubusercontent.com/109252002/179071679-8864c100-9d12-4ed6-8328-c98ab351339a.png)

### Verbos HTTP en el navegador
Es bueno aclarar que desde un navegador se realiza una petición get para acceder a una página. Esto lo podemos identificar desde herramientas del desarrollador al consultar una pagina.
![image](https://user-images.githubusercontent.com/109252002/179073419-34919b69-e9c4-48a6-879e-50e1b8dd9291.png)

### Estructuras de datos XML y JSON

XML es un estándar de estructura para compartir información, es de fácil entendimiento para la maquina, usando etiquetas, atributos y elementos, generalmente se utiliza en un estandar de protocolo SOAP, ejemplo:

   ![image](https://user-images.githubusercontent.com/109252002/179075122-2c480fb3-6435-455c-a3fb-c5b8c8bdd220.png)

JSON es un estándar para compartir información que es mas comprensible al ojo humano, es mas versátil, utiliza parejas de información (nombre: valor)
         
   ![image](https://user-images.githubusercontent.com/109252002/179075306-073cb477-4b1c-4a56-9ea3-43aa97c9d86a.png)

### Estandar SOAP y Estandar RESTful

El estándar SOAP es un protocolo que comparte información (webservices) con formato XML, dentro de un sobre (envelope), es un símil de una carta fisica, tienes un sobre que es el envelope SOAP que contiene la información dentro, en el caso del ejemplo contendra una carta mientras que el mensaje SOAP estara en una estructura XML.
![image](https://user-images.githubusercontent.com/109252002/179079034-d04f8cb3-90b6-44d0-ac00-42ca35784f8a.png)
puede que se requiera construir varios servicios para diferentes operaciones.

Por su parte el estándar REST que realiza operaciones en colecciones de datos (resources) de forma más sencilla que SOAP, en general toma como base una colección y se indica con un **Verbo** la operación a realizar y dependiendo esta se puede o no requerir mas data (ejemplo mensaje JSON en request para un POST) 
![image](https://user-images.githubusercontent.com/109252002/179079294-ed11bffe-d0a8-4463-a662-58bc3d664d37.png)


## Ejemplo Práctico de GET/POST



### links de ayuda o más Información

- https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/protocolo-http/
- https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/http-request/
- https://gavilanch.wordpress.com/2019/01/03/anatomia-de-una-peticion-http/
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- https://www.w3schools.com/tags/ref_httpmethods.asp
- https://desarrolloweb.com/articulos/que-es-rest-caracteristicas-sistemas.html
- 


