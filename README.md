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

Icluyendo esta línea en el preámbulo, LaTeX tendrá acceso a más comandos y entornos que
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
