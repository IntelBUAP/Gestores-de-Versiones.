
#### Gestor de Versiones: CVS (Concurrent Version System).


##### *** - Introducción.***

***
```
- En este marco teórico, se describe el concepto de Gestor de Versión CVS. Dado el problema entre los desarrolladores del intercambio de ficheros de código fuente, surge la necesidad de evitar este tipo de conflicto mediante la herramienta mencionada, esto, descrito en la investigación recabada en este documento.

Así mismo, se hace mención de su historia, principales características, uso y manejo del mismo con su respectiva descripción.

Los gestores de versiones, también llamados Herramientas de Gestión de Configuraciones de Software ó Repositorios, son herramientas que permiten a desarrolladores de Proyectos centralizar y coordinar sus trabajos. Manteniendo los registros y cambios de distintos ficheros de un Proyecto; principalmente cógido fuente. Permitiendo la colaboración de distintos desarrolladores e incluyendo la evolución en líneas paralelas de un mismo Proyecto.

Conociendo más características de la misma, hará de nuestro ejercicio y desarrollo una interacción concurrente e independiente.
```
***
##### - Ventajas.
***
```
	- Aplicación Cliente-Servidor.
	- Usado para archivos de código fuente y otros tipos de archivos.
	- Empleado para administrar versiones y cambios sobre archivos.
	- Difundido bajo licencia de GLP.
	- Permite la concurrencia de trabajo.
	- Integración de versiones.
	- Manejo de múltiples versiones simultáneas.

```
***

##### - Otros sistemas.
***
```
	- Microsoft Source Safe.
	- Clear Case.
	- Visual Studio Team System Source Control.
	- YACC.
	- DARCS.
	- Apache Subversion (SVN).
	- Git.
	- Mercurial.

```
***





`aoapedro@hotmail.com`

***

Historia de CVS
-------------------------------
**CVS** comenzo a desarrollarse por
[***Dick Grune***](http://www.dickgrune.com/ "Dick Grune")
a mediados de los *80's* a partir de un sistema
de control de versiones anterior llamado
*"sistema de control de revisiones"* (RCS), que gestiona
archivos individuales, pero no proyectos integrales.

![Dick Grune](http://www.dickgrune.com/pictures/dick.jpg "Dick Grune")

Dick Grune creo lo que se conoce como la *"version antigua"*
de CVS para poder cooperar con sus estudiantes
(*Erik Baalbergen y Maarten Waage*)
en el ACK (*Ámsterdam Compiler Kit* compilador de C).
Ya que los tres tenian diferentes horarios
y solo podian programar en sus ratos libres.
Inicialmente lo llamaron
**cmt** (*commit versions independently*),
porque les permitió combinar versiones independientes de codigo
en un mismo proyecto.

Grune lanzó públicamente el código (*un conjunto de scripts*)
en Usenet para mod.sources el **23 de junio 1986**.
Y por fin un sistema de control de versiones permitió
a los desarrolladores trabajar simultaneamente
de forma mas o menos independiente,
pasando cada uno a trabajar sobre una copia del proyecto total
que se iba sincronizando con el proyecto general.

Unos años mas tarde, en **1989**,
***Brian Berliner***
tomo los scripts de Grune  y los reescribió en C,
creando lo que sería la *"versión moderna"* de CVS,
ya con una clara arquitectura cliente-servidor,
tiempo despues se le unieron ***Jeff Polk***
y muchos otros colaboradores,
lo liberaron para beneficio de la comunidad bajo la **GPL**.

El **19 de noviembre de 1990**, CVS versión **1.0**
fue presentado a la
**Free Software Foundation**
para su desarrollo y distribución.
Así pasó a ser el sistema de control de versiones más usado del mundo.

Desde entonces se han sucedido diversos cambios
realizados por varias empresas,
especialmente **Cygnus Support** y **Cyclic Software**.
En la actualidad, casi todos los cambios recientes en **CVS**
son obra de Cyclic. Y tras eliminar alguna dependencias
CVS paso a ser parte oficial del proyecto **GNU**,
además es usado por la mayoría de los grandes proyectos de
software libre del mundo
(*gcc, emacs, guile, gtk, gimp, gnome, linux, etc.*).

***

##Descripción de los comandos de _CVS_

El formato general de todos los comandos de _CVS_ es:

	cvs [ cvs_options ] cvs_command [ command_options ] [ command_args ]

Donde:

	cvs

Es el nombre del programa _CVS_.

	cvs_options

Algunas opciones que afectan a todos los sub-comandos de _CVS_.

	cvs_command

Uno de varios sub-comandos diferentes. Algunos de los comandos tienen alias que se pueden utilizar en su lugar; los alias se indican en el manual de referencia para ese comando. Sólo hay dos situaciones en las que es posible omitir _'cvs_command'_: _'-H cvs'_ provoca una lista de comandos disponibles, y _'-v cvs'_ muestra información de la versión de _CVS_.

	command_options

Opciones que son específicas del comando.

	command_args

Argumentos a los comandos.


###Opciones globales

Las _'cvs_options'_ disponibles son:

	--allow-root=rootdir

Especifica el directorio _CVSROOT_ legal.

	-a

Autentifica todas las comunicaciones entre el cliente y el servidor. Solo tiene efecto en el cliente _CVS_.

	- T tempdir

Use _tempdir_ como el directorio donde los archivos temporales son colocados. Anula la configuración de la variable de entorno _$ TMPDIR_ y cualquier directorio precompilado. Este parámetro debe especificarse como una ruta absoluta.

	-d cvs_root_directory

Utilice _cvs_root_directory_ como la ruta de acceso al directorio raíz del repositorio. Anula la configuración de la variable de entorno _$ CVSROOT_.

	-e editor

Utilice editor para introducir la información de registro de revisiones. Anula el ajuste de las variables de entorno _$ CVSEDITOR_ y _$ EDITOR_.

	 -H
	--help

Muestra informacion del uso del comando _'cvs_command'_ especificado.

	-r
Haga nuevos archivos de trabajo de sólo lectura. Mismo efecto que si se establece la variable de entorno _$CVSREAD_.

	-s variable=value

Establece una variable de usuario.

	-t

Traza la ejecución del programa; muestra mensajes en la pantalla de los pasos de la actividad _CVS_.

	 -v
	--version

Muestra la version y la información del copyright para _CVS_.

	-w

Crea nuevos archivos de trabajo de lectura y escritura. Anula la configuración de la variable de entorno _$ CVSREAD_.

####Añadir archivos y directorios en el repositorio

	add [-k rcs-kflag] [-m message] files...

El comando _add_ se utiliza para presentar los nuevos archivos y directorios para la adición al repositorio _CVS_. Cuando se utiliza _add_ en un directorio, un nuevo directorio se crea en el repositorio inmediatamente. Cuando se utiliza en un archivo, sólo el directorio de trabajo se actualiza. Los cambios en el repositorio no se hacen hasta que el comando _commit_ se utiliza en el archivo que se acaba de agregar.
El comando _add_ también resucita a los archivos que se han eliminado previamente. Esto se puede hacer antes o después de que el comando _commit_ se utilice para finalizar la eliminación de archivos. Los archivos resucitados se restauran en el directorio de trabajo en el momento en que se ejecute el comando _add_.

#####Opciones del comando _add_

	-k kflag

Procesa palabras clave de acuerdo con _kflag_.

	-m message

Utiliza _message_ como el mensaje de registro, en lugar de invocar un editor.

####_annotate_ - ¿Qué revisión modificó cada línea de un archivo?

	annotate [options] files…

Para cada archivo en _files_, imprime la revisión principal del tronco, junto con información sobre la última modificación para cada línea.

#####Opciones del comando _annotate_

	-l

Directorio local solamente, sin recursividad.

	-R

Directorios de proceso de forma recursiva.

	-f

Utilice revisión de cabecera si no se encuentra la etiqueta / fecha.

	-F

Comentar archivos binarios.

	-r revision

Comentar archivo como de la revisión / etiqueta específicada.

	-D date

Comentar archivo como de la fecha específicada.

#####Ejemplo del comando _annotate_

	$ cvs annotate ssfile
	Annotations for ssfile
	***************
	1.1          (mary     27-Mar-96): ssfile line 1
	1.2          (joe      28-Mar-96): ssfile line 2

El archivo _'ssfile'_ contiene actualmente dos líneas. La línea _ssfile line 1_ se registró por mary el 27 de marzo. Luego, el 28 de marzo, joe añadió la línea _ssfile line 2_, sin modificar la línea _ssfile line 1_. Este informe no dice nada acerca de las líneas que han sido borradas o reemplazadas; es necesario utilizar _cvs diff_ para eso.

####_checkout_ - Mirar las fuentes para la edición

	checkout [options] modules…

Crea o actualiza un directorio de trabajo que contiene copias de los archivos de fuente especificados por _modules_. Debe ejecutar _checkout_ antes de usar la mayoría de los otros comandos de _CVS_, ya que la mayoría de ellos operan en su directorio de trabajo.

Los módulos son o bien los nombres simbólicos para alguna colección de directorios fuente y archivos, o rutas de acceso a directorios o archivos en el repositorio. Los nombres simbólicos se definen en el archivo _'modules'_.

En función de los módulos especificados, _checkout_ puede crear directorios de forma recursiva y poblarlos con los archivos de fuente correspondientes. Puede entonces editar estos archivos fuente en cualquier momento (independientemente de que otros desarrolladores de software están editando sus propias copias de las fuentes); actualizarlos para incluir nuevos cambios aplicados por otros al repositorio de código fuente; o hacer un _commit_ de su trabajo como un cambio permanente en el repositorio de código fuente.

Tenga en cuenta que _checkout_ se utiliza para crear directorios. El directorio de nivel superior creado siempre se añade al directorio donde se invoca _checkout_, y por lo general tiene el mismo nombre que el módulo especificado. En el caso de un alias del módulo, el sub-directorio creado puede tener un nombre diferente, pero usted puede estar seguro de que será un subdirectorio, y que _checkout_ mostrará la ruta relativa que lleva a cada archivo extraído dentro de su área privada de trabajo (a menos que especifique la opción global _"-Q"_).

#####Opciones del comando _checkout_

	-D date

Utiliza la revisión más reciente a más tardar en la fecha. Esta opción es _sticky_, e implica _'-P'_.

	-f

Sólo útil con las banderas _'-D date'_ o _'-r tag'_. Si no se encuentra la revisión correspondiente, recupera la revisión más reciente (en lugar de ignorar el archivo).

	-k kflag

Procesa las palabras clave de acuerdo con _kflag_. Esta opción es _sticky_; las futuras actualizaciones de este archivo en el directorio de trabajo utilizarán la misma _kflag_.

	-l

Local; ejecutar sólo en el directorio de trabajo actual.

	-n

No ejecutar cualquier programa _checkout_ (como se especifica con la opción _'-o'_ en el archivo de los módulos).

	-P

Recortar directorios vacíos.

	-p

Archivos de tubería a la salida estándar.

	-R

Directorios _checkout_ de forma recursiva. Esta opción está activada de forma predeterminada.

	-r tag

Utiliza la etiqueta de revisión. Esta opción es _sticky_, e implica _'-P'_	.

**Además de esas, puede utilizar estas opciones de comandos especiales con _checkout_:**

	-A

Restablece cualquier etiqueta _sticky_, fechas u opciones _'-k'_. No restablece opciones _sticky_ _'-k'_  en los archivos modificados.

	-c

Copia el archivo de módulo, ordenado, a la salida estándar, en lugar de crear o modificar los archivos o directorios en el directorio de trabajo.

	-d dir

Crea un directorio llamado _dir_ para los archivos de trabajo, en lugar de utilizar el nombre del módulo. En general, el uso de esta bandera es equivalente a usar _'mkdir dir; cd dir'_ seguido por el comando _checkout_ sin la etiqueta _' -d '_.

#####Ejemplo del comando _checkout_
Obtiene una copia del módulo _'tc'_:

	$ cvs checkout tc

Obtiene una copia del módulo _'tc'_ como se veía hace un día:

	$ cvs checkout -D yesterday tc


####_commit_ - Revise los archivos en el repositorio

	commit [-lRf] [-m ’log_message’ | -F file] [-r revision] [files…]

Utilice _commit_ cuando se quiera incorporar los cambios de los archivos fuente de trabajo en el repositorio de origen.

Si no se especifican archivos particulares en _commit_, todos los archivos en el directorio actual de trabajo se examinan. _commit_ es cuidadoso al cambiar en el repositorio sólo aquellos archivos que que realmente han cambiado. Por defecto (o si se especifica explícitamente la opción _'-R'_), se examinan también los archivos de los subdirectorios y se hace _commit_ si han cambiado; puede utilizar la opción _'-l'_ para limitar el _commit_ a sólo el directorio actual.

_commit_ verifica que los archivos seleccionados están al día con las revisiones actuales en el repositorio de origen; se notifica y se sale sin hacer el _commit_, si alguno de los archivos especificados debe actializarse. _commit_ no llama al comando de actualización, sino que deja que se pueda hacer cuando sea el momento adecuado.

Cuando todo está bien, un editor se invoca para permitirle introducir un mensaje de registro que se escribirá a uno o más programas de registro y se coloca en el archivo RCS en el repositorio. Este mensaje de registro se puede recuperar con el comando log. Se puede especificar el mensaje de registro en la línea de comandos con la opción _'-m message'_, y así evitar la invocación editor, o utilizar la opción _"-F file'_ para especificar que el argumento del archivo contiene el mensaje de registro.

#####Opciones del comando _commit_

	-l

Local; ejecuta sólo en el directorio de trabajo actual.

	-R

Directorios _commit_  de forma recursiva. Esto está activada por defecto.

	-r revision

_commit_ a revisión. _revision_ debe ser o bien una rama, o una revisión en el tronco principal que es mayor que cualquier número de revisión existente. No se puede hacer _commit_ a una revisión específica en una rama.

_commit_ también es compatible con las siguientes opciones:

	-F file

Lee el mensaje de registro del archivo, en lugar de invocar un editor.

	-f

Tenga en cuenta que este no es el comportamiento estándar de la opción _'-f'_ como se define en las opciones de comandos comunes.

Fuerza a CVS a hacer _commit_ de una nueva revisión, incluso si no se ha realizado ningún cambio en el archivo. Si la revisión actual del archivo es 1.7, los siguientes dos comandos son equivalentes:

	$ cvs commit -f file
	$ cvs commit -r 1.8 file

La opción _'-f'_ deshabilita la recursividad (es decir, implica _'-l'_). Para forzar a CVS para hacer _commit_ de una nueva revisión de todos los archivos en todos los subdirectorios, debe utilizar _'-f -R'_.

	-m message

Utiliza _message_ como el mensaje de registro, en lugar de invocar un editor.

***

#####diff—Muestra las diferencias entre revisiones#####

*Sintaxis*: diff [-lR] [-k kflag] [format_options] [[-r rev1 | -D date1] [-r rev2 | -D date2]] [files…]
*Requerimientos*: directorio de trabajo, repositorio.
*Cambios*: ninguno.

El comando **diff** es usado para comparar diferentes revisiones de archivos. La acción predeterminada es comparar sus archivos de trabajo con las revisiones que se basaron en el, y reportar cualquier diferencia encontrada.

#####export- Exporta fuentes desde CVS, similar al comando checkout.#####

*sintaxis*: export [-flNnR] [-r rev|-D date] [-k subst] [-d dir] module…
*requerimientos*: repositorio.
*cambios*: directorio actual.

Este comando es una variante de checkout, es usado cuando quieres una copia de la fuente para el módulo sin los directorios administrativos de CVS. Por ejemplo, podrías usar export para preparar fuentes para su envio fuera de sitio.Este comando requiere que se especifique una fecha o una etiqueta (con '-D' ó '-r') de modo que usted puede contar con la reproducción de la fuente de envíos a otros(y por lo tanto siempre se tendran directorios vacios ).

A menudo se le gustaría usar '-kv' con cvs export. Esto hace que cualquier palabra clave que se amplie de tal manera que al importarla a algún otro sitio no se pierdan las palabas clave en la revisión de la información.Pero tenga en cuenta que no maneja una exportación que contiene los archivos binarios correctamente.También tenga en cuenta que después de haber usado '-kv', Ya no se puede usar el comando **ident**(que es parte de la suite RCS), que busca cadenas de palabras clave. Si usted quiere ser capaz de utilizar **ident** no debe usar '-kv'.

#####history- Muestra el status de archivos y usuarios#####

- *Sintaxis*: history [-report] [-flags] [-options args] [files…]


- *Requerimientos*: el archivo ‘$CVSROOT/CVSROOT/history’

CVS puede mantener un archivo histórico que rastrea cada uso de checkout, commit, rtag, update, y comandos release. Puede usar history para mostrar esta información en varios formatos.

Loggin debería estar habilitado para la creación del archivo ‘$CVSROOT/CVSROOT/history’.

history usa ‘-f’, ‘-l’, ‘-n’, and ‘-p’ de manera que entra en conflicto con el uso normal dentro de CVS.


***

`aoapedro@hotmail.com`
