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

To look at a previous version of your code, you can use update. Let's assume that you want to see revision 1.
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
