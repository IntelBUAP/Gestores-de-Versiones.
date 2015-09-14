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
