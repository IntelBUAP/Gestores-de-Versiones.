<img src="Imagenes/bazaar.png" height="200" width="200"/>

##Introducción##
Bazaar es una herramienta que sirve como sistema de control de versiones de forma distribuida de origen open source, que permite ayudar al seguimiento del historial de un proyecto sobre tiempo y colaborar fácilmente con otros.

Bazaar se caracteriza por ser adaptable y orientado a la mayoría de los trabajos de desarrollo de software tanto local como remoto, también se caracteriza por ser amigable para los que recién empiezan, y al mismo tiempo lo suficientemente potente para los expertos, no comprometiendo así la curva de aprendizaje. Bazaar es ligero en el sentido que no precisa tener un servidor dedicado también permite estar presente en una serie de aplicaciones y servicios libres y/o comerciales.

Al margen de las características de Bazaar que posee por si mismo, cuenta con el patrocinio de Canonical tanto para su desarrollo como su soporte, disponible bajo licencia GPL.

###<center>SISTEMA CONTROL DE VERSIONES BAZAAR</center>
- ####BAZ: Un Gestor de Versiones Anterior a BAZAAR
El nombre de BAZAAR fue utilizado origin almente por una bifurcación cliente de 
la GNU arch tla. Esta bifurcacion es ahora llamada BAZ para distinguirlo del 
software BAZAAR actual. BAZ fue anunciado en Octubre del 2004 por el empleado
de Canonical Robert Collins y se mantuvo hasta 2005, cuando el proyecto 
entonces llamado BAZAAR-NG (software actual) fue anunciado como el sucesor de BAZ.
BAZ está ahora sin mantenimiento y canonical lo declaró obsoleto. La última
versión de BAZ fue la 1.4.3, lanzado en Octubre del 2005. Baz se abandonó en 2006.


- ####BAZAAR
En febrero del 2005, Martin Pool, un desarrollador que había descrito y revisado
una serie de sistemas de control de revisiones en las conversaciones y en su 
weblog previamente, anunció que había sido contratado por canonical y la tarea
de contruir un sistema de control de versiones distribuido que los piratas infor-
máticos de código abierto le encaanta usar. Un sitio web y una lista de correo
pública se estableció en Marzo de 2005 y el pre-lanzamiento de la primer numerada,
0.0.1, fue lanzado el 26 de Marzo del 2005.
BAZAAR fue concebido desde el principio como una pieza diferente de software tanto
de GNU arch y BAZ. Tiene un conjunto de comandos diferentes y es una base de 
código y diseño completamente diferente. BAZAAR fue pensado originalmente como un
banco de pruebas para caracteristicas para ser posteriormente integradas a BAZ. 
Pero a mediados del 2005 muchos de los principales desarrolladores de BAZ habian
comenzado a trabajar principalmente en BAZAAR directamente y BAZ fue abandonado.
La version 1.0 de BAZ fue lanzado en Diciembre de 2007. En Febrero del 2008, 
BAZAAR se convirtió en un proyecto de GNU. En Abril de 2012 Martin Pool dejó
canonical y el ritmo del desarrollo del proyecto ha disminuido. De acuerdo con 
Jelmer Vernooij los miembros del equipo de Bazar de Canonical fueron asignados a
diferentes tareas a principios de 2012 y él mismo renunció a contribuir al bazar 
a finales de 2012, después de 7 años de contribuir al proyecto. En marzo 2013 un
debate sobre el GNU Emacs lista de correo comenzó sobre si Bazar todavía se mantiene 
con eficacia y si Emacs bdeberia transladarse a otro sistema control de versiones.
En Enero del 2014 por múltiples razones una de ellas es la impresión de que el bazar
estaba casi muerto: "Hay tal vez 2-3 compromete a tronco cada mes. El tiempo para
corregir errores en bazar también parece ser bastante largo, por lo general".

##Instalación de clientes##

La configuración de Bazaar-NG se debe crear en “~/.bazaar/bazaar.conf”:

```sh
$ mkdir ~/.bazaar/
$ cd ~/.bazaar/
$ touch bazaar.conf
```

Podemos editar “bazaar.conf” y añadir:

```sh
[DEFAULT]
email             = Your Name <email@isp.com>
editor            = /usr/bin/vim
```

Bazaar-NG requiere que cada desarrollador especifique su nombre e email para así registrar y vincular cada uno de los cambios que se realizan al código, adicionalmente, el hecho de proporcionar el email facilita que cualquier programador pueda ponerse en contacto con alguien que haya realizado un cambio determinado (en caso de proyectos donde participan muchas personas, es de agradecer).

Con la variable “editor” indicamos que editor queremos que se ejecute cuando Bazaar-NG requiere que proporcionemos información, por ejemplo la explicación de los cambios cuando queramos actualizar la rama.

En el fichero de configuración podemos añadir de forma opcional:

```sh
check_signatures  = check-available
create_signatures = when-required
```

Con check_signatures podemos indicar 3 valores:


  - require: Para cada actualización de código debe existir una firma gnupg y ser válida.
  - ignore: No se comprueban firmas gnupg.
  - check-available: (Valor por defecto) Si existe una firma gnupg para la actualización, comprobarla. Bazaar-NG fallará si encuentra una firma incorrecta, pero no si la firma no esta presente.

Con create_signatures podemos indicar también 3 valores:

  - always: Firmar cada actualización que enviemos.
  - when-required: (Valor por defecto) Firmar las actualizaciones que enviemos, sólo si la rama requiere que así lo hagamos.
  - never: No firmar las actualizaciones que enviemos, aunque la rama así lo requiera.

Como se puede intuir por las opciones, Bazaar nos permite firmar criptográficamente (con gnupg) los cambios que realicemos al código y comprobar a la vez, las firmas de los demás desarrolladores. Esta es una medida de seguridad efectiva para garantizar que los cambios son realmente de quien parecen ser, así evitamos que alguna persona mal intencionada intente inyectar código malicioso en nuestro proyecto.

Finalmente, indicar que hasta ahora hemos configurado la sección “Default” que es la configuración global para todos los repositorios. Podríamos crear configuraciones específicas por ramas:

```sh
[DEFAULT]
email             = Your Name <email@isp.com>
editor            = /usr/bin/vim
check_signatures  = check-available
create_signatures = when-required

[/home/usuario/rama01]
email             = Your Name <other_email@isp.com>
```

##Características##

Dentro de las caracteristicas que encontramos en Bazaar tenemos:

- Gestiona el almacenamiento de cada uno de los elementos del proyecto.
- Capacidad de gestionar ramas de desarrollo paralelas a la principal.
- Gestión de conflictos, en el caso de un usuario cambie un elemento de un proyecto.
- Generación de informes de estado, donde se muestren las diferencias entre las distintas versiones.
- Proporciona soporte para IDEs y editores como Eclipse, Visual Studio, Emacs, entre otros.

Sin embargo, a diferencia de CVS o Subversion, Bazaar nos permite trabajar de formas mucho más flexibles… desde el típico esquema cliente-servidor hasta la descentralización de los repositorios.
Con Bazaar tenemos la posibilidad de trabajar de una forma más flexible que CVS o Subversion, adaptándose al flujo de trabajo que queramos utilizar:

  - Centralizado o Lock-Step: Concepto de trabajo igual que el aplicado por Subversion o CVS con la ventaja de una gestión de ramas mejorada mediante un repositorio.
  - Lock-Step con commits locales: Igual que el anterior pero los desarrolladores realizan commits locales sin modificar el servidor hasta que consideran oportuno actualizarlo. Tenemos la ventaja de reducir el número de commits erróneos que interfieran en el trabajo del resto de desarrolladores.
  - Descentralizado con linea principal compartida: Cada programador tiene su propia rama además de permisos en la rama principal. Cada uno trabaja en su rama personal (commit) y cuando lo consideran apropiado, lo fusionan con la rama principal (pull, merge). Ventajas:
    - Organización del trabajo sencilla.
    - Un desarrollador puede fusionar su rama con la de otra persona con la que este trabajando en algo conjuntamente.
  - Descentralizado con guardián automático o manual: Cada programador tiene su propia rama y permisos de solo lectura en la rama principal. Cuando un desarrollador quiere fusionar su código en la linea principal, lo pide al “guardián” que se encarga de revisar, compilar y hacer tests unitarios para comprobar que todo es correcto. La ventaja principal radica en que el código se revisa antes de pasar a la línea principal. 

 ## Proyectos
Proyectos destacados que utilizan Bazaar como sistema de control de versiones:

- GNU Mailman 
- Ubuntu
- GNU Mailman
- GNU Emacs
- Inkscape
- MySQL
- Gnash
- Squid

#Cómo usar Bazaar#

##Presentarse##
Antes de empezar a trabajar, es conveniente que le diga a Bazaar quién es
usted. De ese modo su trabajo será identificando correctamente en los logs
de revisión.
Utilice su nombre y dirección de email en lugar de John Doe, teclee:
```sh
	$ bzr whoami "John Doe <john.doe@gmail.com>"
	//Bazaar creará o modificará ahora un archivo de configuración,
	//incluyendo su nombre y dirección de email.
```

Ahora compruebe que su nombre y dirección de email se han registrado
correctamente:
```sh
	$ bzr whoami
	John Doe <john.doe@gmail.com>
```

##Ponga archivos bajo control de versiones##
Vamos a crear un directorio y algunos archivos para utilizar con Bazaar:
```sh
	$ mkdir miproyecto
	$ cd miproyecto
	$ mkdir subdirectorio
	$ touch test1.txt test2.txt test3.txt subdirectorio/test4.txt
```

>Nota para usuarios de Windows: utilice Windows Explorer para crear sus
directorios, luego haga click derecho en dichos directorios y seleccione
Nuevo archivo para crear sus archivos.
Ahora vamos a hacer que Bazaar se inicialize en el directorio de su proyecto:
```sh
	$ bzr init
```
Si parece que no ha ocurrido nada no se preocupe. Bazaar ha creado un branch
dónde guardará sus archivos y su histórico de revisiones.

El siguiente paso es decirle a Bazaar a que archivos desea seguirles la pista.
Ejecutando bzr add agregará recursivamente todos los elementos dentro del
proyecto:
```sh
	$ bzr add
		added subdirectorio
		added test1.txt
		added test2.txt
		added test3.txt
		added subdirectorio/test4.txt
```
A continuación tome una instantánea de sus archivos agregándolos a su branch.
Agregue un mensaje para explicar por qué hace el commit:
```sh
	$ bzr commit -m "Importación inicial"
```
Como Bazaar es un sistema de control de versiones distribuido, no necesita
conectar con un servidor central para hacer el commit. Bazaar guarda su branch
y todos sus commits dentro del directorio con el que está trabajando, busque
el subdirectorio .bzr.

##Haciendo cambios en sus archivos##
Vamos a cambiar un archivo e introduzcamos ese cambio en su branch.
Edite test1.txt en su editor favorito y luego compruebe qué ha hecho:
```sh
	$ bzr diff
	=== modified file 'test1.txt'
	--- test1.txt   2007-10-08 17:56:14 +0000
	+++ test1.txt   2007-10-08 17:46:22 +0000
	@@ -0,0 +1,1 @@
	+test test test
```
Añada su trabajo al branch de Bazaar:
```sh
	$ bzr commit -m "Añadida la primera línea de texto"
	Committed revision 2.
```
##Viendo el log de revisiones##
Puede ver el histórico de su branch navegando su log:
```sh
	$ bzr log
	------------------------------------------------------------
	revno: 2
	committer: John Doe <john.doe@gmail.com>
	branch nick: miproyecto
	timestamp: Mon 2007-10-08 17:56:14 +0000
	message:
	  Añadida la primera línea de texto
	------------------------------------------------------------
	revno: 1
	committer: John Doe <john.doe@gmail.com>
	branch nick: miproyecto
	timestamp: Mon 2006-10-08 17:46:22 +0000
	message:
	  Importación inicial
```
##Publicando su branch con SFTP##
Hay un par de maneras para publicar su branch. Si ya tiene un servidor SFTP
o se siente cómodo configurando uno, puede publicar su branch con el.
Sino salte a la siguiente sección para publicar con Launchpad, un servicio
de hosting gratuito para Bazaar.

Vamos a suponer que desea publicar su branch en www.example.com/miproyecto:
```sh
	$ bzr push --create-prefix sftp://su.nombre@example.com/~/public_html/miproyecto
	2 revision(s) pushed.
```
Bazaar creará un directorio miproyecto en el servidor
remoto e introducirá su branch en él.

Ahora cualquiera podrá crear su propia copia de su branch tecleando:
```sh
	$ bzr branch http://www.example.com/miproyecto
```
	
>Nota: para utilizar SFTP deberá instalar paramiko y pyCrypto.
Vea <http://wiki.bazaar.canonical.com/InstallationFaq> para más información.

##Publicando su branch con Launchpad##
Launchpad es una suite de herramientas de desarrollo y hosting para proyectos
de software libre. Puede utilizarlo para publicar su branch.
Si no dispone de una cuenta de Launchpad, siga la guia de registro de cuentas
y registre una clave SSH en su nueva cuenta de Launchpad.

Cambie john.doe por su nombre de usuario de Launchpad, teclee:
```sh
	$ bzr push bzr+ssh://john.doe@bazaar.launchpad.net/~john.doe/+junk/miproyecto
```

>Nota: +junk significa que este branch no está asociado con ningún proyecto
concreto en Launchpad.

Ahora cualquiera podrá crear su propia copia de su branch tecleando:
```sh
	$ bzr branch http://bazaar.launchpad.net/~john.doe/+junk/miproyecto
```
También puede ver información sobre su branch, histórico de revisiones
incluido, en <https://code.launchpad.net/people/+me/+junk/miproyecto>
Creando su propia copia de otro branch
Para trabajar con el código de otra persona, tendrá que hacer su propia
copia de su branch. Vamos a coger un ejemplo real, la interfaz GTK de Bazaar:
```sh
	$ bzr branch http://bazaar.launchpad.net/~bzr/bzr-gtk/trunk bzr-gtk.john
	Branched 292 revision(s).
```
Bazaar descargará todos los archivos y el histórico de revisiones completo del
trunk branch del proyecto bzr-gtk y creará una copia llamada bzr-gtk.john.
Ahora dispone de su propia copia del branch y puede enviar cambios con o sin
una conexión de red. Puede compartir su branch en cualquier momento
publicándola y, si el equipo de bzr-gtk desea utilizar su trabajo, Bazaar les
facilita integrar su branch dentro de su trunk branch.
Actualizando su branch desde el branch principal.
Mientras envía cambios a su branch, es probable que otras personas también
sigan enviando código al branch principal.

Para asegurarse de que su branch está al dia debería integrar los cambios
desde el principal dentro de su branch personal:
```sh
	$ bzr merge
	Merging from saved parent location: http://bazaar.launchpad.net/~bzr/bzr-gtk/trunk
	All changes applied successfully.
```
Compruebe qué ha cambiado:
```sh
	$ bzr diff
```
Si está contento con los cambios puede añadirlos en su branch personal:
```sh
	$ bzr commit -m "Integración desde el branch principal"
	Committed revision 295.
```
Integrando su trabajo en el branch principal
Después de haber trabajado en su branch personal de bzr-gtk puede que quiera
enviar sus cambios de vuelta al proyecto. La manera más fácil es utilizando
una instrucción merge.
Una instrucción merge es una petición de lectura mecánica para llevar a cabo
una integración concreta. Por lo general contiene un parche de vista previa de
la integración y, o bien contiene las revisiones necesarias, o proporciona un
branch donde pueden encontrarse.
Sustituyendo mycode.patch, cree su instrucción merge:
```sh
	$ bzr send -o mycode.patch
	Using saved parent location: http://bazaar.launchpad.net/~bzr/bzr-gtk/trunk
```
Ahora puede enviar por email la instrucción merge al proyecto bzr-gtk quien, si
así lo quieren, pueden utilizarla para integrar su trabajo dentro del
branch principal.

##Aprendiendo más##
Para aprender sobre Bazaar por línea de comandos:
```sh
	$ bzr help
```
Para aprender sobre comandos de Bazaar:
```sh
	$ bzr help commands
```
Para aprender acerca del tema o comando ‘’foo’‘:
```sh
	$ bzr help foo
```

##Fuente##
<http://doc.bazaar.canonical.com/current/es/mini-tutorial/index.html>