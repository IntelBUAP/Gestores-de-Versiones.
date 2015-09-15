Distributed Concurrent Version System
=====================================


+ Introdución
+ Historia
+ Características
+ Comandos y descripción
+ Instalación y setup de clientes

![Imagen][DCVS]
[DCVS]: pictures/svg.png  "Visualization of the "history tree" of a revision controlled project, showing branching, merging, tagging, etc."

## Introduccion
---------------

>El desarrollo de grandes proyectos requiere de sistemas de control de código fuente, que ayuden a los grupos de programadores para manejar los cambios a su código. Existen sistemas que tiene como característica que el repositorio es centralizado y está disponible ya sea, en un sistema de archivos local o en uno remoto tal como un NFS. Sin embargo, hay muchos proyectos en los que los programadores son una parte de una ***SCoNe (Seldomly Connected Network)***. Para tales proyectos un sistema de control distribuido de código fuente es preferible. Un ejemplo donde un sistema distribuido es de utilidad ocurre cuando un grupo de programadores se encuentran trabajando desde equipos conectados a a través de una ***red UUCP***. Otro ejemplo donde el sistema distribuido es de utilidad es cuando uno o más programadores está trabajando bajo la protección de un _firewall_.

>*__Distributed Concurrent Version System (DCVS)__* implementa un sistema de control de código fuente distribuido basado en un sistema centralizado llamado *__CVS__*. En general DCVS permite a los grupos de desarrolladores de software trabajar en conjunto sobre un proyecto de software usando un repositorio de código fuente replicado.

>Las bases de un DCVS son:

> 1.  Cada desarrollador almacena localmente una copia del repositorio.
> 2.  Desde el repositorio local una copia de trabajo del código fuente es verificada.
> 3.  Diversos proyectos que están bajo el control de un DCVS son mantenidos usando listas de distribución en los archivos drip del usuario. (Drip significa distributed replicated information pile).
> 4.  Los cambios son aplicados a la copia de trabajo del código fuente local de un desarrollador.
> 5.  Cuando los cambios están listos para ser entregados de vuelta dentro del repositorio local, un token debe ser obtenido para cada archivo localmente modificado.
> 6.  Una vez que cada token se obtiene, los desarrolladores continúan el proceso de entrega en la forma normal de un CVS.
> 7.  Después del committing exitoso, una copia del archivo repositorio local es replicada en cada uno de las máquinas en la lista de distribución.

## Historia
-----------


>Durante mucho tiempo la gestión o control de versiones se llevó a cabo de manera centralizada con todos sus defectos y ventajas, llegado el  momento este esquema no pudo soportar los sistemas modernos lo cual condujo  a la creación de Distributed Control Version Systems. 
>En un modelo distribuido cada desarrollador tiene su propio repositorio, trabaja en forma local, modifica y crea archivos o directorios sin conocimiento de los demás, es solo hasta que se realiza una operación  del tipo push, que se envían los cambios a otro repositorio.

>Bajo este escenario cada nodo es completamente independiente y compartir  es opcional.

>###Sobre el esquema de trabajo


> **Los conceptos clave de este esquema son:**

> - Los esquemas centralizados se enfocan en sincronizar, seguir y  respaldar archivos, los distribuidos se enfocan en compartir cambios,  cada cambio tiene un identificador único.
> - Escribir/Grabar o descargar y aplicar son operaciones separadas, en un esquema centralizado todo esto ocurre al mismo tiempo.
> - Existen dos términos importante:
> - Push: acción de mandar cambios a algún otro repositorio.
> - Pull: obtener cambios de otro repositorio.


> **Las principales ventajas son:**

> - Es rápido, los diffs, que son comparaciones que se realizan entre la versión actual del proyecto y las anteriores, los commits y los reverts, que son almacenar de forma segura los cambios y revertir  alguna modificación respectivamente, todo ello ocurre de forma local.
> - Se trabaja offline.
> - Se adapta bien a los cambios.
> - Realizar un desarrollo local (branch) y enviarlo para integrarse  al repositorio principal (merge) son operaciones que se realizan  fácilmente.
> -  Requiere poco mantenimiento.

>### Dos exponentes importantes son git y Mercurial

>Mercurical es rápido y simple. Se le conoce con el nickname de hg,  símbolo de la tabla periódica del mercurio.

>Los desarrolladores de Linux necesitaban un nuevo sistema de control  de versiones así que acudieron al gurú de Linux, Torvalds, en busca  de una solución.
>Git fue creado como una herramienta que pudiera adaptarse al cambio  y al desarrollo colaborativo. 
>Este esquema fue concebido para ser completamente distribuido, los  programadores se hallan en cualquier parte y pueden trabajar desde  diferentes compañías o desde su casa y todos contribuyen al mismo proyecto.

##Caracteristicas
-----------------

>DCVS es una version extendida de **CVS** \(Concurrent Version System\) y el programa CVSup, adecuado para el manejo de repositorios de CVS con acceso a escritura local a traves de WANś.

>En un sistema  DCVS hay n repositorios donde sus contenidos se mantienen igual o casi igual por procesos en segundo plano. El programa encargado para esta tarea es una versión extendida de **CVSup**.

>Todos los contenidos de todas las lineas de desarrollo pueden ser desplegados de cualquiera de los n servidores dentro de **workspace** propio de un desarrollador.

>Todas las operaciones que no modifican el repositorio, como **diff**, **patch**, **log**, **annotate**, etc. trabajaran justo como lo hacian en CVS pero siempre usando el repositorio local por lo cual se realizará de una manera mucho mas rápida.

>Pero que pasa cuando el código dentro del **workspace** debe cambiar?, si todos los servidores DVCS desean confirmar sus cambios al mismo tiempo posiblemente ocurran varios conflictos. Así que a cada servidor DCVS se le asigna un conjunto de lineas de trabajo \(branches\) de las que es responsable. Las modificaciones a una cierta linea de trabajo solo pueden ser revisadas desde el servidor que se encarga de dicha rama. La separación de modificaciones por líneas de desarrollo hace que sea posible transferir y distribuir automáticamente cambios en la red DCVS. 

>Si algun desarrollador quiere realizar cambios para una linea de desarrollo de la cual no es responsable, entonces deberá crear un nuevo **branch** y subir los cambios ahí. Si los cambios que realizó deben ser agregados al **branch** principal, entonces el desarrollador del servidor DVCS responsable debe realizar una operación **merge.

>Dado que DCVS se apoya de CVSup el cual utiliza codificación delta para manejar los cambios y la sincronización de los archivos ¿Cómo puede asegurarse que los **deltas** en cierto **branch** puede ser identificado como perteneciente de cierto servidor DVCS?. Para eso utiliza algo llamado **magic branch numbers**, los cuales son numeros de revision con un cierto numero de elementos y el numero 0 en la penúltima posición. Por ejemplo tomemos 1.34.0.4. Los **deltas** pertenecientes a este **branch** serán etiquetados 1.34.4.2, 1.34.4.2, 1.34.4.3, etc. Para separar **branches** en diferentes servidores, debemos asegurar que los **"branch numbers"** \(en nuestro ejemplo 4\) elegidos para representar el **branch** son diferentes para cada servidor.

>Para lograr esto, DCVS asigna un unico rango de **branch numbers** a cada par de servidores. Todos los rangos para todos los servidores deben ser mutuamente excluyentes. cada servidor DCVS puede decidir si es o no responsable para cierto **branch** o **delta** o un archivo dado. si es así, todas las operaciones de modificacion son permitidas; sino las operaciones de modificación son posibles unicamente sobre el servidor remoto apropiado.

<<<<<<< HEAD
>Otro problema que se presenta cuando se trabaja con repositorios DCVS distribuidos son los  
nombres de las configuraciones \(tags\). Estos deben ser únicamente asignables exactamente  
a un servidor DCVS. DCVS resuelve este problema de una forma muy simple, expandiendo los  
tags con un prefijo especifico del servidor como: **_at_**dcvs**_mydomain_**org, así no  
ocurren conflictos en el espacio de nombre del tag.
=======
>Otro problema que se presenta cuando se trabaja con repositorios DCVS distribuidos son los nombres de las configuraciones \(tags\). Estos deben ser únicamente asignables exactamente a un servidor DCVS. DCVS resuelve este problema de una forma muy simple, expandiendo los tags con un prefijo especifico del servidor como: **_at_**dcvs**_mydomain_**org, así no ocurren conflictos en el espacio de nombre del tag.
>>>>>>> b00d1d9cdffc14c3dacbd7e3d48099ec56cbb05e


##Instalación desde código fuente
----------------------------------

Crear un directorio local, por ejemplo ~/word/dcvs:
> **mkdir ~/work/dcvs**

Acceda al directorio:
> **cd ~/work/dcvs**

Obtenga las fuentes con CVS o CVSup como se describe en:
>https://dcvs.elegosoft.com/dcvs-download-en.php

Alternativamente, desempaquete el código fuente, por ejemplo:

>**tar xzf dcvs-src-0.1.2.tar.gz**

Si no ha creado el usuario y grupo dcvs, en este momento es conveniente crearlo

Entre al directorio producción

>**cd prod**

Puede usar make de GNU o BSD para construir e instalar todos lo programas:

>**make all**

>**make install**

Puede revisar los ajustes con:

>**make info**

Si tiene problemas de paquetes viejos, puede actualizar con:

>**make tcp install-tcp**

>**make parseparams install-parseparams**


Probablemente necesitara permisos de root para la instalacion.

##Comandos
----------

>**dcvs checkout** módulos...

>Crea su copia privada de las fuentes de los  módulos. Puede trabajar con esta copia sin interferir con otros trabajos.

>**dcvs update**

>Ejecute este comando desde su directorio privado cuando deseé actualizar sus copias con los cambios que otros desarrolladores han realizado en el repositorio fuente.

>**dcvs add** file...

>Este comando agregará nuevos archivos de su directorio de trabajo al grabado de **dcvs**. Los archivos serán agregados al repositorio la próxima vez que ejecute  **'dcvs commit'**.

>**dcvs remove** file...

>Este comando declara que usted quiere eliminar archivos de el repositorio. Los archivos eliminado no afectan a otros hasta que ejecute el comando **'dcvs commit'**.

>**dcvs commit** file...

>Use este comando cuando deseé publicar sus cambios a otros desarrolladores, mediante la incorporación en el repositorio fuente.

###Nuevos comandos en DCVS

>**catcset**

>Muestra uno o mas archivos *changeset*, que fueron previamente creados con **mkcset**.

>**catsnap**

>Muestra uno o mas archivos *snapshot*, que fueron previamente creados con **mksnap**.

>**lscset**

>Lista los *changesets* existentes, que fueron previamente creados con **mkcset**.

>**lssnap**

>Lista los *snapshots*, que fueron previamente creados con **mksnap**


>**mkcset**

>Crea un nuevo *changeset*, basado en dos revisiones, *snapshots* o revisiones.

>**mksnap**

>crea un nuevo *snapshot*, basado en una reivison, fecha o la copia de trabajo.

###Comandos CVS en DCVS

>**add**

>Agrega un nuevo archivo o directorio al repositorio.

>**admin**

>Ejecuta funciones de control en el repositorio fuente.

>**checkout**

>Crea un directorio de trabajo de archivos fuente para la edición.

>**commit**

>Aplica cambios, adiciona y elimina en el repositorio fuente, desde su directorio de trabajo.

>**diff**

>Muestra diferencias entre los archivos de trabajo y el repositorio fuente, o entre dos revisiones en el repositorio.

>**export**

>Prepara copias de un conjunto de archivos fuente para enviar fuera del sitio.

>**history**

>Muestra reportes de comandos **dcvs** que usted u otros ejecutaron en un archivo particular o directorio en el repositorio fuente.

>**import**

>Incorpora un conjunto de actualizaciones desde fuera del sitio dentro de el repositorio fuente.

>**init**

>Inicializa un repositorio añadiendo el subdirectorio DCVSROOT y algunos archivos de control. Deberá usar este comando o inicializar el repositorio de alguna otra manera antes de ser usado.

>**log**

>Muestra el registro de información.

>**rdiff**

>Prepara una colección de *diffs* como un archivo parche entre dos liberaciones en el repositorio.

>**release**

>Cancela un *dcvs checkout* abandonando cualquier cambio.

>**remove**

>Elimina archivos de el repositorio fuente, algunos archivos en espera de *dcvs commit*.

>**rtag**

>Explicitamente especifica una etiqueta simbólica para una particular revisión de los archivos en el repositorio fuente.


>**status**

>Muestra el actual estado de los archivos: ultima versión, versión en el directorio de trabajo, si la versión de trabajo ha sido editada y opcionalmente etiqueta simbólica en el archivo RCS.

>**tag**

>Especifica una etiqueta simbólica para el repositorio. Por default etiqueta las ultimas revisiones que fueron sincronizadas con su directorio de trabajo.


>**update**

>Actualiza su directorio de trabajo con los últimos cambios del repositorio. Merges son realizados automáticamente cuando es posible.

  
------------
  
  
     
|Integrantes de Stallman| Correo |
:-----------------------|-------:|
|Hijuitl Cuatlayo Jose Patricio | patriciohc.0@gmail.com |
|Jimenez Coronado Roberto | correo |
|Jiménez Pacheco Daniel| correo |
|Lira Huerta Ernesto| correo |
|Ortega Rojas Luis Enrique | ortegarle@gmail.com |
