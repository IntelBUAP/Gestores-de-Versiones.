#Introducción a Mercurial


Mercurial es un sistema de control de versiones multiplataforma, para desarrolladores de software. Está implementado principalmente haciendo uso del lenguaje de programación Python, pero incluye una implementación binaria de diff escrita en C. Mercurial fue escrito originalmente para funcionar sobre GNU/Linux. Ha sido adaptado para Windows, Mac OS X y la mayoría de otros sistemas tipo Unix. Mercurial es, sobre todo, un programa para la línea de comandos. Todas las operaciones de Mercurial se invocan como opciones dadas a su programa motor, hg (cuyo nombre hace referencia al símbolo químico del mercurio).


Las principales metas de desarrollo de Mercurial incluyen un gran rendimiento y escalabilidad; desarrollo completamente distribuido, sin necesidad de un servidor; gestión robusta de archivos tanto de texto como binarios; y capacidades avanzadas de ramificación e integración, todo ello manteniendo sencillez conceptual1 Incluye una interfaz web integrada.

El creador y desarrollador principal de Mercurial es Matt Mackall. El código fuente se encuentra disponible bajo los términos de la licencia GNU GPL versión 2, lo que clasifica a Mercurial como software libre.

##Para Linux, MacOS X, y otras variantes de Unix



#Historia
Mackall hizo pública la existencia de Mercurial el 19 de abril de 2005.3 El estímulo que llevó a esto fue el anuncio de Bitmover, publicado anteriormente aquel mismo mes, informando que retirarían la versión gratuita de BitKeeper.

Se había estado usando BitKeeper debido a los requisitos de control de versiones del proyecto del núcleo Linux. Mackall decidió escribir un sistema de control distribuido de versiones como sustituto para usarlo con el núcleo Linux. Este proyecto comenzó aproximadamente al mismo tiempo que otro denominado git, iniciado por el propio Linus Torvalds con objetivos similares.

El proyecto Linux decidió usar Git en lugar de Mercurial. Sin embargo, muchos otros proyectos usan este último.


#Comandos
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
##Clonar
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

##Primeros Cambios
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