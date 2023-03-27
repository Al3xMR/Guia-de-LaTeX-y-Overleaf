> Extraído de [Learn LaTeX in 30 minutes](https://es.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes) de Overleaf y traducido por [@Al3xMR](https://github.com/Al3xMR/).

# Qué es LaTeX

LaTeX (pronunciado “LAY-tek” o “LAH-tek”) es una herramienta para la composición de documentos de apariencia profesional. A diferencia de otros editores de texto como Microsoft Word, LaTeX se basa en la mezcla de texto plano y de comandos LaTeX usados para expresar los resultados tipográficos deseados.

Para producir el documento, el archivo LaTeX es procesado por un software llamado `TeX engine` que usa los comandos incluidos en el archivo de texto para controlar los procesos tipográficos, convirtiendo los comandos LaTeX y el documento de texto en un archivo PDF compuesto profesionalmente. Esto quiere decir que solo se necesita concentrar en el contenido del documento, y la computadora, mediante comandos LaTeX y el motor TeX, se encargará de la apariencia visual y formato.

# Creación de un documento LaTeX

Para crear documentos LaTeX, se hace uso de la herramienta web [Overleaf](https://www.overleaf.com/), de donde iniciando un nuevo proyecto, se puede empezar con un archivo `.tex`.

El formato más básico para un documento es el siguiente:

```latex
\documentclass{article}
\begin{document}
Primer documento. Este es un simple ejemplo, sin
parametros adicionales o paquetes incluídos.
\end{document}
```

La primera línea del código, `\documentclass{article}`, declara el tipo de documento, es decir, su clase, la cual controla la apariencia general del documento. Distintos tipos de documento requieren distintas clases. Por ejemplo, una hoja de vida requerirá una clase diferente que un documento científico que usaría la clase estándar `article`.

Existen muchos otras clases de documentos, entre estos `book` y `report`. Para ver una lista de muchas clases de documentos posibles, visitar el catálogo en [CTAN](https://www.ctan.org/topic/class).

Una vez establecida la clase del documento, el contenido, también conocido como el cuerpo del documento, se escribe entre las etiquetas `\begin{document}` y `\end{document}`.

# El preámbulo de un documento

Corresponde al encabezado. Todo lo que se encuentra antes del cuerpo del documento corresponde al preámbulo, que actúa como la sección de configuración del documento.

Dentro del preámbulo se define la clase junto a especificaciones como el lenguaje que será usado cuando sed escriba el documento; cargar paquetes que se buscarían usar y es donde se aplicarán otro tipo de configuraciones.

El preámbulo mínimo se vería de esta manera:

```latex
\documentclass[12pt, letterpaper]{article}
\usepackage{graphicx}
```

donde `\documentclass[12pt, letterpaper]{article}` define la clase general del documento. Parámetros adicionales, los cuales deben ser separados por comas, se incluyen en corchetes y se usan para configurar esta instancia de la clase `article`.

En este ejemplo, `12pt` establece el tamaño de la fuente y `letterpaper` establece el tamaño del documento.

Para tamaño de fuente se puede usar `9pt`, `11pt`, `12pt`, pero si se deja vacío, el valor predeterminado es de `10pt`. Asi también, para el tamaño del documento, otros posibles valores son `a4paper` y `legalpaper`.

La línea del preámbulo `\usepackage{graphicx}` es un ejemplo de carga de un paquete externo para aumentar las capacidades de LaTeX, permitiéndole importar archivos de gráficas externos.

# Incluyendo información de título, autor y fecha

Para añadir título, autor y fecha a nuestro documento, se requiere tres líneas más en el preámbulo (no en el cuerpo principal del documento). Esas líneas son:

- `\title{Mi primer documento LaTeX}`: título del documento
- `\author{Kevin Martinez}`: aqui se escribe el nombre de el/los autor(es) y, opcionalmente, el comando `\thanks` dentro de las llaves:
    - `\thanks{Financiado por el equipo de Overleaf.}`: puede ser añadido después del nombre del autor, dentro de las llaves para el comando `author`. Se añadirá un superíndice y una nota de pie de página para agradecer a una institución en el artículo.
- `\date{March 2023}`: Se puede ingresar la fecha manualmente o usar el comando `\today` para ingresar la fecha actual cada vez que el documento es compilado.

Con estas líneas, el preámbulo debería verse algo así:

```latex
\documentclass[12pt, letterpaper]{article}
\title{Mi primer documento LaTeX}
\author{Kevin Martinez\thanks{Financiado por el equipo de Overleaf.}}
\date{March 2022}
```

Para componer el título, autor y fecha se debe usar el comando `\maketitle` dentro del cuerpo del documento:

```latex
\begin{document}
\maketitle
Hemos agregado un titulo, autor y fecha a nuestro primer documento!
\end{document}
```

Es decir, la unión del preámbulo y el cuerpo deberían producir un documento completo que puede ser abierto en Overleaf:

```latex
\documentclass[12pt, letterpaper]{article}
\title{Mi primer documento LaTeX}
\author{Kevin Martinez\thanks{Financiado por el equipo de Overleaf.}}
\date{March 2022}
\begin{document}
\maketitle
Hemos agregado un titulo, autor y fecha a nuestro primer documento!
\end{document}
```

Este ejemplo produce el siguiente archivo saliente:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled.jpeg" width=500px></div>


# Añadiendo comentarios

Un comentario LaTeX es una sección de texto que no será añadida al documento ni lo afectará de ninguna manera. Es usado para notas de “quehaceres pendientes”; incluir notas para explicar; proveer explicaciones en línea de macros o comentar líneas o secciones de código en depuración.

Para hacer un comentario en LaTeX, simplemente se escribe un símbolo `%` al inicio de una línea, como se ve en el código de a continuación usado en el ejemplo de arriba.

```latex
\documentclass[12pt, letterpaper]{article}
\title{Mi primer documento LaTeX}
\author{Kevin Martinez\thanks{Financiado por el equipo de Overleaf.}}
\date{March 2022}
\begin{document}
\maketitle
Hemos agregado un titulo, autor y fecha a nuestro primer documento!

% Esta linea es un comentario. No será mostrada en el documento.
\end{document}
```

Este ejemplo producirá una salida idéntica a la mostrada en el ejemplo de arriba.

# Negrita, itálica y subrayado

Ahora, se hechará un vistazo a algunos comandos de formato de texto:

- **Negrita**: texto en negrita en LaTeX es aplicado usando el comando `\textbf{...}`.
- *Itálica*: texto italizado es aplicado usando el comando `\textit{...}`.
- Subrayado: para subrayar texto se usa el comando `\underline{...}`.

Otro comando muy útil es `\emph{argument}`, cuyo efecto en “argumento” depende del contexto. Dentro de texto normal, el texto enfatizado es italizado, pero este comportamiento es revertido si se usa dentro de un texto italizado. Algunos paquetes como `Beamer` cambian el comportamiento del comando `\emph`.

Por ejemplo:

```latex
Algunos de los mejores \emph{descubrimientos} en la ciencia fueron hechos por accidente.
\textit{Algunos de los mejores \emph{descubrimientos} en la ciencia fueron hechos por accidente.}
```

Esto produciría el texto:
Algunos de los mejores *descubrimientos* en la ciencia fueron hechos por accidente.
*Algunos de los mejores* descubrimientos *en la ciencia fueron hechos por accidente.*

# Añadir imágenes

Para añadir imágenes a un documento LaTeX hay que tener en cuenta que las imágenes deben ser cargadas al proyecto de Overleaf.

El siguiente ejemplo muestra como incluir una imagen:

```latex
\documentclass{article}
\usepackage{graphicx} %Paquete LaTeX para importar gráficos
\graphicspath{{images/}} %configurando el paquete graphicx

\begin{document}
El universo es inmenso y parece ser 
homogeneo, en una escala enorme, 
dondequiera que veamos.

% El comando \includegraphics es
% proporcionado (implementado) por el
% paquete graphicx
\includegraphics{universe}

Hay una imagen de una galaxia aqui arriba.
\end{document}
```

Este ejemplo produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled.png" width=500px></div>

Importar gráficos a un documento LaTeX requiere de un paquete añadido que provee comandos y características requeridas para incluir archivos externos de imágenes. El ejemplo de arriba carga el paquete `graphicx` que, entre otros comandos, provee `\includegraphics{...}` para importar gráficos y `\graphicspath{...}` para advertir a LaTeX dónde están localizados los gráficos.

Para usar este paquete, se deberá incluir la línea `\usepackage{graphicx}` en el preámbulo del documento.

En el ejemplo, el comando `\graphicspath{{images/}}` informa a LaTeX que las imágenes están almacenadas en una carpeta llamada `images`, que está contenida en el directorio actual.

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%201.png" width=500px></div>

Notas:

- A pesar de que el nombre completo del archivo, incluyendo la extensión, es soportado por el comando `\includegraphics`, es considerado una mejor practica omitir la extensión porque eso permitirá a LaTeX buscar todos los formatos soportados.
- Generalmente, el nombre del archivo de gráfico no debería contener espacios en blanco o puntos múltiples; también es recomendado usar letras minúsculas para la extension del archivo cuando se cargan imágenes a Overleaf.

## Leyendas, etiquetas y referencias

Las imágenes pueden tener leyendas, etiquetas y referencias por medio del entorno de figura, así como se ve aquí abajo:

```latex
\documentclass{article}
\usepackage{graphicx}
\graphicspath{{images/}}

\begin{document}

\begin{figure}[h]
		\centering
		\includegraphics[width=0.75\textwidth]{mesh}
		\caption{Una buena trama.}
		\label{fig:mesh1}
\end{figure}

Como se puede obsrevar en la figura \ref{fig:mesh1}, 
la funcion crece cerca del origen. Este ejemplo esta 
en la página \pageref{fig:mesh1}.

\end{document}
```

El ejemplo mostrado produce la siguiente salida:
<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%202.png" width=500px></div>

Hay muchos comandos notorios en este ejemplo:

- `\includegraphics[width=0.75\textwidth]{mesh}`: Esta forma de `\includegraphics` le dice a LaTeX que establezca el ancho de la figura en el 75% del ancho del texto, cuyo valor está almacenado en el comando `\textwidth`.
- `\caption{Una buena tama.}`: Como su nombre sugiere, este comando establece la leyenda de la figura que puede ser posicionada encima o debajo de la figura. Si se crea una lista de figuras esta leyenda sera usada en esa lista.
- `\label{fig:mesh1}`: Para referenciar a esta imagen dentro de un documento se le asigna una etiqueta usando el comando `\label`. La etiqueta se usa para generar un numero para la imagen y, combinada con el siguiente comando, permitirá referenciar hacia esta.
- `\ref{fig:mesh1}`: Este código será sustituido por el numero correspondiente a la imagen referenciada.

Las imágenes incorporadas en un documento LaTeX deben ser colocadas dentro de un entorno de figura o similar, de modo que LaTeX puede posicionar automáticamente la imagen en una localización formidable dentro del documento.

# Creando listas en LaTeX

Se pueden crear diferentes tipos de lista usando entornos, que son usados para encapsular el código LaTeX requerido para implementar un tipo especifico de composición de características. Un entorno empieza con `\begin{nombre-de-entorno}` y termina con `\end{nombre-de-entorno}`, donde `nombre-de-entorno` debe ser `figure`, `tabular` o cualquiera de los tipos de listas: `itemize` para listas sin orden o `enumerate` para listas ordenadas.

## Listas sin orden

Las listas sin orden son producidas por el entorno `itemize`. Cada lista debe ser precedida por el comando `\item`, como se muestra a continuación:

```latex
\documentclass{article}
\begin{document}
\begin{itemize}
	\item Las entradas individuales son indicadas con un punto negro llamado viñeta.
	\item Las entradas pueden ser de cualquier tamaño.
\end{itemize}
\end{document}
```

Esto producirá la siguiente salida:

- Las entradas individuales son indicadas con un punto negro llamado viñeta.
- Las entradas pueden ser de cualquier tamaño.

## Listas ordenadas

Sigue la misma sintaxis que las listas sin orden, pero son creadas usando el entorno `enumerate`.

```latex
\documentclass{article}
\begin{document}
\begin{enumerate}
	\item Este es la primera entrada en nuestra lista.
	\item Los números de la lista incrementarán con cada entrada que añadamos.
\end{enumerate}
\end{document}
```

Esto producirá la siguiente salida:

1. Este es la primera entrada en nuestra lista.
2. Los números de la lista incrementarán con cada entrada que añadamos.

# Añadiendo matemática a LaTeX

Una de las principales ventajas de LaTeX es la facilidad con la que las expresiones matemáticas pueden escribirse. LaTeX provee dos modos de escritura para componer matemáticas:

- `inline` usado para escribir formulas que son parte de un párrafo.
- `display` usado para escribir expresiones que no son parte de un texto o párrafo, y son compuestos en líneas separadas.

## Modo matemático `inline`

Ejemplo de modo matemático `inline`:

```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
En física, la equivalencia de masa y energía 
esta dada por la ecuación $E=mc^2$, descubierta 
en 1905 por Albert Einstein.
\end{document}
```

Lo que produce la siguiente salida:

En física, la equivalencia de masa y energía esta dada por la ecuación $E=mc^2$, descubierta en 1905 por Albert Einstein.

Para componer matemáticas en modo `inline` se puede usar uno de estos pares delimitadores:

`\(...\)`, `$...$` o `\begin{math} ... \end{math}`, como se muestra a continuación:

```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
\begin{math}
E=mc^2
\end{math} es una muestra de cómo usar
el método matemático inline en un párrafo
---así también lo es $E=mc^2$, y también
lo es \(E=mc^2\).
\end{document}
```

La salida de este ejemplo es la siguiente:

$E=mc^2$ es una muestra de cómo usar el método matemático inline en un párrafo---así también lo es $E=mc^2$, y también lo es $E=mc^2$.

## Modo matemático `display`

Las ecuaciones mostradas en el modo `display` puede ser numera o no numerada, como se muestra a continuación:

```latex
\documentclass[12pt, letterpaper]{article}
\begin{document}
La equivalencia masa - energia se describe por la famosa ecuación
\[ E=mc^2 \] descubierta en 1905 por Albert Einstein.

En unidades naturales ($c = 1$), la formula expresa la identidad
\begin{equation}
E=m
\end{equation}
\end{document}
```

La salida de este ejemplo es la siguiente:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%203.png" width=500px></div>

Para componer matemáticas en modo `display` se puede usar uno de estos pares delimitadores:

`\[ ... \]`, `\begin{displaymath} ... \end{displaymath}`, o `\begin{equation} ... \end{equation}`. Anteriormente la composición de matemáticas en modo display requerían el uso de los caracteres delimitadores `$$`, como `$$ matematica aqui $$`, pero este método no se recomienda actualmente: use  `\[ ... \]` en su lugar.

## Aplicaciones más complejas

A continuación, se muestran ejemplos para demostrar un rango de ingreso de contenido matemático usando LaTeX:

```latex
\documentclass{article}
\begin{document}
Subindices en el modo matematico se escriben como $a_b$ y los superindices se escribe asi $a^b$. Estos pueden ser combinados y anidados para escribir expresiones como
\[ T^{i_1 i_2 \dots i_p}_{j_1 j_2 \dots j_q} = T(x^{i_1},\dots,x^{i_p},e_{j_1},\dots,e_{j_q}) \]
Se escriben integrales usando $\int$ y las fracciones usando $\frac{a}{b}$. Los límites son ubicados en integrales usando superindices y subindices:

\[ \int_0^1 \frac{dx}{e^x} =  \frac{e-1}{e} \]

Letras griegas minusculas se escriben como $\omega$ $\delta$ etc. Mientras que las letras griegas mayusculas se escriben como $\Omega$ $\Delta$.

Operadores matematicos se prefijan con un backslash como $\sin(\beta)$, $\cos(\alpha)$, $\log(x)$ etc.
\end{document}
```

La salida de este codigo será

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%204.png" width=500px></div>

El siguiente ejemplo usa el entorno `equation*` que es provisto por el paquete `amsmath`, entonces necesitamos añadir la siguiente línea en el preámbulo del documento:

`\usepackage{amsmath}` para usar el entorno `equation*` y añadir ecuaciones sin numerar.  

Entonces, se tiene el siguiente ejemplo:

```latex
\documentclass{article}
\usepackage{amsmath} % Para usar el entorno equation*
\begin{document}
\section{Primer ejemplo}

El conocido teorema de Pitágoras \(x^2 + y^2 = z^2\) fue probado como invalido por otros exponjentes, significando que la siguiente ecuacion no tiene soluciones enteras para  \(n>2\):

\[ x^n + y^n = z^n \]

\section{Segundo ejemplo}

Esta es una expresion matematica simple \(\sqrt{x^2+1}\) dentro de texto. 
Esto tambien lo es: 
\begin{math}
\sqrt{x^2+1}
\end{math}
Pero haciendo uso de otro comando.

Esta es una expresion matematica sin numeracion
\[\sqrt{x^2+1}\] 
separada del texto.

Esto tambien es lo mismo:
\begin{displaymath}
\sqrt{x^2+1}
\end{displaymath}

\ldots y esto:
\begin{equation*}
\sqrt{x^2+1}
\end{equation*}
\end{document}
```

Lo que resulta en:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%205.png" width=500px></div>

# Estructura básica de un documento

Se explorarán los extractos y como particionar un documento LaTeX en diferentes capítulos, secciones y párrafos.

## Resúmenes/Extracto

Los artículos científicos usualmente proveen un extracto que es un breve resumen/vistazo de sus temas principales, o argumentos.

```latex
\documentclass{article}
\begin{document}

\begin{abstract}
Este es un párrafo simple al inicio de un documento. Una breve introducción acerca del contenido principal.
\end{abstract}
\end{document}
```

La salida será la siguiente:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%206.png" width=500px></div>

## Párrafos y saltos de línea

- Para añadir un nuevo párrafo es necesario presionar la tecla `enter` dos veces, terminando la línea actual e insertando una línea en blanco subsecuente.
- Para empezar una nueva línea sin empezar un nuevo párrafo, es necesario ingresar un salto de línea manual usando el comando `\\`, o alternativamente, el comando `\newline`.

```latex
\documentclass{article}
\begin{document}

\begin{abstract}
Este es un párrafo simple al inicio de un documento. Una breve introducción acerca del contenido principal.
\end{abstract}

Despues del extracto se puede empezar con el primer párrafo, entonces se preciona `enter` dos veces para empezar un segundo párrafo.

Esta linea empezará un segundo párrafo.

Empezare un tercere párrafo y entonces añadire \\ un salto de linea que causará que este texto empiece en una nueva linea pero mantenga parte del mismo párrafo.
Alternativamente, puedo usar el comando \verb|\newline|\newline para empezar una nueva linea, que es parte del mismo párrafo.
\end{document}
```

La salida de este ejemplo será:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%207.png" width=500px></div>

Note que LaTeX identa automáticamente los párrafos -excepto inmediatamente después de encabezados del documento como `section` o `subsection`- como veremos.

Se advierte a los nuevos usuarios que muchos `\\` o `\newline`s no deberían usarse para simular párrafos con un espaciado mayor entre ellos porque esto podría interferir con los algoritmos de tipografía de LaTeX. El método recomendado es continuar usando líneas en blanco para crear nuevos párrafos, sin ningún `\\`, y cargar el paquete `parskip` añadiendo al preámbulo `\usepackage{parskip}`.

## Capítulos y secciones

Documentos largos, sin importar el software de autoría, usualmente particionan el texto en partes, capítulos, secciones, subsecciones y así sucesivamente.

Los comandos usados para el particionamiento dependerán de la clase del documento que se esté usando, por ejemplo, la clase `book` puede dividirse en partes, capítulos, secciones, subsecciones y así sucesivamente, al contrario, la clase `letter` no provee ningún soporte de comandos para hacer eso.

Por ejemplo:

```latex
\documentclass{book}
\begin{document}

\chapter{Primer Capítulo}

\section{Introducción}

Esta es la primera sección.

Lorem  ipsum  dolor  sit  amet,  consectetuer  adipiscing  
elit. Etiam  lobortisfacilisis sem.  Nullam nec mi et 
neque pharetra sollicitudin.  Praesent imperdietmi nec ante. 
Donec ullamcorper, felis non sodales...

\section{Segunda Sección}

Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...

\subsection{Primera Subsección}
Praesent imperdietmi nec ante. Donec ullamcorper, felis non sodales...

\section*{Sección No Numerada}
Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem...
\end{document}
```

La salida a este código será la siguiente:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%208.png" width=500px></div>

- Los capítulos se dividen usando el comando `\chapter{name}`
- Las secciones de un capítulo se dividen usando el comando `\section{sección 1}`
- Las secciones se pueden dividir en subsecciones y subsecciones de subsecciones con `\subsection` y `\subsubsection`
- Las secciones y sus subdivisiones se numeran automáticamente, pero se puede desactivar añadiendo un `*`, por ejemplo, `\section*{...}` o `subsection*{...}`¨.

Todas las particiones se listan a continuación, tomando en cuenta que variarán entre la clase de documento que esté asiganda.

- `\part{part}`
- `\chapter{chapter}`
- `\section{section}`
- `\subsection{subsection}`
- `\subsubsection{subsubsection}`
- `\paragraph{paragraph}`
- `\subparagraph{subparagraph}`

Particularmente, los comandos `\part` y `\chapter` solo están disponibles en las clases `report` y `book`.

# Creación de tablas

## Creación de tablas básicas

```latex
\begin{enter}
\begin{tabular}{c c c}
cell1 & cell2 & cell3 \\
cell4 & cell5 & cell6 \\
cell7 & cell8 & cell9
\end{tabular}
\end{center}
```

Este ejemplo produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%209.png" width=125px></div>

El entorno `tabular` es el método predeterminado por LaTeX para crear tablas. Se debe especificar el parámetro para este entorno, en este caso, `{c c c}` que alerta que habrá tres columnas y el texto dentro deberá estar centrado. Tambien se puede usar `r` para alinear a la derecha o `l` para alinearlo a la izquierda. El símbolo de alineación `&` es usado para demarcar las celdas individuales dentro de una fila de la tabla. Para terminar la fila de la tabla, se debe usar el salto de línea `\\`. La tabla está contenida dentro de un entorno `center` para centrarlo dentro del ancho del texto de la página.

## Añadiendo bordes

Los entornos tabulares soportan líneas horizontales y verticales (reglas) como parte de la tabla:

- Para añadir reglas horizontales, sobre y debajo de las filas, usar el comando `\hline`.
- Para añadir reglar verticales, entre las columnas, use el parámetro de linea vertical `|`.

En este ejemplo el argumento es `{|c|c|c|}` que declara tres columnas (centradas) cada una separada con una regla vertical; además, se usa `\hline` para añadir una regla horizontal sobre la primera fila y debajo de la última fila:

```latex
\begin{center}
\begin{tabular}{|c|c|c|}
	\hline
	cell1 & cell2 & cell3 \\
	cell4 & cell5 & cell6 \\
	cell7 & cell8 & cell9 \\
	\hline
\end{tabular}
\end{center}
```

Lo que produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/LL30Fig18-plain.svg" width=500px></div>

Aqui hay otro ejemplo:

```latex
\begin{center}
\begin{tabular}{||c c c c||}
	\hline
	col1 & col2 & col2 & col3 \\ [0.5ex]
	\hline\hline
	1 & 6 & 87837 & 787 \\
	\hline
	2 & 7 & 78 & 5415 \\
	\hline
	4 & 545 & 18744 & 7560 \\
	\hline
	5 & 88 & 788 & 6344 \\ [1ex]
	\hline
\end{tabular}
\end{center}
```

Lo que produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%2010.png" width=500px></div>

> Para optimizar el tiempo de creación de tablas, se pueden usar herramientas como [TablesGenerator.com](https://www.tablesgenerator.com/) para exportar código de tabulares
> 

## Leyendas, etiquetas y referencias

Se puede poner leyendas y referenciar tablas de la misma manera en que se hace con las imágenes. La única diferencia es que en lugar de usar el entorno `figure`, se hace uso del entorno `table`.

```latex
La tabla \ref{tabla:datos} muestra cómo añadir una 
leyenda a la tabla y referenciarla.
\begin{table}[h!]
\centering
\begin{tabular}{||c c c c||} 
 \hline
 Col1 & Col2 & Col2 & Col3 \\ [0.5ex] 
 \hline\hline
 1 & 6 & 87837 & 787 \\ 
 2 & 7 & 78 & 5415 \\
 3 & 545 & 778 & 7507 \\
 4 & 545 & 18744 & 7560 \\
 5 & 88 & 788 & 6344 \\ [1ex] 
 \hline
\end{tabular}
\caption{Tabla para probar leyendas y etiquetas.}
\label{tabla:datos}
\end{table}
```

Esto produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%2011.png" width=500px></div>

# Añadiendo una Tabla de Contenidos

Crear un tabla de conteidos es facil porque el comando `\tableofcontents` hace casi todo el trabajo por ti:

```latex
\documentclass{article}
\title{Secciones y capitulos}
\author{Kevin Martinez}
\date{Marzo 2023}
\begin{document}

\maketitle

\tableofcontents

\section{Introducción}

Esta es la primera sección.

Lorem  ipsum  dolor  sit  amet,  consectetuer  adipiscing  
elit.   Etiam  lobortisfacilisis sem.  Nullam nec mi et 
neque pharetra sollicitudin.  Praesent imperdietmi nec ante. 
Donec ullamcorper, felis non sodales...

\section*{Seccion no numerada}
\addcontentsline{toc}{section}{Seccion no numerada}
% \addcontentsline para añadir una seccion no numerada manualmente
% toc = Table of contents
% section para ponerlo al mismo nivel que una sección
% Titulo para poner en la tabla de contenidos

Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...

\section{Segunda seccion}

Lorem ipsum dolor sit amet, consectetuer adipiscing elit.  
Etiam lobortis facilisissem.  Nullam nec mi et neque pharetra 
sollicitudin.  Praesent imperdiet mi necante...

\end{document}
```

Esto produce la siguiente salida:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%2012.png" width=500px></div>

Las secciones, subsecciones y capítulos son incluidos automáticamente en la tabla de contenidos. Para añadir entradas manualmente, como una sección no numerada, use el comando `\addcontentsline` como se muestra en el ejemplo.

# Encontrando y usando paquetes LaTeX

LaTeX no solo entrega habilidades tipográficas significativas, sino que también provee una estructura de extensión a través del uso de paquetes añadidos (add-on). En lugar de tratar de proveer comandos y características que “traten de hacerlo todo”, LaTeX está diseñado para ser extensible, permitiendo a usuarios cargar cuerpos de cuerpo externos (paquetes) que proveen capacidades tipográficas más específicas o extienden las características propias de LaTeX. Como se observó en la sección “Añadiendo imágenes”, el paquete `graphicx` extiende LaTeX proveyendo comandos para importar archivos gráficos y fue cargado (en el preámbulo) por escritura: `\usepackage{graphicx}`.

## Cargando paquetes

Como se mecionó arriba, los paquetes son cargados en el preámbulo del documento mediante el comando `\usepackage` pero dado que algunso paquetes LaTeX proveen un conjunto de opciones, lo cuales pueden ser usados para configurar su comportamiento, el comando `\usepackage` a menudo se ve asi:

```latex
\usepackage[options]{somepackage}
```

Los corchetes `[...]` le dicen a LaTeX qué conjunto de opciones deben ser aplicadas cuando cargue algún paquete. Dentro del conjunto de opciones solicitadas por el usuario, las opciones individuales, o ajustes, son separadas típicamente por una coma; por ejemplo, el paquete `geometry` provee muchas opciones para configurar la disposición de la página en LaTeX, entonces un uso típico de `geometry` se vería de la siguiente forma:

```latex
\usepackage[total={6.5in,8.75in}, top=1.2in, left=0.9in, includefoot]{geometry}
```

El paquete `geometry` es un ejemplo de un paquete escrito y contribuido por miembros de la comunidad global de LaTeX y puesto a disposición, gratis, para cualquiera que desee usarlo.

Si un paquete LaTeX no provee ninguna opción, o el usuario quiere usar los valores por defecto en las opciones del paquete, debe ser cargado de la siguiente forma:

```latex
\usepackage{algunpaquete}
```

Cuando escribes `\usepackage[...]{algunpaquete}` LaTeX buscar por un correspondiente archivo llamado `algunpaquete.sty`, el cual es necesario que sea cargado y procesado para hacer que los comandos del paquete estén disponibles y ejecute xualquier otro código provisto para ese paquete. Si LaTeX no es capaz de encontrar `algunpaquete.sty` terminará mostrando un error, como se demuestra en el siguiente ejemplo de Overleaf:

```latex
\documentclass[12pt, letterpaper]{article}
\usepackage{algunpaquete} % Este NO es un paquete real existente
\begin{document}
Esto va a fallar!
\end{document}
```

Lo que produce los siguiente errores:

<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%2013.png" width=500px></div>
<div align="center"><img src="https://github.com/Al3xMR/Guia_LaTeX-Overleaf/blob/main/images/Untitled%2014.png" width=500px></div>

## Encontrando información sobre paquetes: CTAN

Los paquetes son distribuidos a través de la Red de Archivos Comprensivos TeX, usualmente referida como CTAN (Comprehensive TeX Archive Network), el cual, al tiempo de escribir esto, hospeda 6287 paquetes de 2881 contribuidores. CTAN [se describe a sí misma](https://www.ctan.org/ctan) cómo

> “… un conjunto de sitios de Internet alrededor del mundo que ofrece material relacionado a TeX para su descarga.
> 

Puedes buscar en CTAN para buscar paquetes útiles; por jemeplo:

- [Por tema](https://www.ctan.org/topics/cloud)
- [Alfabéticamente](https://www.ctan.org/pkg) (útil si sabes el nombre del paquete)

Tambien puedes usar la herramienta de búsqueda (al inicio de la página).

## Paquetes disponibles en Overleaf: Introduciendo TeX Live

Una vez al año un subconjunto (grande) de paquetes hospedados en CTAN, más fuente relacionadas a LaTeX y otro software, es reunido y distribuido como un sistema llamado [TeX Live](https://tug.org/texlive/), el cual puede ser usado para instalar tu propia configuración (local) de LaTeX. De hecho, [los servidores de Overleaf también usan TeX Live](https://www.overleaf.com/learn/latex/Overleaf_and_TeX_Live) y son actualizados cuando una nueva versión de TeX Live es lanzada.

Los paquetes nuevos, y actualizaciones de los ya existentes, son subidos a CTAN durante todo el año pero las actualizaciones de TeX Live son distribuidas anualmente; y en consecuencia, los paquetes contenidos en la versión actual de TeX Live no estarán a la fecha con los que estan hospedados en CTAN.
