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
Una vez instalado LaTeX podemos crear un primer documento para aprender los comandos
más importantes.

En primer lugar es necesario indicar el tipo de documento que queremos crear. Esto se
indica mediante la línea de código:
```tex
\documentclass{article}
```

En este caso hemos creado un documento corto con la clase "article". También existen
otras opciones como, por ejemplo, `"report"` o `"book"`, que son adecuadas para
documentos largos.
