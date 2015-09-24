#Introducción a Mercurial

Mercurial es un sistema de control de versiones multiplataforma, para desarrolladores de software. Está implementado principalmente haciendo uso del lenguaje de programación Python, pero incluye una implementación binaria de diff escrita en C. Mercurial fue escrito originalmente para funcionar sobre GNU/Linux. Ha sido adaptado para Windows, Mac OS X y la mayoría de otros sistemas tipo Unix. Mercurial es, sobre todo, un programa para la línea de comandos. Todas las operaciones de Mercurial se invocan como opciones dadas a su programa motor, hg (cuyo nombre hace referencia al símbolo químico del mercurio).

Las principales metas de desarrollo de Mercurial incluyen un gran rendimiento y escalabilidad; desarrollo completamente distribuido, sin necesidad de un servidor; gestión robusta de archivos tanto de texto como binarios; y capacidades avanzadas de ramificación e integración, todo ello manteniendo sencillez conceptual1 Incluye una interfaz web integrada.

##Historia
El creador y desarrollador principal de Mercurial es Matt Mackall. El código fuente se encuentra disponible bajo los términos de la licencia GNU GPL versión 2, lo que clasifica a Mercurial como software libre.

Mackall hizo pública la existencia de Mercurial el 19 de abril de 2005. El estímulo que llevó a esto fue el anuncio de Bitmover, publicado anteriormente aquel mismo mes, informando que retirarían la versión gratuita de BitKeeper.

Se había estado usando BitKeeper debido a los requisitos de control de versiones del proyecto del núcleo Linux. Mackall decidió escribir un sistema de control distribuido de versiones como sustituto para usarlo con el núcleo Linux. Este proyecto comenzó aproximadamente al mismo tiempo que otro denominado git, iniciado por el propio Linus Torvalds con objetivos similares.

El proyecto Linux decidió usar Git en lugar de Mercurial. Sin embargo, muchos otros proyectos usan este último.

##Características

  - **Arquitectura distribuida**

Los sistemas gestores de versiones tradicionales (como Subversion) tienen generalmente una arquitectura cliente-servidor, donde un servidor central almacena las revisiones de un proyecto. En contraste, Mercurial es verdaderamente distribuido, permitiéndole a cada desarrollador una copia local del historial de desarrollo completo. De esta forma es posible trabajar independientemente de un servidor central o del acceso a la red. El envío de cambios (committing), ramificaciones (branching) y fusión (merging) de archivos son rápidas y poco costosas.

  - **Rápido**

Las implementaciones y estructuras de datos de Mercurial están diseñadas para ser rápidas. 
Es posible comprobar cambios (diffs) entre revisiones, o regresar a versiones anteriores en segundos. Por ello Mercurial es ideal para grandes proyectos.

  - **Independiencia de la platforma**

Mercurial fue escrito con pensando en la independencia de las plataformas. Por ello, la mayor parte de Mercurial está escrita en Phyton, con una pequeña porción en C por rasones de rendimiento. Como resultado, están disponibles versiones binarias para todas las plataformas mayores.

  - **Extensible**

La funcionalidad de Mercurial se puede incrementar mediante extensiones, ya sea activando las oficiales que se distribuyen junto con Mercurial o descargando algunas de la red o creando las propias. Las esxtensiones están escritas en Phyton y pueden cambiar el funcionamiento de los comandos básicos, agregar nuevos comandos, etc.

  - **Fácil de Usar**

Mercurial presenta un set de comandos con el que la mayoría de los usuarios de sistemas de control de versiones como Subversion se pueden sentir bastante familiarizados. Acciones potencialmente peligrosas se encuentran disponibles al activar extensiones, por lo que la interfaz básica es fácil de usar, fácil de aprender y dificil de quebrantar.

  - **Open Source**

Mercurial es software gratuito licenciado bajo los términos de la GNU General Public License Version 2 o cualquier version más reciente.

##Tutorial para instalar clientes Linux, MacOS X, y otras variantes de Unix
#Prerequisites


Some Linux distributions fail to include bits of Python's distutils by default, in which case you'll need to install a package usually called python-dev. Suse 9.3 needs python-devel which is not on the installation media: a download from Suse is required. FreeBSD users please see the note below.

## Mercurial needs Python to run:

* If your system does not ship with Python, install it first. Version 2.4 or greater is required.
* You need Python C header files. They may be in package called python-dev or pythonX.Y-dev (where X.Y is the specific version of Python in use, such as 2.4).
* You'll also need a C compiler (such as gcc) and a 3-way MergeProgram.

For the documentation, the prerequisites depend on which version of Mercurial you are trying to install:

* For Mercurial 1.3.x and earlier, building the documentation requires AsciiDoc and xmlto, and the latter in turn requires libxslt.
* Building the documentation for Mercurial 1.4 and later requires Docutils.

You may want to check your operating system distribution for these (and possibly other software required by the prerequisites themselves). If you don't want to build and install the documentation, substitute             `make install-bin` and `make install-home-bin` for `make install` and `make install-home` below.

 
> You can save a lot of time by installing as many prerequisites from system packages as you can. Your distribution will provide information about the dependencies for Python and Mercurial, and although many of these are strictly optional (and, for those supposedly required by Python, unrelated to the normal functioning of Mercurial), some of these are vital. If you are going to build Python, be sure to get the "build dependencies" (the -dev versions of the dependencies) so that Python's configure script can find the header files for various libraries.

> Sites offering an interface to distribution package repositories, such as those for Ubuntu and Debian can be useful in identifying dependencies. The control file in Debian/Ubuntu packages is also a useful source of build dependency information.

> See "Platform Notes" below for recipes covering a range of different environments.

## Unpacking the source

The necessary first step:

```
$ tar xvzf mercurial-<ver>.tar.gz
$ cd mercurial-<ver>
```
##Per-user installation

To install in your home directory (~/bin and ~/lib, actually), run:
```
$ make install-home                     # add PYTHON=/path/to/python2.4-or-newer if necessary
```
To make hg available as a command, run the following shell commands (for bash) and add them to your shell configuration file (such as `.bashrc` or `.bash_profile`):

```
export PYTHONPATH=${HOME}/lib/python
export PATH=${HOME}/bin:$PATH
```

On some 64-bit systems (but not all), you'll need to use lib64 instead of lib in PYTHONPATH. The rule of thumb is that if /usr/lib64 exists, use lib64, otherwise lib. Besides being conservative for your own system, if you are putting up Mercurial to manage a web site or application that is being hosted for you by an ISP, this is likely the method which will least conflict with your host's environment.


>On some systems, a remote, interactive login via ssh will not cause .bashrc to be invoked. It may therefore be appropriate to specify environment variable definitions in your .bash_profile instead (or ensure that your .bash_profile sources your .bashrc appropriately).

>This behaviour is explained in the bash manual page: for an "interactive login shell", bash reads from the user's .bash_profile, .bash_login, or .profile instead of .bashrc (which is read for "an interactive shell that is not a login shell" or "when it is being run by the remote shell daemon"). This seems to contradict the behaviour for remote logins via rsh where .bashrc does get read.

>For hg operations directly acting on remote repositories over SSH (instead of activities involving an interactive login and actually typing the commands in a remote shell), the remote .bashrc file should be invoked as part of the login process. Thus it makes sense to configure paths for Mercurial in this file and reference it in the other configuration files.

>Unfortunately, some combinations of OpenSSH and bash will not cause .bashrc to be invoked (for reasons discussed in this thread). See guidance in the FAQ for workarounds.

##System-wide installation

To install system-wide, you'll need **root** privileges.


`$ make install`

By default, Mercurial is installed under /usr/local, and on some systems an adjustment to the PATH environment variable may be required:

```
$ export PATH=${PATH}:/usr/local/bin                                     # assumes no older hg exists in the standard path

```
If Python does not reside under `/usr/local`, an adjustment to the PYTHONPATH environment variable is necessary. For example, for Python 2.5:

```
$ export PYTHONPATH=/usr/local/lib/python2.5/site-packages:${PYTHONPATH} # bash/ksh syntax
```

If the default python is older than 2.4, use the `PYTHON` option:

```
$ make install PYTHON=/path/to/python2.4
```
###Changing the prefix

With this method, the addition of the `PREFIX` option will keep the Mercurial libraries out of /usr/local and put them instead where the prefix specifies similar to the way that install-home above keeps Mercurial local to a user in the per-user-installation. For example:

```
$ make install PREFIX=/var/hg
```

The `PYTHONPATH` and `PATH` will also need to be appropriately adjusted if `PREFIX` option is used.

For instance, using Python 2.5, and with `PREFIX=/var/hg`, you will need to set `PYTHONPATH` as follows in your environment:

```
$ export PYTHONPATH=/var/hg/lib/python2.5/site-packages:${PYTHONPATH} # bash/ksh syntax

```
Alternatively, you can also create a wrapper script that sets the `PYTHONPATH` variable, regardless of the user's environment:

```
#!/bin/sh
mv /var/hg/bin/hg /var/hg/bin/hg.py
cat > /var/hg/bin/hg <<\EOF
PYTHONPATH=/var/hg/lib/python2.5/site-packages:${PYTHONPATH}
export PYTHONPATH
exec /var/hg/bin/hg.py "$@"
EOF
```
If `PYTHONPATH` is not correctly set, then `hg debuginstall` will print an error message that says:

```
ImportError: No module named mercurial
```

or

```
abort: couldn't find mercurial libraries in [...]
(check your install and PYTHONPATH)
```

##Build directory installation

If you'd like to run development versions of Mercurial directly out of the Mercurial source distribution directory, do the following:


`$ make local`

This will build Mercurial's extensions in-place. Then, simply make a symbolic link to the hg script from a directory in your path.

###Some notes on the C compiler

The C compiler is used for compiling Mercurial's extensions written in C.

Sometimes, Python (actually distutils) may be calling a different C compiler (usually the one used for compiling Python itself) than the one installed on your system. In this case, you can try set the environment variable CC to tell Python to use your favourite C compiler.

With Python 2.4, you may want to set the environment variable LDSHARED for generating shared objects on some platforms.

##Testing a new install

And finally:

```
$ hg debuginstall   # sanity-test the install
Checking encoding (UTF-8)...
Checking extensions...
Checking templates...
Checking patch...
Checking merge helper...
Checking commit editor...
Checking username...
No problems detected
```
If you get complaints about missing modules, you probably haven't set PYTHONPATH correctly.

##Platform Notes

###Fedora

**Fedora 18 (Spherical Cow)**

In order to install mercurial on Fedora 18, you can run the command below:


`$ sudo yum install mercurial`

###FreeBSD

FreeBSD provides the Ports System to easily install and manage applications. To install mercurial on FreeBSD, use the port (typically found in `/usr/ports/devel/mercurial`), or install and use the `portinstall` tool. Read Updating FreeBSD Ports to make certain you have the most recent ported version of mercurial and all dependent packages.

###NetBSD

NetBSD's pkgsrc system provides a package for mercurial in `pkgsrc/devel/mercurial`. To install it, run:

```
$ cd /usr/pkgsrc/devel/mercurial
$ make install
```
See the pkgsrc documentation for more information on pkgsrc, and how to get, update and use it.

###OS X

For Mercurial 1.4 and later, building the documentation requires Docutils. This can be installed via macports:


`$ sudo port install py26-docutils`

For Mercurial 1.3.x and earlier, source installation requires AsciiDoc and xmlto in order to build documentation. These are easy to install via fink or macports:

fink:

```
$ sudo apt-get install asciidoc xmlto # get the latest binary
$ fink install asciidoc xmlto # build from source
```
macports:


`$ sudo port install asciidoc xmlto`

Do one of these before building mercurial.

For some people on OS X 10.5, Mercurial fails to run with an error similar to the following:

```
Traceback (most recent call last):
  File "/opt/local/bin/hg", line 18, in <module>
    mercurial.util.set_binary(fp)
  File "/opt/local/lib/python2.5/site-packages/mercurial/demandimport.py", line 74, in __getattribute__
    self._load()
  File "/opt/local/lib/python2.5/site-packages/mercurial/demandimport.py", line 46, in _load
    mod = _origimport(head, globals, locals)
  File "/opt/local/lib/python2.5/site-packages/mercurial/util.py", line 93, in <module>
    _encoding = locale.getlocale()[1]
  File "/opt/local/Library/Frameworks/Python.framework/Versions/2.5/lib/python2.5/locale.py", line 462, in getlocale
    return _parse_localename(localename)
  File "/opt/local/Library/Frameworks/Python.framework/Versions/2.5/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: UTF-8
```
This appears to be due to the version of Terminal that comes with OS X 10.5 setting the value of the environment variable LC_CTYPE to a bad value, causing Python to throw. You can work around this problem either by going to "Terminal > Preferences... > Settings" and unchecking the option "Set LANG environment variable on startup", or else you can set the environment variables LC_ALL and LANG to appropriate values in your ~/.profile (e.g. add export LC_ALL=en_US.UTF-8 and export LANG=en_US.UTF-8). For more information on the LC_* and LANG variables see man locale.

###Ubuntu

**10.04 LTS Lucid Lynx**

In order to run mercurial built from source on Ubuntu 10.04 LTS Lucid Lynx, if you have previously installed the mercurial package with:


`$ sudo apt-get install mercurial`

or using the synaptic package manager, then you will need to remove it and the mercurial-common package installed automatically as a dependency. You can do so with the following commands:

```
$ sudo apt-get remove mercurial --purge
$ sudo apt-get autoremove   # will delete the now unused mercurial-common
```
You can also explicitly remove the mercurial-common package like this:


`$ sudo apt-get remove mercurial-common --purge`

If you fail to remove mercurial-common, then you will get an error when you attempt to run hg about a missing module which will mimic not having python-dev installed. (ie osutil module not being found).

####6.06 LTS Dapper Drake

In order to build mercurial on Ubuntu Dapper 6.06, it is first necessary to install gcc, the standard libraries, and the Python header libraries. This can be done with the following command:


`sudo apt-get install build-essential gcc python-dev`

For generating documentation (done during the installation) you will also have to install the AsciiDoc and xmlto packages (for Mercurial 1.3.x and earlier):


`sudo apt-get install asciidoc xmlto`

###SUSE/SLES

In order to build the inotify hgext on SUSE/SLES you may have to edit `_inotify.c` and change the include line for `inotify.h` from:

```
#include <sys/inotify.h>
```

to:


`#include <linux/inotify.h>`

#### OpenSUSE 13.2, OpenSUSE Tumbleweed and openSUSE 42.1 Milestone 2


`sudo zypper install mercurial`

###Arch

Arch has made Python 3 the default system Python. Python 2 is now as /usr/bin/python2. This breaks Mercurial's build process. Here's how to build on Arch:

`PYTHONPATH=`python2 -c 'import sys; sys.stdout.write(":".join(sys.path))'` make local PYTHON=python2`

##Solaris

Here's an example on installing Mercurial on Solaris 2.6 with ActiveState Python 2.4.1 (compiled with Sun CC) and GCC 2.95.3:


`$ CC=gcc LDSHARED='gcc -G' python setup.py install`

In our example, the -G option tells GCC to generate shared objects on Solaris, which is equivalent the -shared option on some other platforms. See GCC's manpage for more information on this.

`- I` installed it via make install-home, but I had to do some gcc calls myself (it didn't take -xarch and -x03). -ArneBab

##Solaris 10 (Sparc)

Initially had some issues attempting to use the sunfreeware packages. The version of Python available from there didn't seem to have md5 enabled. Please note that I'm a bit of a novice with Solaris so if someone knows better then please ammend this note - MichaelAnthon


1. Ensure that the following packages are installed
    * SUNWopenssl-include
    * SUNWopenssl-libraries
    * SUNWzlib
    * SMCgcc and SMClgcc346 (I had to upgrade to the 3.4.6 version before it would compile cleanly)
 

2. Build python (using gcc from /usr/sfw and the Solaris assembler and linker from /usr/ccs and libraries from /usr/sfw/lib/, /usr/lib and /usr/local/lib)


    ```
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/sfw/lib/:/usr/lib:/usr/local/lib
    export PATH=$PATH:/usr/ccs/bin:/usr/sfw/bin
    ./configure --libdir=/usr/sfw/lib/ --libdir=/usr/lib --libdir=/usr/local/lib --includedir=/usr/sfw/include --includedir=/usr/include --includedir=/usr/local/include
    make
    make install (as root)
    ```

3. Install setuptools from http://pypi.python.org/pypi/setuptools ( /!\ at this point I had to make a symlink from /usr/bin/python to /usr/bin/python2.6, not sure if the python install SHOULD have done that for me)

4. Install Mercurial

`/usr/local/bin/easy_install -U mercurial`


##Comandos
El programa ejecutable de Mercurial se llama hg. Cada comando de Mercurial comienza por hg, seguido de un nombre de comando, seguido de posibles opciones y argumentos oportunos.

En principio se puede teclear hg en la línea de comandos, y el programa debería mostrar un resumen de la ayuda de los comandos.

Para saber que versión de Mercurial se está ejecutando, teclear:
```
 $ hg version
 Mercurial version fa3578bfafbf+20050629

 Copyright (C) 2005 Matt Mackall <mpm@selenic.com>
 This is free software; see the source for copying conditions.
 There is NO warranty; not even for MERCHANTABILITY
 or FITNESS FOR A PARTICULAR PURPOSE
```
###Clonar
La forma más fácil de comenzar con Mercurial es usar un repositorio que ya contiene algunos ficheros y alguna historia previa.

Para hacer esto, se utiliza el comando clone. Esto hace un clon de un repositorio; se hace una copia completa de otro repositorio de manera que tenemos nuestra propia copia local y privada para trabajar con ella.

```
 $ hg clone http://www.selenic.com/repo/hello hola-mio
```
Si todo fue bien, el comando clone no muestra ninguna salida. Ahora debemos encontrar un subdirectorio llamado hola-mio en nuestro directorio actual:

```
 $ ls
 hola-mio
```
Dentro del directorio hola-mio, encontraremos algunos ficheros:
```
 $ ls hola-mio
 hello.c  Makefile
```
Estos ficheros son copias exactas de los ficheros en el repositorio que acabamos de clonar.

###Primeros Cambios
Nos encontramos dentro de nuestro repositorio hola-mio, el cual clonamos en SpanishTutorialClone.

El aislar cada línea de desarrollo distinta en un repositorio separado es una buena práctica habitual en Mercurial. Esto previene que se mezcle código no relacionado entre si, y hace más fácil testear partes del proyecto una a una. Comenzaremos siguiendo este modelo.

Nuestro objetivo inicial será que el programa "hello, world" ("hola, mundo") imprima otra línea de salida. Primero clonaremos nuestro repositorio hola-mio.

```
 $ cd ..
 $ hg clone hola-mio hola-mio-nueva-salida
```
De nuevo, este comando no muestra nada si todo va bien.

Nota: Observar que hemos dado a nuestro nuevo repositorio un nombre descriptivo, identificando básicamente el propósito del repositorio. Puesto que hacer un clon de un repositorio en Mercurial es muy eficiente, podemos rápidamente acumular muchos repositorios ligeramente diferentes. Si a dichos repositorios no les damos nombres descriptivos, perderemos rápidamente la habilidad de saber de qué tratan cada uno de ellos.

Ahora es el momento de hacer un cambio en el nuevo repositorio. Vayamos al directorio de trabajo (WorkingDirectory), el cual es simplemente el nombre que le hemos dado al directorio donde se encuentran todos los ficheros:
```

 $ cd hola-mio-nueva-salida
 $ vi hello.c
```
El contenido de hello.c se parece a lo siguiente:
```
 /*
  * hello.c
  *
  * Placed in the public domain by Bryan O'Sullivan
  *
  * This program is not covered by patents in the United States or other
  * countries.
  */

 #include <stdio.h>

 int main(int argc, char **argv)
 {
     printf("hello, world!\n");
     return 0;
 }
```
Editamos main para que imprima una línea de salida extra:

```
 int main(int argc, char **argv)
 {
     printf("hello, world!\n");
     printf("sure am glad I'm using Mercurial!\n");
     return 0;
 }
```
Una vez terminado, cerramos el vi (o nuestro editor favorito) y hemos acabado. Eso es todo. Con esta edición estamos listos para crear un ChangeSet.

Pero, ¿qué ocurre si somos interrumpidos y olvidamos los cambios que acabamos de hacer en el ChangeSet? Para saber esto usamos el comando status.
```

 $ hg status
 M hello.c
```
Esta salida nos dice que el fichero hello.c tiene un cambio listo para incluir en un ChangeSet.

El acto de crear un nuevo ChangeSet se denomina Commit (de "cometer" cambios). Realizamos un Commit utilizando el comando commit:
```

 $ hg commit
```
Esto abrirá nuestro editor de texto y nos presentará unas cuantas líneas un poco crípticas en él:

```
 <esta línea estará vacía>
 HG: manifest hash 0d66196b08b861878228219d46258f088092286e
 HG: changed hello.c
```
La primera línea estará vacía, la segunda contendrá un número de hash bastante largo, y las líneas que siguen identifican los ficheros que van en este ChangeSet.

Para hacer el Commit del ChangeSet, debemos describir las razones de los cambios. Esto se denomina normalmente el comentario del ChangeSet. En este caso escribamos algo como lo siguiente:


 Se expresa en inglés y con júbilo la existencia de Mercurial
Después cerramos el editor y (como debe ser de esperar) el comando de commit no muestra ninguna salida.

¿Que nos dice ahora el comando de status?
```

 $ hg status
```
¡Nada! Nuestros cambios han sido incluidos en el ChangeSet, por tanto nuestro Tip coincide ahora con el contenido de nuestro directorio de trabajo. ¿Significa eso que nuestro nuevo commit se mostrará ahora en el historial de cambios?

```
 $ hg log
 changeset:   3:da99cce05957f7a62b74d345fd55365dc33109f0
 tag:         tip
 user:        bos@camp4.serpentine.com
 date:        Wed Jun 29 12:58:37 2005
 summary:     Se expresa en inglés y con júbilo la existencia de Mercurial
```
¡Efectivamente, ahí está! Acabamos de crear y hacer un commit de un ChangeSet.

Como se discutió en SpanishTutorialClone, el nuevo ChangeSet únicamente existe en este repositorio. Esto es un elemento crítico del modo en que funciona Mercurial.

Para compartir los cambios realizados, debemos continuar en SpanishTutorialShareChange.

**Preparación de Mercurial**

Como primer paso, debemos decirle a Mercurial nuestro nombre. Para ello abre con un editor de texto el archivo ```~/.hgrc``` (o ```mercurial.ini``` en tu directorio principal en Windows) y agregar la sección ui (*user interaction*) con tu nombre de usuario:

```
[ui]
username = Mr. Johnson <johnson@smith.com>
```

**Inicializa el proyecto**

<!--- --->
Agrega un nuevo folder en el que deseas trabajar:
```
$ hg init project
```
**Poner archivos en seguimiento**

Inntroducir el folder del proyecto, crear algunos archivos, agregarlos todos y confirmarlos.
```
$ cd project
$ echo 'print("Hello")' > hello.py
$ hg add
$ hg commit
``` 
(tu editor predeterminado abre, agrega el mensaje de confirmación, guarda y cierra el archivo correspondiente.)

Además puedes agregar archivos específicos en lugar de todos los archivos en el directorio. Mercurial pondrá en seguimiento solo éstos archivos e ignorará los otros. El siguiente ejemplo le indica a Mercurial que agregue todos los archivos con los nombres que empiecen con "file0" así como los archivos file10, file11 and file12.
```
$ hg add file0* file10 file11 file12
```
**Guardar los cambios**

Después de modificar archivos en seguimiento, verifica qué archivos fueron modificados, cuales fueron agregados o removidos, y cuales aún no se encuentran en seguimiento:
```
$ hg status
```

Para ver los cambios exactos:
```
$ hg diff
```

Confirmar los cambios:

```
$ hg commit
```
**Copiar y mover archivos**

Cuando copias o mueves archivos, debes decirle a Mercurial que copie o mueva el archivo por ti, de forma que pueda hacer el seguimiento de las relaciones entre archivos.

Recuerda confirmar después de mover o copiar.
```
$ hg cp hello.py copy
$ hg mv hello.py target
$ hg diff # see the changes
$ hg commit
```

**Checar tu historial**

Puedes checar tu historial con el comando:
```
$ hg log
```
Esto imprime una lista de cambios junto con su fecha, el usuario que los confirmó y el mensaje de confirmación.

**Verificar una revision anterior**

En algún momento del desarrollo de un proyecto, podrías querer regresar en el historial para hacer cambios directamente, por ejemplo, porque un cambio anterior introdujo un *bug* y quieres repararlo cuando ocurrió.

Para ver una versión previa de tu código, puedes usar **update**. Vamos a asumir que quieres ver la revisión 1.


```
$ hg update 1
```
Ahora tu código regresó a la revisión 1, el segundo **commit** (Mercurial inicia contando en el 0). Para checar si realmente tienes esa revisión, puedes usar identify -n.
```
$ hg identify -n
```
Para acutalizar a la revision mas actual, puedes usat "tip" como nombre de revision.
```
$ hg update tip
```
**Corregir errores en versiones anteriores**

Cuando estás buscando un bug en una revision anterior tienes dos opciones: arreglarlo en el código actual, o regresar en el historial y buscar arreglar el código exactamente donde insertaste el bug, lo cual genera un historial limpio.

Para hacer esto de una forma correcta, primero puedes actualizar la revision anterior, arreglar el bug y hacer un commit. Después une esta revision y haz commit del merge. No te preocupes, merging en Mercurial is rápido y sin dolor, como tú podrás verlo en un instante.

Ahora asumamos que el bug fue introducido en la revision 1.
```
$ hg update 1
$ echo 'print("Hello Mercurial")' > hello.py
$ hg commit
```
Ahora el arreglo esta guarda en el historial. Solo necesitamos unir esto con le version actual de tu código.
```
$ hg merge
```
Si hay conflictos usa hg resolve - tambien te dira que hacer en caso de que existan conflictos.

Primero lista los archivos con conflictos
```
$ hg resolve --list
```
Luego resuelve uno por uno e intenta unir otra vez
```
$ hg resolve conflicting_file
```
(fix it by hand, if necessary)

Marca el archivo como resuelto
```
$ hg resolve --mark conflicting_file
```
Haz un commit del merge tan pronto como hayas corregido todos los conflictos. Este paso is tambien necesario cuando no hay conflictos!
```
$ hg commit
```
A estas alturas, puedes arreglar y unir todo tu trabajo, y solo programa. Adicionalmente el historial muestra claramente donde arreglaste el bug y simepre podrás checar donde estaba el bug. 
