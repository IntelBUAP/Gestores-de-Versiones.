####Gestor de Versiones: CVS (Concurrent Version System).


##### *** - Introducción.***

***
<p style="text-align: justify;"> - En este marco teórico, se describe el concepto de Gestor de Versión CVS. Dado el problema entre los desarrolladores del intercambio de ficheros de código fuente, surge la necesidad de evitar este tipo de conflicto mediante la herramienta mencionada, esto, descrito en la investigación recabada en este documento. </p>

<p style="text-align: justify;">- Así mismo, se hace mención de su historia, principales características, uso y manejo del mismo con su respectiva descripción. </p>

<p style="text-align: justify;"> - Los gestores de versiones, también llamados Herramientas de Gestión de Configuraciones de Software ó Repositorios, son herramientas que permiten a desarrolladores de Proyectos centralizar y coordinar sus trabajos. Manteniendo los registros y cambios de distintos ficheros de un Proyecto; principalmente cógido fuente. Permitiendo la colaboración de distintos desarrolladores e incluyendo la evolución en líneas paralelas de un mismo Proyecto. Conociendo más características de la misma, hará de nuestro ejercicio y desarrollo una interacción concurrente e independiente. </p>

##### - Ventajas.

* Aplicación Cliente-Servidor.
* Usado para archivos de código fuente y otros tipos de archivos.
* Empleado para administrar versiones y cambios sobre archivos.
* Difundido bajo licencia de GLP.
* Permite la concurrencia de trabajo.
* Integración de versiones.
* Manejo de múltiples versiones simultáneas.

##### - Otros sistemas.

* Microsoft Source Safe.
* Clear Case.
* Visual Studio Team System Source Control.
* YACC.
* DARCS.
* Apache Subversion (SVN).
* Git.
* Mercurial.

***


##### - Historia.
***
<p style="text-align: justify;"> **CVS** comenzo a desarrollarse por [***Dick Grune***](http://www.dickgrune.com/ "Dick Grune") a mediados de los *80's* a partir de un sistema de control de versiones anterior llamado *"Sistema de Control de Revisiones"* (RCS), que gestiona archivos individuales, pero no proyectos integrales. </p><p style="text-align: center;"> ![Dick Grune](http://www.dickgrune.com/pictures/dick.jpg "Dick Grune") </p>
<p style="text-align: justify;"> Dick Grune creo lo que se conoce como la *"version antigua"* de CVS para poder cooperar con sus estudiantes (*Erik Baalbergen y Maarten Waage*) en el ACK (*Ámsterdam Compiler Kit* compilador de C). Ya que los tres tenian diferentes horarios y solo podian programar en sus ratos libres. Inicialmente lo llamaron **cmt** (*commit versions independently*), porque les permitió combinar versiones independientes de codigo en un mismo proyecto. Grune lanzó públicamente el código (*un conjunto de scripts*) en Usenet para mod.sources el **23 de junio 1986**. Y por fin un sistema de control de versiones permitió a los desarrolladores trabajar simultaneamente de forma mas o menos independiente, pasando cada uno a trabajar sobre una copia del proyecto total que se iba sincronizando con el proyecto general. </p> <p style="text-align: justify;"> Unos años mas tarde, en **1989**, ***Brian Berliner*** tomo los scripts de Grune  y los reescribió en C, creando lo que sería la *"versión moderna"* de CVS, ya con una clara arquitectura cliente-servidor, tiempo despues se le unieron ***Jeff Polk*** y muchos otros colaboradores, lo liberaron para beneficio de la comunidad bajo la **GPL**. </p> <p style="text-align: justify;"> El **19 de noviembre de 1990**, CVS versión **1.0** fue presentado a la **Free Software Foundation** para su desarrollo y distribución. Así pasó a ser el sistema de control de versiones más usado del mundo. Desde entonces se han sucedido diversos cambios realizados por varias empresas, especialmente **Cygnus Support** y **Cyclic Software**. En la actualidad, casi todos los cambios recientes en **CVS** son obra de Cyclic. Y tras eliminar alguna dependencias CVS paso a ser parte oficial del proyecto **GNU**, además es usado por la mayoría de los grandes proyectos de software libre del mundo (*gcc, emacs, guile, gtk, gimp, gnome, linux, etc.*). </p>

***

##### - Características.
***
1. Arquitectura cliente-servidor.
    <p style="text-align: justify;"> * El servidor guarda la(s) versión(es) actual(es) del proyecto y su historial (una version consolidada del proyecto).
    <p style="text-align: justify;"> * El cliente o estacion de trabajo hace modificaciones al codigo y realiza las pruebas necesarias para satisfacer los requerimientos. Los clientes se conectan al servidor para sacar una copia completa del proyecto, esto se hace eventualmente para que puedan trabajar con esa copia y más tarde ingresar sus cambios.
    <p style="text-align: justify;"> * Debe exitir comunicacion entre cliente y el servidor al realizar operaciones CVS como checkins o actualizaciones, pero si se quiere editar o manipular las versiones actuales de los archivos los clientes pueden bajar una copia y realizar las operaciones disponibles a nivel local. </p></p></p>

<p style="text-align: justify;"> 2. Mantiene el registro de la historia de las versiones del programa de un proyecto solamente con desarrolladores locales. </p>

<p style="text-align: justify;"> 3. Originalmente, el servidor utilizaba un sistema operativo similar a Unix, aunque en la actualidad existen versiones de CVS en otros sistemas operativos como Windows. </p>

<p style="text-align: justify;"> 4. Si se actualizan modificaciones, el servidor trata de acoplar las diferentes versiones. *(Si esto falla, por ejemplo debido a que dos clientes tratan de cambiar la misma línea en un archivo en particular, entonces el servidor deniega la segunda actualización e informa al cliente sobre el conflicto, que el usuario deberá resolver manualmente.)* Si la operación de ingreso tiene éxito, entonces los números de versión de todos los archivos implicados se incrementan automáticamente, y el servidor CVS almacena información sobre la actualización. </p>

<p style="text-align: justify;"> 5. Descripción suministrada por el usuario. </p>
* Fecha.
* Nombre del autor.
* Archivos de registro (log) del autor.

<p style="text-align: justify;"> 6. CVS también puede mantener distintas "ramas" *(revisiones paralelas de un modulo para efectuar cambios sin tocar la evolucion principal. Se suele emplear para pruebas o para mantener cambios en versiones viejas)* de un proyecto. Por ejemplo, una versión difundida de un proyecto de programa puede formar una rama y ser utilizada para corregir errores. Todo esto se puede llevar a cabo mientras la versión que se encuentra actualmente en desarrollo y posee cambios mayores con nuevas características se encuentre en otra línea formando otra rama separada. </p>
<p style="text-align: justify;"> 7. Cada archivo tiene un numero de revision independiente, este numero registra el numero de cambios hechos al archivo y no tiene ninguna relacion con algun numero de version del proyecto completo. </p>

<p style="text-align: justify;"> 8. En los casos en que varios desarrolladores o equipos requieran una versión de los archivos y, debido a la geografía o la política no puedan adquirirlo; pueden importar una versión de otro equipo **(incluso si no utilizan CVS)**, y luego CVS puede combinar los cambios de la rama de proveedor con los últimos archivos si eso es lo que se desea. </p>

<p style="text-align: justify;"> 9. Proporciona una base de datos de módulos flexibles que ofrece una correspondencia simbólica de los nombres a los componentes de una distribución de software más grande, (esto se aplica a las colecciones nombres de directorios y archivos; un solo comando puede manipular toda la selección). </p>

<p style="text-align: justify;"> 10. Los clientes pueden: </p>
* Comparar diferentes versiones de archivos.
* Solicitar una historia completa de los cambios.
* Sacar una "foto" histórica del proyecto tal como se encontraba en una fecha determinada o en un número de revisión determinado.
* Utilizar la orden de actualización con el fin de tener sus copias al día con la última versión que se encuentra en el servidor (esto elimina la necesidad de repetir las descargas del proyecto completo).
* Funcionar en cualquiera de los sistemas operativos más difundidos.
* Sacar copias del proyecto al mismo tiempo.
* Sacar y comparar versiones sin necesidad de teclear una contraseña en proyectos de código abierto *("acceso de lectura anónimo")*.Solamente el ingreso de cambios requiere una contraseña en estos casos.

#####- Limitaciones de CVS.
<p style="text-align: justify;"> 1. Los archivos en el repositorio sobre la plataforma CVS no pueden ser renombrados, estos deben ser agregados con otro nombre y luego eliminados. </p>

<p style="text-align: justify;"> 2. El protocolo CVS no provee una manera de que los directorios puedan ser eliminados o renombrados, cada archivo en cada subdirectorio debe ser eliminado y re-agregado con el nuevo nombre. </p>

<p style="text-align: justify;"> 3. Soporte limitado para archivos Unicode con nombres de archivo no ASCII.</p>

<p style="text-align: justify;"> 4. Actividades como la planificacion, los releases, etc, quedan fuera de su ambito de trabajo y deben ser abordadas por las personas y otras herramietnas complementarias</p>

***

##### - Uso del Gestor con comandos.
***

##### I. Descripción.

El formato general de todos los comandos de _CVS_ es:

    cvs [ cvs_options ] cvs_command [ command_options ] [ command_args ]

Donde:

    cvs

Es el nombre del programa _CVS_.

    cvs_options

Algunas opciones que afectan a todos los sub-comandos de _CVS_.

    cvs_command
<p style="text-align: justify;">Uno de varios sub-comandos diferentes. Algunos de los comandos tienen alias que se pueden utilizar en su lugar; los alias se indican en el manual de referencia para ese comando. Sólo hay dos situaciones en las que es posible omitir _'cvs_command'_: _'-H cvs'_ provoca una lista de comandos disponibles, y _'-v cvs'_ muestra información de la versión de _CVS_.</p>

    command_options

Opciones que son específicas del comando.

    command_args

Argumentos a los comandos.

##### II. Opciones globales.

Las _'cvs_options'_ disponibles son:

    --allow-root=rootdir

Especifica el directorio _CVSROOT_ legal.

    -a
<p style="text-align: justify;"> Autentifica todas las comunicaciones entre el cliente y el servidor. Solo tiene efecto en el cliente _CVS_.</p>

    - T tempdir
<p style="text-align: justify;"> Use _tempdir_ como el directorio donde los archivos temporales son colocados. Anula la configuración de la variable de entorno _$ TMPDIR_ y cualquier directorio precompilado. Este parámetro debe especificarse como una ruta absoluta. </p>

    -d cvs_root_directory
<p style="text-align: justify;"> Utilice _cvs_root_directory_ como la ruta de acceso al directorio raíz del repositorio. Anula la configuración de la variable de entorno _$ CVSROOT_ .</p>

    -e editor
<p style="text-align: justify;">Utilice editor para introducir la información de registro de revisiones. Anula el ajuste de las variables de entorno _$ CVSEDITOR_ y _$EDITOR. </p>

     -H
    --help

Muestra informacion del uso del comando _'cvs_command'_ especificado.

    -r
<p style="text-align: justify;"> Haga nuevos archivos de trabajo de sólo lectura. Mismo efecto que si se establece la variable de entorno _$CVSREAD_. </p>

    -s variable=value

Establece una variable de usuario.

    -t
<p style="text-align: justify;"> Traza la ejecución del programa; muestra mensajes en la pantalla de los pasos de la actividad _CVS_. </p>

     -v
    --version

Muestra la version y la información del copyright para _CVS_.

    -w
<p style="text-align: justify;"> Crea nuevos archivos de trabajo de lectura y escritura. Anula la configuración de la variable de entorno _$ CVSREAD_. </p>

#####III. Añadir archivos y directorios en el repositorio.

    add [-k rcs-kflag] [-m message] files...
<p style="text-align: justify;"> El comando _add_ se utiliza para presentar los nuevos archivos y directorios para la adición al repositorio _CVS_. Cuando se utiliza _add_ en un directorio, un nuevo directorio se crea en el repositorio inmediatamente. Cuando se utiliza en un archivo, sólo el directorio de trabajo se actualiza. Los cambios en el repositorio no se hacen hasta que el comando _commit_ se utiliza en el archivo que se acaba de agregar. </p><p style="text-align: justify;"> El comando _add_ también resucita a los archivos que se han eliminado previamente. Esto se puede hacer antes o después de que el comando _commit_ se utilice para finalizar la eliminación de archivos. Los archivos resucitados se restauran en el directorio de trabajo en el momento en que se ejecute el comando _add_. </p>

#####IV. Opciones del comando _add_.

    -k kflag

Procesa palabras clave de acuerdo con _kflag_.

    -m message

Utiliza _message_ como el mensaje de registro, en lugar de invocar un editor.

#####V. _annotate_ - ¿Qué revisión modificó cada línea de un archivo?

    annotate [options] files…
<p style="text-align: justify;"> Para cada archivo en _files_, imprime la revisión principal del tronco, junto con información sobre la última modificación para cada línea. </p>

#####VI. Opciones del comando _annotate_.

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

#####VII. Ejemplo del comando _annotate_.

    $ cvs annotate ssfile
    Annotations for ssfile
    
    1.1          (mary     27-Mar-96): ssfile line 1
    1.2          (joe      28-Mar-96): ssfile line 2
<p style="text-align: justify;"> El archivo _'ssfile'_ contiene actualmente dos líneas. La línea _ssfile line 1_ se registró por mary el 27 de marzo. Luego, el 28 de marzo, joe añadió la línea _ssfile line 2_, sin modificar la línea _ssfile line 1_. Este informe no dice nada acerca de las líneas que han sido borradas o reemplazadas; es necesario utilizar _cvs diff_ para eso. </p>

####VIII. _checkout_ - Mirar las fuentes para la edición.

    checkout [options] modules…
<p style="text-align: justify;"> Crea o actualiza un directorio de trabajo que contiene copias de los archivos de fuente especificados por _modules_. Debe ejecutar _checkout_ antes de usar la mayoría de los otros comandos de _CVS_, ya que la mayoría de ellos operan en su directorio de trabajo. </p><p style="text-align: justify;"> Los módulos son o bien los nombres simbólicos para alguna colección de directorios fuente y archivos, o rutas de acceso a directorios o archivos en el repositorio. Los nombres simbólicos se definen en el archivo _'modules'_. </p><p style="text-align: justify;"> En función de los módulos especificados, _checkout_ puede crear directorios de forma recursiva y poblarlos con los archivos de fuente correspondientes. Puede entonces editar estos archivos fuente en cualquier momento (independientemente de que otros desarrolladores de software están editando sus propias copias de las fuentes); actualizarlos para incluir nuevos cambios aplicados por otros al repositorio de código fuente; o hacer un _commit_ de su trabajo como un cambio permanente en el repositorio de código fuente. </p><p style="text-align: justify;"> Tenga en cuenta que _checkout_ se utiliza para crear directorios. El directorio de nivel superior creado siempre se añade al directorio donde se invoca _checkout_, y por lo general tiene el mismo nombre que el módulo especificado. En el caso de un alias del módulo, el sub-directorio creado puede tener un nombre diferente, pero usted puede estar seguro de que será un subdirectorio, y que _checkout_ mostrará la ruta relativa que lleva a cada archivo extraído dentro de su área privada de trabajo (a menos que especifique la opción global _"-Q"_). </p>

#####IX. Opciones del comando _checkout_.

    -D date
<p style="text-align: justify;"> Utiliza la revisión más reciente a más tardar en la fecha. Esta opción es _sticky_, e implica _'-P'_.  </p>

    -f
<p style="text-align: justify;"> Sólo útil con las banderas _'-D date'_ o _'-r tag'_. Si no se encuentra la revisión correspondiente, recupera la revisión más reciente (en lugar de ignorar el archivo). </p>

    -k kflag
<p style="text-align: justify;"> Procesa las palabras clave de acuerdo con _kflag_. Esta opción es _sticky_; las futuras actualizaciones de este archivo en el directorio de trabajo utilizarán la misma _kflag_.  </p>

    -l
Local; ejecutar sólo en el directorio de trabajo actual.

    -n
<p style="text-align: justify;"> No ejecutar cualquier programa _checkout_ (como se especifica con la opción _'-o'_ en el archivo de los módulos).</p>

    -P

Recortar directorios vacíos.

    -p

Archivos de tubería a la salida estándar.

    -R
<p style="text-align: justify;"> Directorios _checkout_ de forma recursiva. Esta opción está activada de forma predeterminada. </p>

    -r tag

Utiliza la etiqueta de revisión. Esta opción es _sticky_, e implica _'-P'_    .

#####X. Además de esas, puede utilizar estas opciones de comandos especiales con _checkout_:

    -A
<p style="text-align: justify;"> Restablece cualquier etiqueta _sticky_, fechas u opciones _'-k'_. No restablece opciones _sticky_ _'-k'_  en los archivos modificados. </p>

    -c
<p style="text-align: justify;"> Copia el archivo de módulo, ordenado, a la salida estándar, en lugar de crear o modificar los archivos o directorios en el directorio de trabajo. </p>

    -d dir
<p style="text-align: justify;"> Crea un directorio llamado _dir_ para los archivos de trabajo, en lugar de utilizar el nombre del módulo. En general, el uso de esta bandera es equivalente a usar _'mkdir dir; cd dir'_ seguido por el comando _checkout_ sin la etiqueta _' -d '_. </p>

#####XI. Ejemplo del comando _checkout_.
Obtiene una copia del módulo _'tc'_:

    $ cvs checkout tc

Obtiene una copia del módulo _'tc'_ como se veía hace un día:

    $ cvs checkout -D yesterday tc


####XII. _commit_ - Revise los archivos en el repositorio.

    commit [-lRf] [-m ’log_message’ | -F file] [-r revision] [files…]
<p style="text-align: justify;"> Utilice _commit_ cuando se quiera incorporar los cambios de los archivos fuente de trabajo en el repositorio de origen. </p><p style="text-align: justify;"> Si no se especifican archivos particulares en _commit_, todos los archivos en el directorio actual de trabajo se examinan. _commit_ es cuidadoso al cambiar en el repositorio sólo aquellos archivos que que realmente han cambiado. Por defecto (o si se especifica explícitamente la opción _'-R'_), se examinan también los archivos de los subdirectorios y se hace _commit_ si han cambiado; puede utilizar la opción _'-l'_ para limitar el _commit_ a sólo el directorio actual. </p><p style="text-align: justify;"> _commit_ verifica que los archivos seleccionados están al día con las revisiones actuales en el repositorio de origen; se notifica y se sale sin hacer el _commit_, si alguno de los archivos especificados debe actializarse. _commit_ no llama al comando de actualización, sino que deja que se pueda hacer cuando sea el momento adecuado. </p><p style="text-align: justify;"> Cuando todo está bien, un editor se invoca para permitirle introducir un mensaje de registro que se escribirá a uno o más programas de registro y se coloca en el archivo RCS en el repositorio. Este mensaje de registro se puede recuperar con el comando log. Se puede especificar el mensaje de registro en la línea de comandos con la opción _'-m message'_, y así evitar la invocación editor, o utilizar la opción _"-F file'_ para especificar que el argumento del archivo contiene el mensaje de registro. </p>

#####XIII. Opciones del comando _commit_.

    -l

Local; ejecuta sólo en el directorio de trabajo actual.

    -R

Directorios _commit_  de forma recursiva. Esto está activada por defecto.

    -r revision
<p style="text-align: justify;"> _commit_ a revisión. _revision_ debe ser o bien una rama, o una revisión en el tronco principal que es mayor que cualquier número de revisión existente. No se puede hacer _commit_ a una revisión específica en una rama. </p>

_commit_ también es compatible con las siguientes opciones:

    -F file

Lee el mensaje de registro del archivo, en lugar de invocar un editor.

    -f
<p style="text-align: justify;"> Tenga en cuenta que este no es el comportamiento estándar de la opción _'-f'_ como se define en las opciones de comandos comunes. </p><p style="text-align: justify;"> Fuerza a CVS a hacer _commit_ de una nueva revisión, incluso si no se ha realizado ningún cambio en el archivo. Si la revisión actual del archivo es 1.7, los siguientes dos comandos son equivalentes: </p>
     
    $ cvs commit -f file
    $ cvs commit -r 1.8 file
<p style="text-align: justify;"> La opción _'-f'_ deshabilita la recursividad (es decir, implica _'-l'_). Para forzar a CVS para hacer _commit_ de una nueva revisión de todos los archivos en todos los subdirectorios, debe utilizar _'-f -R'_. </p>
    
    -m message

Utiliza _message_ como el mensaje de registro, en lugar de invocar un editor.

#####XIV. diff - Muestra las diferencias entre revisiones.

    diff [-lR] [-k kflag] [format_options] [[-r rev1 | -D date1] [-r rev2 | -D date2]] [files…]

* Requerimientos: directorio de trabajo, repositorio.
* Cambios: ninguno.
</p><p style="text-align: justify;"> El comando _diff_ es usado para comparar diferentes revisiones de archivos. La acción predeterminada es comparar sus archivos de trabajo con las revisiones que se basaron en el, y reportar cualquier diferencia encontrada. </p>

#####XV. export - Exporta fuentes desde CVS, similar al comando checkout.

    export [-flNnR] [-r rev|-D date] [-k subst] [-d dir] module…

* Requerimientos: repositorio.
* Cambios: directorio actual.
<p style="text-align: justify;"> Este comando es una variante de checkout, es usado cuando quieres una copia de la fuente para el módulo sin los directorios administrativos de CVS. Por ejemplo, podrías usar export para preparar fuentes para su envio fuera de sitio.Este comando requiere que se especifique una fecha o una etiqueta (con '-D' ó '-r') de modo que usted puede contar con la reproducción de la fuente de envíos a otros(y por lo tanto siempre se tendran directorios vacios ). </p><p style="text-align: justify;"> A menudo le gustaría usar '-kv' con cvs export. Esto hace que cualquier palabra clave que se amplie de tal manera que al importarla a algún otro sitio no se pierdan las palabas clave en la revisión de la información.Pero tenga en cuenta que no maneja una exportación que contiene los archivos binarios correctamente.También tenga en cuenta que después de haber usado '-kv', Ya no se puede usar el comando **ident**(que es parte de la suite RCS), que busca cadenas de palabras clave. Si usted quiere ser capaz de utilizar **ident** no debe usar '-kv'. </p>

#####XVI. history - Muestra el status de archivos y usuarios.

    history [-report] [-flags] [-options args] [files…]

* Requerimientos: el archivo ‘$CVSROOT/CVSROOT/history’
* Cambios: nada.

<p style="text-align: justify;"> CVS puede mantener un archivo histórico que rastrea cada uso de checkout, commit, rtag, update, y comandos release. Puede usar history para mostrar esta información en varios formatos. </p>

Loggin debería estar habilitado para la creación del archivo ‘$CVSROOT/CVSROOT/history’.
<p style="text-align: justify;"> _history_ usa ‘-f’, ‘-l’, ‘-n’, and ‘-p’ de manera que entra en conflicto con el uso normal dentro de CVS. </p>

#####<p style="text-align: justify;">  XVII. import - Importación de fuentes en CVS usando ramas de desarrollo. </p>

    import [-opciones] ETIQUETALIBERACIÓN etiquetadesarrollo repositorio ...  

* Requerimientos: directorio de distribución de repositorio, fuente.
* Cambios: repositorio.
    
</p><p style="text-align: justify;"> Use **_import_** para incorporar una fuente de distribución de la totalidad de una fuente externa (por ejemplo, un proveedor de origen) en el directorio de repositorio de código fuente. Puede utilizar este comando, tanto para la creación inicial de un repositorio, y actualizaciones al por mayor en el módulo de la fuente externa. El argumento repositorio da un nombre de directorio (o una ruta de acceso a un directorio) bajo el directorio CVS raíz de repositorios; si no existiera el directorio, import lo crea. </p><p style="text-align: justify;"> Cuando usas import para actualizaciónes de código que han sido modificadas en su repositorio de fuentes(desde una importación antes), será norificado por algún conflicto de archivos en las dos ramas de desarrollo; usa 'checkout -j' para reconciliar las diferencias, tal como import instruye hacerlo. Si CVS decide que un archivo deberia ser ignorado, no lo importa e imprime una 'I 'seguido de el nombre de archivo. </p><p style="text-align: justify;"> Si el archivo "$ CVSROOT / CVSROOT / cvswrappers 'existe, cualquier archivo cuyo nombre coincida con las especificaciones de ese archivo será tratado como paquetes y el filtrado adecuado se realizará en el directorio / archivo antes de ser importado. Ver el archivo cvswrappers. </p><p style="text-align: justify;"> La fuente externa se guarda en una rama de primer nivel, por defecto 1.1.1. Las actualizaciones son hojas de esta rama; por ejemplo, los archivos de la primera colección importada de la fuente será la revisión 1.1.1.1, a continuación, los archivos de la primera actualización importados serán la revisión 1.1.1.2, y así sucesivamente. </p><p style="text-align: justify;"> Se requieren al menos tres argumentos. Repositorio es necesario para identificar la colección de fuente. Vendortag es una etiqueta para toda la rama (por ejemplo, por 1.1.1). También debe especificar al menos una RELEASETAG para identificar los archivos en las hojas creadas cada vez que ejecute **_import_**. El RELEASETAG debe ser nuevo, no existentes previamente en el archivo de depósito, e identificar de forma única el import release. </p><p style="text-align: justify;"> Note que **_import_** no cambia el directorio en el que se invoca.En particular, no se estableció ese directorio como directorio de trabajo CVS; si quieres trabajar con las fuentes importarlas primero y luego compruebalo en un directorio diferente. </p>

#####XVIII. log - Imprime información de registro para los archivos.

    log [options] [files…]   

* Requerimientos: repositorio, directorio de trabajo.
* Cambios: ninguno.
* Sinónimo: parche.

<p style="text-align: justify;"> Muestra la información de registro para los archivos. Log utiliza para llamar a la RCS la utilidad rlog. Aunque esto ya no es así en las fuentes actuales, esta historia determina el formato de la salida y las opciones, que no están muy al estilo de los demás comandos CVS. La salida incluye la ubicación de el archivo RCS, la revisión pincipal (la última revisión en el tronco), todos los nombres simbólicos (etiquetas) y algunas otras cosas. Para cada revisión, el número de revisión, el autor, el número de líneas añadidas / eliminadas y el mensaje de registro se imprimen. Todas las horas se muestran en hora universal coordinada (UTC). (Otras partes de CVS tiempos de impresión en la zona horaria local). </p>

#####XIX. rdiff - Formatos 'patch' diff entre versiones.

    rdiff [-flags] [-V vn] [-r t|-D d [-r t2|-D d2]] modules…    

* Requerimientos: repositorio.
* Cambios: ninguno.
* Sinónimo: parche.

<p style="text-align: justify;"> Construye un parche formato Larry Wall (1) Archivo entre dos lanzamientos, que se pueden alimentar directamente en el parche de programa para llevar una vieja versión puesta al día con la nueva versión. (Esta es una de las pocos comandos CVS que operan directamente desde el repositorio, y no requiere una comprobación previa.) La salida diff se envía al dispositivo de salida estándar. Puede especificar (usando el estándar '-r' y '-D' opciones) cualquier combinación de uno o dos revisiones o fechas. Si se especifica una sola revisión o la fecha, el archivo de revisión refleja las diferencias entre esa revisión o la fecha y las revisiones de cabecera actuales en el archivo RCS. Tenga en cuenta que si la versión de software afectado está contenido en más de un directorio, entonces puede ser necesario especificar la opción '-p' para el comando patch cuando se parchean las fuentes antiguas, de modo que el parche es capaz de encontrar los archivos que se encuentran en otros directorios. </p>

#####XX. release - Indica que un módulo ya no está en uso.

    release [-d] directories…   

* Requerimientos: Directorio de trabajo.
* Cambios: Directorio de trabajo, registro de la historia.

<p style="text-align: justify;"> Este comando está destinado a cancelar de forma segura el efecto de 'cvs checkout'. Desde CVS no bloquea los archivos, no es estrictamente necesario el uso de este comando. Usted siempre puede simplemente borrar su directorio de trabajo, si se quiere; pero corre el riesgo de perder los cambios que pueda haber olvidado, y no deja ningún rastro en el archivo histórico CVS si es que usted ha abandonado su checkout. </p>

<p style="text-align: justify;"> Use ‘cvs release'para evitar estos problemas. Este comando comprueba que no haya cambios no confirmados presentes; que se está ejecutando desde inmediatamente por encima de un directorio CVS de trabajo; y que el repositorio de grabado para sus archivos es el mismo que el definido en el repositorio de la base de datos del módulo. Si todas estas condiciones se cumplen, 'cvs release' deja constancia de su ejecución (que acredite que intencionalmente quiere abandonar su checkout) registro en el CVS del histórico. </p>

#####XXI. remove - Elimina archivos de uso activo.

    remove [-flR] [files...]  

* Requerimientos: repositorio, directorio de trabajo.
* Cambios: directorio de trabajo.

<p style="text-align: justify;"> El comando remove se utiliza para eliminar archivos no deseados de su uso activo. El usuario elimina normalmente los archivos desde el directorio de trabajo antes de la invocación del comando remove. Sólo el directorio de trabajo se actualiza. Los cambios en el repositorio no se realizan hasta que el comando commit es ejecutado. </p>

<p style="text-align: justify;"> El comando remove no elimina archivos desde el repositorio. CVS mantiene todos los datos históricos en el repositorio de manera que es posible reconstruir los estados anteriores de los proyectos bajo control de revisión. Para deshacer el comadno remove CVS ó para resucitar los archivos que se han eliminado previamente, consulte la Sección complemento Agregar archivos y directorios en el repositorio. </p>

#####XXII. update - Trae el árbol de trabajo en sincronización con el repositorio.

    update [-ACdflPpR] [-I name] [-j rev [-j rev]] [-k kflag] [-r tag|-D date] [-W spec] files…

* Requerimientos: repositorio, directorio de trabajo.
* Cambios: directorio de trabajo.

</p><p style="text-align: justify;"> Después de ejecutar un checkout para crear su copia privada de la fuente desde el repositorio común, otros desarrolladores continuarán cambiando la fuente central. De vez en cuando, cuando sea conveniente en su proceso de desarrollo, puede utilizar el comando **_update_** desde dentro de su directorio de trabajo para conciliar su trabajo con las revisiones aplicadas al repositorio de código fuente desde el último **_checkout_** ó **_update_**. </p>
***
 
##### - Instalación *(Links a tutoriales online)*.
***
#####1. Windows.
* [Instalación CVS en Windows](http://nideaderedes.urlansoft.com/2006/04/23/cvs-en-windows-en-menos-de-10-minutos/)

##### 2. Linux.
* [Instalación CVS en Linux](https://ubuntulife.wordpress.com/2007/05/28/instalar-un-servidor-de-cvs-en-ubuntu/)

##### 3. MacOX.
* [InstalarCVS en Mac OS X](http://cambrico.net/mac/instalar-cvs-en-mac-os-x-leopard)

***
`aoapedro@hotmail.com`

<!--It's comentary...-->

 

