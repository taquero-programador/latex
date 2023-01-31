# LaTeX

## ¿Qué es LaTeX?
LaTeX es un sistema de preparación de documentos que facilita la escritura de
documentos cientifícos y ténicos. Alguna de sus principales ventajas son la **alta
calidad** de los documentos en general, la posililidad de escribir fórmulas matemáticas
complejas y su método para gestionar las referencias cruzadas en un documento.

La característica principal que diferencia LaTeX de otras herramientas habituales para
escribir documentos (por ejemplo, Word) es que LaTeX se basa en diferenciar entre el
contenido y el formato con el que se presenta el contenido.

En procesadores como Word veremos directamente en la pantalla la forma y el formato del
documento que creamos. En LaTeX, en cambio, añadimos el contenido junto con pequeñas 
instrucciones escritas en forma de etiquetas que indican el formato de las distintas 
secciones. Para obtener obtener el documento en su estado final es necesario un proceso
de compilado que interpreta las instrucciones de formato que hemos introducido.

Aunque según para qué tipo de documentos esto pueda presentar un inconveniente, la
realidad es que es de gran utilidad para poder trabajar con el contenido de un 
documento sin preocuparse por los problemas asociados a su formato. En los procesadores
de texto habituales, cuando un documento alcanza una longitud considerable es cuando
empiezan los problemas: la velocidad de carga aumenta, aparecen saltos de página
aleatorios, las referencias internas se rompen, etc. Todos estos problemas son de
última instancia, una consecuencia de trabajar simultáneamente los aspectos del
contenido y los aspectos del formato.

Esto puede evitarse con LaTeX ya que se trabaja siempre con un documento sencillo sin
formato. Todas las instrucciones de formato se indican en las etiquetas adecuadas y se
interpretan únicamente cuando compilamos el documento. Además, LaTeX gestiona
automáticamente ciertos aspectos importantes de un documento como pueden ser los
índices de contenido, las listas de bibliografía o las referencias cruzadas a imágenes,
ecuaciones, etc.

## Instalación (Linux)
1. La distribución TeXLive es la distribución TeX por defecto en la mayoría de sistemas
Linux. Para evitar problemas, lo mejor es hacer una instalación completa:
```bash
sudo apt install textlive-full -y
```

2. Instalar un editor de textos para LaTeX:
```bash
sudo apt install texmaker -y
```

Para VIM:
```conf
Plug 'lervag/vimtex'

# config
let g:vimtex_view_method = 'zathura'
let g:vimtex_view_general_viewer = 'okular'
let g:vimtex_view_general_options = '--unique file:@pdf\#src:@line@tex'
let g:vimtex_compiler_method = 'latexrun'
let maplocalleader = ","
```

3. Si instalar un editor específico para LaTeX normalmente tendrás la opción de
compilar tus archivos a `.pdf` directamente desde la GUI. En caso contrario también
es posible compilar directamente desde la terminal:
```bash
pdflatex file.txt
```

## Crear un documento

#### Declaración de la clase de documento
Una vez instalado LaTeX podemos crear un primer documento para aprender los comandos
más importantes.

En primer lugar es necesario indicar el tipo de documento que queremos crear. Esto se
indica mediante la línea de código:
```tex
\documentclass{article}
```

En este caso hemos creado un documento corto con la clase `"article"`. También existen
otras opciones como, por ejemplo, `"report"` o `"book"`, que son adecuadas para
documentos largos.

Una vez declarado el tipo de documento, debemos indicar el comienzo del contenido
mediante las etiquetas:
```tex
\begin{document}
    Mi primer documento en LaTeX!
\end{document}
```

Estas dos etiquetas delimitan el contenido de nuestro contenido. Es importante escribir
siempre todo el contenido entre estas dos etiquetas. De lo contrario, será imposible
compilar el documento.

Una opción es escribir las ecuaciones junto con el texto, sin cambiar necesariamente
de línea. Esto se consigue escribiendo las ecuaciones entre los símbolos de `$`.
Por ejemplo:
```tex
La expresi\'on m\'as importante de la teor\'ia de la relatividad es $E=mc^2$.
```

Si en cambio queremos escribir la ecuación centrada en una línea aparte, debemos
escribir la ecuación entre `$$`. Por ejemplo:
```tex
La expresi\'on m\'as importante de la teor\'ia de la relatividad es $$E=mc^2$$.
```

#### Declaración de entornos
Dentro de un documento es habitual definir distintos entornos para crear bloques de
contenido que LaTeX debe interpretear de forma distinta. Los entornos se definen
siempre mediante las etiquetas:
```tex
\begin{document}
\end{document}
```

Como hemos visto, el entorno principal de un documento se conoce como `document`.
Dentro del entorno `document`, es posible definir subentornos según las funciones
deseadas. Por ejemplo, dentro del entorno `document`, podemos abrir otro entorno para
centrar un texto:
```tex
\begin{document}
    \begin{center}
        Este texto aparece centrado
    \end{center}
\end{document}
```

Otro ejemplo consiste en definir un entorno `itemize` para crear una lista:
```tex
\begin{document}
    Aqu\'i empieza una lista:
    \begin{itemize}
        \item Primer elemento de la lista
        \item Segundo elemento de la lista
    \end{itemize}
\end{document}
```

#### Preámbulo de un documento
La sección entre la declaración de un documento y el comienzo del contenido se conoce
como preámbulo.

En esta sección puede incluirse instrucciones adicionales para trabajar con el
documento. En particular, es recomendable añadir en esta sección información sobre el
documento. Por ejemplo, el título, el autor y la fecha.
```tex
\title{Mi primer documento}
\date{2018-03-01}
\author{Bender Doblador}
```

Esta información no aparecerá en el documento al ser compilada, pero queda guardada y
puede ser utilizada, por ejemplo, para crear una portada.

El preámbulo también es utilizado para cargar paquetes adicionales que añaden
funcionalidades a nuestro documento. Existe un gran número de paquetes que pueden ser
cargados a LaTeX: para crear tablas de contenido, encabezados, símbolos matemáticos,
tablas, etc. La primera vez que utilices un paquete nuevo, el propio programa de LaTeX
que utlices se encargara de instalarlo en tu ordenador para que esté disponible.

Por ejemplo, un paquete de uso habitual en un documento de contenido matemático es
el `amsmath` de la American Mathematical Society. Este paquete puede ser cargado desde
el preámbulo escribiendo:
```tex
\usepackege{amsmath}
```

Incluyendo esta línea en el preámbulo, LaTeX tendrá acceso a más comandos y entornos que
te permitirán escribir fácilmente ecuaciones de mayor complejidad.

También en el preámbulo es recomendable indicar el idioma de escritura del documento
mediante el paquete babel. En caso de escribir el documento en español esto se puede
hacer con el comando:
```text
\usepackege[spanish]{babel}
```

Esta indicación permite a LaTeX tener en cuenta ciertas particularidades del idioma
español. Por ejemplo, es útil para dividir correctamente la palabra a final de la línea
y para tener acceso a alguna expresiones matemáticas es español (e.g. seno -> sen).

También es importante tener en cuenta que, por defecto, LaTeX no acepta algunos
caracteres específicos del español como son, por ejemplo, la ñ o las voales con tilde.
Esto se debe al origen aglosajón de LaTeX.

Para escribir estos caracteres particulares del español hay dos opciones. La primera
consiste en escapara los caracteres con una barra inversa. Así, las letras con tilde
pueden escribirse mediante:
Carácter | Resultado
-- | --
\'a | á
\'e | é
\'i | í
\'o | ó
\'u | ú
\'A | Á
\'E | É
\'I | Í
\'O | Ó
\'U | Ú
\'n | ñ
\'N | Ñ
\"u | ü
\"U | Ü

Esta primera opción es la más recomendable cuando un grupo de personas deben trabajar
con el mismo documento ya que evita inconsistencias entre distintos sistemas.

La seguna opción consiste en cargar un paquete de caracteres que permitan escribir
directamente los caracteres especiales en LaTeX. Una de las opciones más extendidas
es la codificación `utf8`. Esta puede cargarse en un documento mediante:
```tex
\usepackege[utf8]{inputec}
```

Alternativamente, también es posible utilizar la codificación:
```tex
\usepackege[utf8]{inputec}
```

#### Comentarios
Una de las posibilidades que ofrece LaTeX es la de añadir comentarios en medio del
documento. Estos comentarios pueden servir para clarificar el uso de algunos comandos
y no aparecen en el documento compilado.

La forma más rápida de añadir un comentario es escribir el símbolo `%` seguida del
comentario. Por ejemplo, la siguiente línea:
```tex
Esta es una l\'inea de texto % Esto es un comentario
```

En caso de querer escribir comentarios de varias líneas podemos utilizar el entorno
`comment`, que está disponible mediante el comando `comment`:
```tex
\usepackege{comment}
\begin{document}
    \begin{comment}
        Esto es un comentario de distintas líneas. En este caso, todo el texto contenido entre las etiquetas del entorno comment no aparecerán en el documento compilado.
    \end{comment}
\end{document}
```

## Crear una portada
Para crear una portada en un documento de LaTeX puede utilizar dos comandos distintos.

La opción más simple consiste en utilizar el comando `\maketitle`. Solo hace falta
escribir este comando justo después de empezar el entorno `document` para que LaTeX
genere automáticamente un título para el documento. La opción más avanzada y que nos da
más libertad para personalizar una portada en el entorno `titlepage`.

#### Portada con el comando `maketitle`
Hay dos aspectos importantes a tener en cuenta antes de utilizar este comando. En primer lugar, es necesario definir los parámetros necesarios para crear el título en
el preámbulo del documento. Esto incluye definier el título, el autor y la fecha del
documento.

Utilizando este metódo podemos crear un documento con una portada mediante:
```tex
\documentclass{report}
\title{La vuelta al mundo en 80 d\'ias}
\date{2023-01-31}
\author{Bender Doblador}
\begin{document}
    \maketitle
    Contenido
\end{document}
```

En caso de no querer mostrar la fecha es necesario escribir el comando `date` en blanco.

En segundo lugar, es importante tener en cuenta que la clase de documento que
seleccionamos define el formato de título. Utilizando la clase de documento `book` o
`report`, se creará automáticamente una página para la portada al principio del
documento. La clase `article`, en cambio, coloca el título, autores y fecha en el
espacio superior de la primera página.

También es posible forzar la creación de la portada en una página aparte indicándole
en el comando que define la clase de documento. Esto es posible mediante el parámetro
`titlepage`. Por ejemplo, en un documento de tipo `article`:
```tex
\documentclass[titlepage]{article}
```

#### Portada con el entorno `titlepage`
Para crear una portada más personalizada es recomedable utilizar el entorno `titlepage`
dentro del documento.

Este entorno nos permite definir los elementos que queremos mostrar en la portada,
incluyendo posición, formato, espaciado, etc.

Un ejemplo de portada creada con este entorno es:
```tex
\documentclass{report}
\begin{document}
    \begin{titlepage}
        \centering
        {\bfseries\LARGE Universidad Superior T\'ecnica \par}
        \vspace{1cm}
        {\scshape\Large Facultad de Ingenier\'ia Industrial \par}
        \vspace{3cm}
        {\scshape\Huge T\'itulo del proyecto \par}
        \vspace{3cm}
        {\itshape\Large Proyecto Fin de Carrera \par}
        \vfill
        {\Large Autor: \par}
        {\Large Nombre Apellidos \par}
        \vfill
        {\Large Junio 2020 \par}
    \end{titlepage}
\end{document}
```

En primer lugar, dentro del entorno `titlepage`, se incluye el comando `\centering`
para indicar que el texto debe mostrarse centrado horizontalmente. Tmabién es posible
alinear el texto a la izquiera con `\raggedright` o a la dereche `\raggedleft`.

En segundo lugar, existen distintas líneas escritas entre llaves. Estas son las
distintas unidades de texto que aparecen en la portada. Estos elementos se escriben
entre llaves para indicar que deben mostrarse con el mismo estilo. En este caso el
estilo incluye definir el tipo de letra y tamaño.

Los tipos de letra utilizados en esta portada son mayúsculas pequeñas (small caps) con
`\scshape`, negrita (boldface) con `\bfseries` y cursiva (italic) con `\itshape`.
Aparte de estas tres posibilidades existen otros tipos de letras.

El tamaño de letra se ha especificado con los comandos `\large`, `\Large` y `\Huge`.

Cada línea de texto termina con el comando `\par`. Esto indica que debe crearse un
nuevo párrafo. De lo contrario, LaTeX generaría todos los elementos de texto en una
sola línea.

Por último, exiten también una serie de comando para indicar el espacio vertical entre
los distintos elementos. Uno de ellos es `\vspaces{longitud}` que crear un espacio
vertical con la longitud especificada. También existen la opción de utilizar el
comando `\vfill`. Este comado simplemente rellena el espacio para ocupar la página
enter.

#### Insertar una imagen o logo en la portada
En trabajos universitarios es habitual el logo de la universidad en la portada. Esto
puede hacerse exactamente con el mismo procedimiento seguido para añadir una imagen.

En caso de añadir un logo en la parte superior de la portada el código necesario es:
```tex
\documentclass{report}
\usepackage{graphicx}
\begin{document}
    \begin{titlepage}
        \centering
        {\includegraphics[width=0.2\textwidth]{logo}\par}
        \vspace{1cm}
        {\bfseries\LARGE Universidad Superior T\'ecnica \par}
        \vspace{1cm}
        {\scshape\Large Facultad de Ingenier\'ia Industrial \par}
        \vspace{3cm}
        {\scshape\Huge T\'itulo del proyecto \par}
        \vspace{3cm}
        {\itshape\Large Proyecto Fin de Carrera \par}
        \vfill
        {\Large Autor: \par}
        {\Large Nombre Apellidos \par}
        \vfill
        {\Large Junio 2020 \par}
    \end{titlepage}
\end{document}
```

Este caso muestra dos cambios respecto al ejemplo anterior. En primer lugar se añadio
el paquete `graphicx` en el preámbulo.
```tex
\usepackege{graphicx}
```

Este paquete es necesario para poder utilizar los comandos referentes a la inserción
de imágenes.

El comando concreto que inserta la imagen es:
```tex
\includegraphics[width=0.2\textwidth]{logo}
```

Este comando inserta la imagen con el nombre del logo. En este caso es necesario que la
imagen esté guardada en la misma carpeta que el archivo LaTeX. Tamién es posible
indicar la ruta hacia la carpeta donde hemos guardado la imagen. Por ejemplo, si está
dentro de la carpeta imágenes podríamos escribir:
```tex
\includegraphics[width=0.2\textwidth]{Imagenes/logo}
```

Si no indicamos la extensión del archivo LaTeX escogerá automáticamente el archivo con
el nombre indicado que sea compatible.

El comando anterior también incluye un parámetro para indicar la anchura de la imagen.
Existen distintas unidades para indicar la anchura de la imagen. En este caso indicamos
que sea un 20% de la anchura total del texto con `0.2\textwidth`.
