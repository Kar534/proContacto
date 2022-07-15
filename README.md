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

Puede considerarse tanto como la maquina que contiene los archivos fuentes para desplegar una pagina o un recurso web (HTML, CSS, JS, etc) o el software que procesa las aplicaciones del lado del servidor recibiendo una petición que interpreta para encontrar los archivos correspondientes y regresando el resultado de la búsqueda junto con los datos asociados. [^1]

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

Los verbos HTTP son operaciones que pueden realizarse para un recurso HTTP de un servidor web [^2], los mas conocidos considero son :
- **GET**: utilizado para consultar un recurso y retornar la información asociada (ejemplo consultar las cuentas de tipo prospecto )
- **POST**: permite crear un recurso que pertenece a una colección de datos (ejemplo crear una cuenta en el objeto Account)
- **PATCH**: permite actualizar la información de un recurso/registro (ejemplo actualizar el estado de una cuenta)
- **DELETE**: eliminar el recurso/registro (eliminar una tarea asociada a un cliente como por ejemplo una cita o actividad)

### Request Response HTTP y Headers
Podriamos considerar que el request es la información que permite identificar que registro especifico se busca (paso 3 de la imagen de peticiones http paso a paso), mientras el response agrupa la información resultante (paso 4 de la imagen anterior), por su parte los headers son parámetros ocultos que permiten el envío/recepción de un mensaje HTTP, ejemplo Authorization, que puede permitir una conexión JWT o de otro tipo, en otras palabras los header son literales que pueden indicarle al servidor web el forma [^3]to que se espera de la información o si requiere de un valor especifico por ejemplo una llave adicional para autorizar la consulta .

### QueryString
Los queryString son parametros que se adicionan a la URL (o consulta) para refinar la información resultante, por ejemplo en un formulario web se ingresa información en varios campos, al pulsar el botón de envío direcciona a una nueva página y puede que la url tenga una configuracion como: 

       http://sitioconsultado/paginadireccionada.html?parametro1=valor1&parametroN=valorN
       donde,
       ? corresponde al caracter que indica el inicio del queryString.
       parametro1, parametroN corresponde a los elementos o variables que permitiran filtrar
       valor1, valorN corresponde a la información que ingresaste en el formulario o los valores que determinan la información resultante.

### ResponseCodes
Son códigos que permiten conocer si la petición fue realizada satisfactoriamente o se presento algún problema [^4], muchas veces se consulta una pagina web y esta demora en responder y finaliza con un codigo y mensaje de error, entre los mensajes que mas he visto y consideraría mas comunes colocaría:

- **200** : Conexión Exitosa
- **400**: Bad Request
- **401**: No Autorizado
- **500**: Error del Servidor
- **502**: Error del Gateway

## Peticiones GET vs POST
Una petición GET envían la información en la url, mientras que peticiones post (creación) requiere de adicionar información en el body del request [^5], esto puede que suene un poco mas complejo pero es sencillo, retomando el ejemplo de la página web y el formulario:
 - Si fuera un formulario de login se estaría realizando un get o una consulta del usuario, por lo cual se enviaría la información (tal vez encriptada) en un queryString en la url.
 - Por su parte si el formulario direcciona a una página de creación se realizaría un POST y necesitaría que se indicara el recurso a utilizar (ejemplo contactos) mas un mensaje con la información ingresada.

En la siguiente imagen se muestra un ejemplo de GET y POST desde Postman
![image](https://user-images.githubusercontent.com/109252002/179071679-8864c100-9d12-4ed6-8328-c98ab351339a.png)

### Verbos HTTP en el navegador
Es bueno aclarar que desde un navegador se realiza una petición get para acceder a una página. Esto lo podemos identificar desde herramientas del desarrollador al consultar una pagina.

![image](https://user-images.githubusercontent.com/109252002/179073419-34919b69-e9c4-48a6-879e-50e1b8dd9291.png)

### Estructuras de datos XML y JSON

XML es un estándar de estructura para compartir información, es de fácil entendimiento para la maquina, usando etiquetas, atributos y elementos, generalmente se utiliza en un estandar de protocolo SOAP, ejemplo:

  ![ejemplo XML](https://user-images.githubusercontent.com/109252002/179088907-36252245-cb55-4a75-b642-0fcd79671061.png)

JSON es un estándar para compartir información que es mas comprensible al ojo humano, es mas versátil, utiliza parejas de información (nombre: valor)
         
  
  ![ejemplo JSON](https://user-images.githubusercontent.com/109252002/179089194-cdfc1ecf-7f88-467b-a19f-bebbf5c8b917.png)

### Estandar SOAP y Estandar RESTful

El estándar SOAP es un protocolo que comparte información (webservices) con formato XML, dentro de un sobre (envelope), es un símil de una carta fisica, tienes un sobre que es el envelope SOAP que contiene la información dentro, en el caso del ejemplo contendra una carta mientras que el mensaje SOAP estara en una estructura XML.

![image](https://user-images.githubusercontent.com/109252002/179079034-d04f8cb3-90b6-44d0-ac00-42ca35784f8a.png)

puede que se requiera construir varios servicios para diferentes operaciones.

Por su parte el estándar REST que realiza operaciones en colecciones de datos (resources) de forma más sencilla que SOAP [^6], en general toma como base una colección y se indica con un **Verbo** la operación a realizar y dependiendo esta se puede o no requerir mas data  (ejemplo mensaje JSON en request para un POST) 

![image](https://user-images.githubusercontent.com/109252002/179079294-ed11bffe-d0a8-4463-a662-58bc3d664d37.png)


## Ejemplo Práctico de GET/POST
Para consultar un recurso desde Postman se crea un request con operación GET a la url requerida (como se menciona en el paso **Peticiones GET vs POST**)
![get json](https://user-images.githubusercontent.com/109252002/179089443-a1b633aa-0c6b-4569-a9a7-de61de8193f0.JPG)

En el caso de un POST o creación de registro individual se usa el resource con la operación POST adicionando un JSON con la información a crear.
![post json](https://user-images.githubusercontent.com/109252002/179090533-25fb1b31-b26c-4e10-8d95-19b779b1335d.JPG)
![image](https://user-images.githubusercontent.com/109252002/179090597-a571b7d3-5113-4ca6-af3a-3d2b9f6f9df2.png)

Despues de recibir la respuesta del POST se puede volver a consultar o hacer un GET y el registro debe aparecer en la respuesta.
![get json 2](https://user-images.githubusercontent.com/109252002/179090714-3753b65b-6501-44e3-8fc9-1649a7828894.JPG)

## Introducción Salesforce

## Objetos Salesforce

1.	![image](https://user-images.githubusercontent.com/109252002/179091569-5497aa4f-2c42-48eb-9edc-803f3e666360.png) Lead

Un Lead o prospecto corresponde a un posible cliente, generalmente nacen de procesos de marketing, aunque pueden aparecer como interesados en adquirir o conocer algún producto, a partir de un lead se puede obtener o generar un Contacto, una cuenta o una oportunidad en el proceso de conversión.

2.	![image](https://user-images.githubusercontent.com/109252002/179091672-4dc89dd4-99bc-4bf1-ba1f-c80967fe29db.png) Account

Una Cuenta corresponde a un cliente, competidor  o partner, en modelos B2B corresponden a la empresa con quien se tendran relaciones laborales.

3.	![image](https://user-images.githubusercontent.com/109252002/179091741-ac4ad3ba-aeaa-4d3e-9761-0bb58b0f4031.png) Contact

Los contactos son personas asociadas a las cuentas, es la identificación de iteraccion humana a quien se le ofreceran oportunidades y de quienes se obtendran reclamos.

4.	![image](https://user-images.githubusercontent.com/109252002/179091810-d2c5e8cf-6a63-4f3a-8126-4dd2c4739bd7.png) Opportunity

Las oportunidades son las posibilidades de entablar un negocio tanto con un nuevo cliente como con existentes  (ventas/negocios/ofertas).

5.	![image](https://user-images.githubusercontent.com/109252002/179091867-e80061ba-bc31-4ce1-8d1a-d8dfde65cd18.png) Product

Se refiere a los productos o servicios que maneja la compañia y ofrece a sus clientes, ejemplo planes de telefonía.

6.	![image](https://user-images.githubusercontent.com/109252002/179091971-7ceed109-e68b-42e4-834b-bec7f8ae43b2.png) PriceBook

Esta relacionado con los productos, en general se puede entender como agrupaciones de productos que se usaran en oportunidades, ejemplo listado de precios para clientes VIP.

7.	![image](https://user-images.githubusercontent.com/109252002/179092675-8c5cc546-0364-4fcf-9981-0bff9d83bf3f.png) Quote

Las ofertas son registros que pueden asociarse a una oportunidad, permitiendo generar una o varias propuestas para el cliente.

8.	![image](https://user-images.githubusercontent.com/109252002/179092855-1971beea-429b-4d0c-b459-5191e58aa60e.png) Asset

Son las referencias de productos que han sido adquiridos por un cliente, por ejemplo si la compañia ofreciera planes de telefonía como el superX y el plusW, durante el proceso de venta el cliente acepta el plan plusW, se generaría un registro que indique la línea que esta asociada a dicho plan.

9.	![image](https://user-images.githubusercontent.com/109252002/179093023-430774fe-ca15-4212-af0f-8d35fb02f135.png) Case

Los Casos son registros que trazan lo que corresponda a PRQs de los clientes, es decir tomando el ejemplo de la línea telefónica, si nuestro cliente tuviera un problema de conectividad podría solicitar que se haga una revisión de su linea, el agente que lo atienda o el formulario que complete, generaría el respectivo case que se asociará a su cuenta.

10.	![image](https://user-images.githubusercontent.com/109252002/179121751-66d9f044-00ea-4893-8b21-6a59478f7610.png) Knowledge Article

Knowledge o más especificamente los articulos de conocimiento brindan la oportunidad de crear registros de ayuda para resolución de temas frecuentes o comunes, en el ejemplo del caso se podría complementar con que el asesor consulta su "base de conocimiento" encontrando un evento similar al reportado por el cliente, le indica al cliente que realice unos pasos o sigue el mismo esos pasos para ver si puede solucionar el caso.

**Modelo Entidad Relación** 

![entidad relacion](/entidad%20relacion.jpg)

## Información Nubes Salesforce y conceptos básicos configuración

Soluciones de Salesforce
A.	¿Qué es Salesforce?
B.	¿Qué es Sales Cloud?
C.	¿Qué es Service Cloud?
D.	¿Qué es Health Cloud?
E.	¿Qué es Marketing Cloud?
Funcionalidades de Salesforce
A.	¿Qué es un RecordType?
B.	¿Qué es un ReportType?
C.	¿Qué es un Page Layout?
D.	¿Qué es un Compact Layout?
E.	¿Qué es un Perfil?
F.	¿Qué es un Rol?
G.	¿Qué es un Validation Rule?
H.	¿Qué diferencia hay entre una relación Master Detail y Lookup?
I.	¿Qué es un Sandbox?
J.	¿Qué es un ChangeSet?
K.	¿Para qué sirve el import Wizard de Salesforce?
L.	¿Para qué sirve la funcionalidad Web to Lead?
M.	¿Para qué sirve la funcionalidad Web to Case?
N.	¿Para qué sirve la funcionalidad Omnichannel?
O.	¿Para qué sirve la funcionalidad Chatter?
Conceptos generales
A.	¿Qué significa SaaS?
B.	¿Salesforce es Saas?
C.	¿Qué significa que una solución sea Cloud?
D.	¿Qué significa que una solución sea On-Premise?
E.	¿Qué es un pipeline de ventas?
F.	¿Qué es un funnel de ventas?
G.	¿Qué significa Customer Experience?
H.	¿Qué significa omnicanalidad?
I.	¿Qué significa que un negocio sea B2B?¿Qué significa que un negocio sea B2C?¿Qué es un KPI?
J.	¿Qué es una API y en qué se diferencia de una Rest API?
K.	¿Qué es un Proceso Batch?
L.	¿Qué es Kanban?
M.	¿Qué es un ERP? 
N.	¿Salesforce es un ERP?




[^1]: https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/protocolo-http/
[^2]: https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/http-request/
[^3]: https://gavilanch.wordpress.com/2019/01/03/anatomia-de-una-peticion-http/
[^4]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
[^5]: https://www.w3schools.com/tags/ref_httpmethods.asp
[^6]: https://desarrolloweb.com/articulos/que-es-rest-caracteristicas-sistemas.html



