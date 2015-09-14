
Control de Versiones Subversion
===============================

Introducción
------------

El control de versiones es el arte del manejo de los cambios en la información.

Ha sido durante mucho tiempo una herramienta crítica para los programadores, 
quienes normalmente empleaban su tiempo haciendo pequeños cambios en el software
y después des- haciendo esos cambios al día siguiente. 

Pero la utilidad del software de control de versiones se extiende más allá de 
los límites del mundo del desarrollo de software. Allá donde pueda encontrarse 
a gente usando ordenadores para manejar información que cambia a menudo, hay un hueco para el control de versiones. 

Y aquí es donde entra en juego Subversion.


##Historia

A principios de 2000, *CollabNet, Inc*. (http://www.collab.net) comenzó a 
buscar a los desarrolladores para escribir un sustituto para **CVS**.

CollabNet ofrece una suite de software de colaboración denominado CollabNet 
Enterprise Edition (CEE), de los cuales uno de los componentes era el control 
de versiones. Aunque CEE utiliza CVS como su sistema de control de versiones 
inicial, las limitaciones de CVS eran evidentes desde el principio, y CollabNet
 sabía que tendría que encontrar algo mejor. 

Desafortunadamente, CVS se había convertido en el estándar de facto en el mundo
 del código abierto en gran medida porque no había nada mejor, al menos no bajo
 una licencia libre. Así CollabNet decidió escribir un nuevo sistema de control
 de versiones desde cero, manteniendo las ideas básicas de CVS, pero sin sus 
fallos y defectos.

En febrero de 2000 Karl Fogel y Jim Blandy aceptaron trabajar en el proyecto, 
decidiendo llamarlo **Subversion**

## Características ##

Subversión proporciona:





- **Versionado de directorios**

Subversion implementa un sistema de ficheros versionado “virtual ” que sigue 

los cambios sobre árboles de directorios completos a través del tiempo. Ambos, ficheros y directorios, se encuentran bajo el control de versiones.







- **Verdadero historial de versiones**

Con Subversion, usted puede añadir, borrar, copiar, y renombrar ficheros y directorios. Y cada fichero nuevo añadido comienza con un historial nuevo, 

limpio y completamente suyo.



- **Envíos atómicos**

Una colección cualquiera de modificaciones o bien entra por completo al 

repositorio, o bien no lo hace en absoluto. Ésto permite a los desarrolladores construir y enviar los cambios como fragmentos lógicos e impide que ocurran 

problemas cuando sólo una parte de los cambios enviados lo hace con éxito.



- **Versionado de metadatos**

Cada fichero y directorio tiene un conjunto de propiedades; claves y sus 

valores asociado a él. Usted puede crear y almacenar cualquier par arbitrario 

de clave/valor que desee. Las propiedades son versionadas a través del tiempo, 

al igual que el contenido de los ficheros.



- **Elección de las capas de red**

Subversión tiene una noción abstracta del acceso al repositorio, facilitando a 

las personas implementar nuevos mecanismos de red. Subversion puede conectarse 

al servidor HTTP Apache como un módulo de extensión. Ésto proporciona a 

Subversión una gran ventaja en estabilidad e interoperabilidad, y acceso 

instantáneo a las características existentes que ofrece este 

servidor—autenticación, autorización, compresión de la conexión, etcétera. 

También tiene disponible un servidor de Subversión independiente, y más ligero. 

Este servidor habla un protocolo propio, el cual puede ser encaminado fácilmente 

a través de un túnel SSH.



- **Manipulación consistente de datos**

Subversión expresa las diferencias del fichero usando un algoritmo de 

diferenciación binario, que funciona idénticamente con ficheros de texto 

(legibles para humanos) y ficheros binarios (ilegibles para humanos). Ambos 

tipos de ficheros son almacenados igualmente comprimidos en el repositorio, 

y las diferencias son transmitidas en ambas direcciones a través de la red.



- **Ramificación y etiquetado eficientes**

El coste de ramificación y etiquetado no necesita ser proporcional al tamaño del proyecto. Subversión crea ramas y etiquetas simplemente copiando el proyecto, 

usando un mecanismo similar al enlace duro. De este modo estas operaciones toman solamente una cantidad de tiempo pequeña y constante.



- **Hackability**

Subversión no tiene un equipaje histórico; está implementado como una colección de bibliotecas compartidas en C con APIs bien definidas. Ésto hace a Subversión extremadamente fácil de mantener y reutilizable por otras aplicaciones y lenguajes.



- **Arquitectura de Subversión**

![](http://image.slidesharecdn.com/presentacion-nuestra-1234631356296993-3/95/control-de-versiones-con-subversion-9-728.jpg?cb=1234609891)
> ### Andy Daniel Cruz Ramos
>### Mónica Conde Domínguez
>### Luisa Cerón Perea
