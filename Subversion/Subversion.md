
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

> ### Andy Daniel Cruz Ramos


**Comandos y su descripción.**

A continución alistaremos los comandos básicos para el uso de Subversion, así como su descripción y su sintaxis.

1. **Ayuda.**
Este comando nos sirve para ver la ayuda necesaria para el uso de un comando y su sintaxis es la siguiente:
$ svn help subcomando

	Donde Subcomando es el comando para el cual requerimos ayuda.

2. **Subir los cambios**
El siguiente comando es CI el cual utilizaremos para compartir los cambios con los demás desarrolladores, su sintaxis es:
$ svn ci

3. **Agregar un archivo.**
Para agregar un archivo o una carpeta y todo su contenido al control de versiones se usa el subcomando add, su sintaxis es la siguiente:
$ svn add archivo.src carpeta/

4. **Borrar un archivo.**
De la misma manera en que se agrega un archivo para borrar es algo similar, su sintaxis es la siguiente:
$ svn delete archivo.src carpeta/

5. **El comando update.**
Nos sirve para asegurar que despues de dejar de trabajar con un repositorio y retomarlo tiempo despues, sea la ultima copia del repositorio, su sintaxis es
$ svn update

6. **Cambios.**
Para observar el historial de cambios y saber que usuario modificó el archivo podemos utilizar el siguiente comando:
$ svn log

7. **Diferencias entre versiones.**
Si queremos encontrar los cambios que se han realizado en un archivo en particular entre la versión actual y la anterior podemos usar el comando diff, su sintaxis es la siguiente:
$svn diff nombre_archivo

8. **Exportar.**
Si se desea trabajar con unn archivo fuera del ambiente subversion, se pueden exportar con el siguiente comando:
$ svn export carpeta_origen carpeta_destino

9. **Etiquetar versión.**
Si se desea hacer el etiquetado de una nueva versión y estabilizar los cambios de la rama trunk podemos utilizar el siguiente comando:
$ svn copy nombre del repo/trunk -r #revisión nombre del repo/tags/nombre de la etiqueta -m "comentario".

10. **Excluir archivos.**
Si se desea excluir archivos generados manualmente y no se quieren subir al repositorio podemos agregarlos a la lista de exclusión con el siguiente comando:
$ svn propedit svn:ignore