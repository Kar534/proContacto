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

### Soluciones de Salesforce
A.	¿Qué es Salesforce?

Salesforce es una plataforma que permite gestionar la información de los clientes de una compañia (CRM), permitiendo que en un mismo aplicativo puedan resolver muchos puntos asociados con sus clientes como ventas, reclamos, marketing, etc.

Esta compañia tiene mas de 20 años de existencia y permite la integración con varios aplicativos, se mantiene en constante cambio y mejora. 

B.	¿Qué es Sales Cloud?

Salesforce trabaja por "nubes" o modulos que permiten agrupar funcionalidades, Sales Cloud por ejemplo se encargaría de los procesos de venta, retomando los objetos principales tendriamos iteración entre un lead que se convierte en un contacto, una cuenta , una oportunidad (no siempre se generan los tres, depende de temas de negocio), en la oportunidad se concretaria el negocio, en cuentas veriamos los activos asociados o adquiridos, etc.

C.	¿Qué es Service Cloud?

por la parte de Service Cloud, esta "nube" se encarga de los temas de reclamos con el objetivo de garantizar la satisfacción de los clientes (dependiendo los requerimientos del negocio).

D.	¿Qué es Health Cloud?

Health Cloud agruparía las funcionalidades de un CRM que esta dirigido a empresas de salud como hospitales, que deben atender pacientes,generar sus citas, etc.

E.	¿Qué es Marketing Cloud?

Marketing Cloud es la nube que se encarga de lo relacionado a campañas de mercadeo, en la cual puedes configurar o crear Journeys, editar plantillas para envio de correo y muchas configuraciones mas, puede integrarse con Salesforce como tal y con Einstein lo cual hace que sea mas robusto en las predicciones o sugerencias para los prospectos.

### Funcionalidades de Salesforce

A.	¿Qué es un RecordType?

Es una configuración que permite que se utilicen diferentes procesos de negocio, listas de valores y page layout según el usuario o alguna condición. ejemplo diferentes pantallas en Account para un usuario con perfil gerencial y para uno de gestion de reclamos.

B.	¿Qué es un ReportType?

Report Type corresponde a "plantillas" que se usan para crear los reportes en salesforce, de caja se pueden encontrar muchas plantillas para reportes basicos para varias entidades, tambien es posible crear un Report Type customizado, con maximo 4 niveles y seleccionando la relaciones entre los objetos que intervienen en dichos "niveles".

C.	¿Qué es un Page Layout?

Page Layout, es el "lienzo", pantalla para vista en especifico, que determina los campos que se mostraran a un usuario.

D.	¿Qué es un Compact Layout?

Es un layout que contiene campos principales, pensado para configuraciones rapidas (por ejemplo para mobile).

E.	¿Qué es un Perfil?

Un perfil es un conjunto de permisos que se asocian a uno o varios usuarios y que puede habilitar o restringuir acceso a objetos o acciones en estos mismos (que puede ver o hacer), por ejemplo un usuario de gestion de reclamos puede que no deba tener acceso a las oportunidades de un cliente, por lo tanto su perfil no tendra marcado ninguna opción para ver información en el objeto en mención, así mismo puede que no tenga permisos para editar o eliminar un cliente, por lo tanto a nivel de account podria tener solo acceso de tipo lectura. En general se configura en un perfil que Apps, Tabs, tipos de registro, page layouts campos puede ver y los respectivos permisos CRUD de objetos tanto vainila (nativos) como customizados (creados por los usuarios).

F.	¿Qué es un Rol?

Los roles configuran el nivel de visibilidad de registros (o datos), es decir puede que con un perfil tenga acceso a Opportunity pero si mi rol no tiene acceso a ciertas oportunidad no podre visibilizar su información, en los roles podemos hablar de jerarquía de roles, en la cual si tengo un superior y esta configurada la respectiva jerarquía, el vera sus registros más los de todos los empleados a su cargo incluyéndome.

G.	¿Qué es un Validation Rule?

Validation Rules son configuraciones que validan reglas de negocio con respecto a los campos ingresados en los formularios, ejemplo si una oferta se selecciona como tipo perdida debe incluir un motivo y descripcion del mismo, de lo contrario no se podra actualizar el registro. 

H.	¿Qué diferencia hay entre una relación Master Detail y Lookup?

Entre objetos se pueden tener relaciones o asociaciones, por ejemplo una cuenta puede tener un objeto customizado de tipo referencias comerciales, al eliminar la cuenta estas referencias dependen unicamente de esa cuenta por lo tanto se eliminaran con ella y al crear un registro siempre tendra esa referencia de la cuenta a la que pertenece. Por su parte las relaciones de tipo lookup no son obligatorias por ejemplo puedo crear un caso que puede o no tener asociado una cuenta, al eliminarse la cuenta el caso se mantiene en la base de datos.

I.	¿Qué es un Sandbox?

Las Sandbox son entornos creados para desarrollo o pruebas de desarrollos o configuraciones antes de pasar a la versión productiva, contienen configuraciones similares a producción, según las licencias adquiridas se pueden crear diferente cantidad de sandboxes.

J.	¿Qué es un ChangeSet?

Son archivos o compilación de configuraciones que se pueden migrar de un ambiente a otro, ejemplo las configuraciones de un requerimiento nuevo que ha sido testado y se pasará al ambiente productivo.

K.	¿Para qué sirve el import Wizard de Salesforce?

Es una herramienta de salesforce para cargar data masiva (no mas de 50000 registros) para algunos objetos vainilla como Account, Contact, Lead, Campaign Members, Solutions y Person Accounts, tambien es posible usarla para objetos custom. desde el Setup de Salesforce se puede seleccionar el archivo y hacer un mapeo de los campos que corresponden a la información a importar.

L.	¿Para qué sirve la funcionalidad Web to Lead?

Web to Lead es una configuración OOTB que se puede habilitar para generar un formulario que se pueden insertar en una página web, de esta forma al llenarlo, la información generará el registro en los prospectos en Salesforce, esto funciona para hacer autogestión en ofertas o servicios a los que el cliente desea acceder.

M.	¿Para qué sirve la funcionalidad Web to Case?

Web to Case por su parte tambien se puede habilitar para usar un formulario en una página web, pero la información resultante se usará en la entidad de Casos, es decir sirve para autogestión de reclamos. 

N.	¿Para qué sirve la funcionalidad Omnichannel?

OmniChannel sirve para permitir a los usuarios gestionar casos o registros no solamente de su canal de atención [^7], garantizando la atención oportuna del cliente y todo lo que pueda implicar esta (satisfación/fidelización).

O.	¿Para qué sirve la funcionalidad Chatter?

Chatter es una herramienta que permite la comunicación, colaboración y compartir información entre usuarios, con el fin de mejorar la eficiencia de las ventas, atención de reclamos o adquirir conocimiento en tiempo mas corto que otros metodos como por ejemplo enviar un correo y esperar la respectiva respuesta.

### Conceptos generales
A.	¿Qué significa SaaS?

La Sigla SaaS significa Software as a Service, en el cual el proveedor de servicio se encarga de la infraestructura, ejemplo servidores, mantenimiento y el software que se utiliza [^8].

B.	¿Salesforce es Saas?

Salesforce puede considerarse como PaaS (Platform as a Service), en la cual se entregan aplicaciones prácticamente listas para usar, el consumidor se encarga de configurar sus reglas de negocio y se desentiende de configuraciones o requerimientos de infraestructura, seguridad, etc, pues son temas a cargo del proveedor de servicio [^8].

C.	¿Qué significa que una solución sea Cloud?

Significa que se encuentra en la red de internet, puedes acceder desde cualquier lugar, simplemente necesitas una conexion a internet y conectar con user/password, asi mismo puede que la información este distribuida o resguardada en diferentes servidores.

D.	¿Qué significa que una solución sea On-Premise?

Por su parte On-Premise requiere de infraestructura fisica en una locacion fija, lo cual incrementa costos de mantenimiento para una empresa, es mas complejo la conexión fuera de la red, generalmente se requiere una VPN o puente que permita acceder a la red.

E.	¿Qué es un pipeline de ventas?

Pipeline son las tareas o pasos que puede/debe hacer un agente de ventas para cerrar una oportunidad, ejemplo llamar a los prospectos, generar cita para enviar la oferta de precios, cierre de ventas (los pasos dependen de las necesidades de cada negocio).

F.	¿Qué es un funnel de ventas?

El funnel por su parte se centra en numeros, ejemplo cuantos prospectos pasaron a la etapa 2,cuantos se ganaron, etc.

G.	¿Qué significa Customer Experience?

Customer Experience es la busqueda de la satisfacción de los clientes, de esta forma se pueden evaluar procesos como la conversión de un cliente, la atención de prqs, fidelización, etc. 

H.	¿Qué significa omnicanalidad?

El termino se refiere a facilitar la comunicación desde diferentes medios, en la actualidad por ejemplo vemos que ya no solo se consiguen comunicaciones telefónicas o vía email, ya es posible interactuar por redes sociales por ejemplo.

I.	¿Qué significa que un negocio sea B2B?¿Qué significa que un negocio sea B2C?¿Qué es un KPI?

La Sigla B2B indica que la venta de productos/servicios esta orientada a comercio con empresas (Business to Business), mientras que un B2C (Business to Customer) se refiere a los que se orientan a consumidores (personas). KPI son indicadores que evaluan desempeño, por ejemplo en campañas ver el retorno de la misma.

J.	¿Qué es una API y en qué se diferencia de una Rest API?

Una API es un conjunto de procedimientos y funciones para acceder a otra aplicación, es un termino amplio que encapsula por ejemplo rest API, SOAP. Rest API es una API que usa protocolo HTTP y formato JSON [^9].

K.	¿Qué es un Proceso Batch?

Un proceso que no requiere de mayor gestión manual y permite realizar acciones sin la supervisión constante de un humano, un ejemplo es la migración de datos a una aplicación, en la cual se realizan pretareas para garantizar que la data no tendra problemas y se ejecutan procesos que enviaran por "lotes" o grupos de registros para procesar.

L.	¿Qué es Kanban?

Método de gestión de trabajo por medio de tarjetas, hace parte de las metodologías ágiles, en este método se configuran o seleccionan diferenes pasos ejemplo, analisis, diseño, desarrollo, pruebas, terminado y se hace el seguimiento de los requerimientos (cada uno en una tarjeta diferente).

M.	¿Qué es un ERP? 

ERP es un software que integra funcionalidades de negocio en un solo sistema, se diferencia de un CRM en que ERP trabaja mas procesos internos para disminuir costos mientras CRM busca aumentar ventas, manejar la relación con los clientes.

N.	¿Salesforce es un ERP?

No, Salesforce es un CRM, esta orientado a manejar la relación con los clientes.

[^1]: https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/protocolo-http/
[^2]: https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/http-request/
[^3]: https://gavilanch.wordpress.com/2019/01/03/anatomia-de-una-peticion-http/
[^4]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
[^5]: https://www.w3schools.com/tags/ref_httpmethods.asp
[^6]: https://desarrolloweb.com/articulos/que-es-rest-caracteristicas-sistemas.html
[^7]: https://www.salesforceben.com/salesforce-omni-channel/
[^8]: https://www.bmc.com/blogs/saas-vs-paas-vs-iaas-whats-the-difference-and-how-to-choose/
[^9]: https://www.freelancinggig.com/blog/2018/11/02/what-is-the-difference-between-api-and-rest-api/
[^10]: https://help.salesforce.com/s/?language=en_US
[^11]: https://trailhead.salesforce.com/es-MX
