# CSS-Styleguide

Una guía de estilo para escribir CSS sostenible y escalable

## Contenido
]
* [Introducción](#introducción)
  * [La importancia de una guía de estilo](#la-importancia-de-una-guía-de-estilo)
  * [Renuncia de responsabilidad](#renuncia-de-responsabilidad)
  * [Principios clave](#principios-clave)
* [Sintaxis y formato](#sintaxis-y-formato)
  * [Conjunto de reglas CSS](#conjunto-de-reglas-css)
    * [ID](#id)
    * [Shorthand](#shorthand)
    * [!important](#important)
  * [Codificación](#codificación)
  * [Comillas](#comillas)
  * [Números](#números)
    * [Ceros](#ceros)
    * [Unidades](#unidades)
    * [Cálculos](#cálculos)
  * [Números mágicos y absolutos](#números-mágicos-y-absolutos)
  * [Convenciones para los nombres](#convenciones-para-los-nombres)
    * [JS hooks](#js-hooks)
    * [Internacionalización](#internacionalización)
  * [Selectores](#selectores)
    * [Selectores sobre-calificados](#selectores-sobre-calificados)
    * [Rendimiento de los selectores](#rendimiento-de-los-selectores)
  * [Uso de Media Queries](#uso-de-media-queries)
  * [Clases en HTML](#clases-en-html)
  * [Preprocesadores](#preprocesadores)
  * [Comentarios](#comentarios)
    * [Tabla de contenidos](#tabla-de-contenidos)
    * [Alto nivel](#alto-nivel)
    * [Bajo nivel](#bajo-nivel)
    * [Código de etiquetas](#código-de-etiqutas)
    * [Comentarios en línea](#comentarios-en-línea)
    * [Extracción Comentarios](#extracción-comentarios)
* [Arquitectura](#arquitectura)
  * [Componentes](#componentes)
  * [El Patrón 7-1](#el-patrón-7-1)
    * [Carpeta _abstracts_](#carpeta-abstracts)
    * [Carpeta _base_](#carpeta-base)
    * [Carpeta _layout_](#carpeta-layout)
    * [Carpeta _components_](#carpeta-components)
    * [Carpeta _pages_](#carpeta-pages)
    * [Carpeta _themes_](#carpeta-themeS)
    * [Carpeta _vendor_](#carpeta-vendor)
    * [Archivo principal](#archivo-principal)
  * [El archivo de la vergüenza](#el-archivo-de-la-vergüenza)
* [Herramientas](#herramientas)
  * [Bootstrap](#bootstrap)
  * [Autoprefixer](#autoprefixer)
  * [Css Comb](#css-comb)

# Introducción

Una guía de estilo no es sólo un documento agradable de leer mientras te imaginas tu código perfecto. Se trata de un documento clave en la vida de un proyecto que describe cómo y por qué se debe escribir el código. Puede parecer una exageración para pequeños proyectos, pero ayuda mucho a mantener el código limpio, escalable y fácil de mantener.

Sobra decir, que cuantos más desarrolladores participen en el proyecto, más necesarias son las guías de estilo.

## La importancia de una guía de estilo

Una guía de estilo para desarrollar código (nota: no es una guía de estilo visual) es una valiosa herramienta para los equipos que:

- Construyen y mantienen productos durante un tiempo razonablemente largo.
- Tienen desarrolladores con diferentes habilidades y especialidades.
- Tienen un número variable de desarrolladores que trabajan en el proyecto en un momento determinado.
- Tienen una serie de código base en el que los desarrolladores entran y salen constantemente.

## Renuncia de responsabilidad

Directrices CSS es una guía de estilo; no es _la_ guía de estilo. Contiene metodologías, técnicas y consejos que se recomienda al equipo, pero tus propios gustos y circunstancias bien pueden ser diferentes. La experiencia puede ser diferente.

Además, esta guía de estilo es **subjetiva y personal**. Piensa en ella como una colección de metodologías y consejos que se han reunido y pulido durante los últimos años.

## Principios clave

Al final del día, si hay una cosa que me gustaría que aprendieses de toda esta guía de estilo, es que **el código debe mantenerse tan simple como sea posible**.

Algunas veces es mejor repetirse un poco para que el proyecto sea fácil de mantener, antes que construir un sistema demasiado pesado, inabarcable e innecesariamente complicado que genere un código imposible de mantener porque es demasiado complejo.

El pragmatismo prevalece sobre la perfección. En algún momento, es probable que te des cuenta que estás yendo en contra de las reglas descritas aquí. Si tiene sentido, si crees que está bien, hazlo. El código solo es un medio, no un fin.

# Sintaxis y formato

Una de las formas más simples de una guía de estilo es un conjunto de normas relativas a la sintaxis y el formato. Tener una forma estándar de escribir CSS se traduce en que el código siempre será familiar para todos los miembros del equipo.

Cuando varios desarrolladores están involucrados en la escritura CSS dentro del mismo proyecto, es sólo cuestión de tiempo antes de que uno de ellos empiece a hacer las cosas a su manera. Las guías de estilo que fomentan la coherencia no solo previenen ésto, sino que también ayudan a la hora de leer y actualizar el código.

A grandes rasgos, lo que queremos es:

- Cuatro (4) espacios en blanco, sin tabulaciones.
- Idealmente, líneas de 80 caracteres.
- Reglas CSS multilínea correctamente escritas.
- Buen uso de los espacios en blanco.

Pero, como cualquier cosa, los detalles son algo irrelevante, la consistencia es la clave.

## Conjunto de reglas CSS

Esta es la forma en la que un conjunto de reglas CSS deben estar escritas:

- Cada selector debe ir en nuevas líneas.
- La llave de apertura debe ir separada por un espacio del selector.
- Cada declaración debe ir en una nueva línea.
- Añadir un espacio antes y después de los dos puntos.
- Poner punto y coma al final de todas las declaraciones.
- La llave de cierre debe ir en una nueva línea.
- Añadir una línea después de la llave de cierre.
- Alineación de los valores en los dos puntos.
- Colores HEX en minúsculas.
- Colores HEX en formato corto cuando sea posible.

 Debido al uso de preprocesadores, se tomarán las siguientes pautas:

- Las llamadas a _mixin_  deben ir antes de cualquier declaración.
- Se ordenaran los atributos de manera lógica.
- No usar prefijos de navegadores.
- No usar un salto de línea antes de una llave de cierre.

Para cumplir estas reglas podemos usar un IDE que permita el formateo de texto, el uso de herramientas como CCScomb y postprocesadores (autoprefixer), que detallaremos al final de este documento.

### ID

**Nunca se usan IDs en CSS.** Pueden ser usados en tu marcado para referencias de JS, pero sólo se usan _clases_ para estilos.

Las _clases_ vienen con el beneficio de ser reusables y tienen un buen y bajo especificado. El especificado es una de las formas más rápidas de afrontar dificultades en proyectos y mantenerlo bajo en todo momento, es imperativo. Una ID es  **255**  veces más específico que una clase, por ello _**nunca**_ los uses en CSS.

### Shorthand

**Los shorthand de CSS deben usarse con precaución.** Es tentador usar declaraciones como 'background: red;' pero haciéndolo lo que de verdad dices es 'no quiero que la imagen haga scroll, que se alinee arriba a la izquierda, que se repita en el eje X y en el eje Y, y con un fondo rojo'. La mayoría de las veces ésto no causará problemas, pero esa sola vez que lo causa es suficiente para evitar el uso de shorthands. En vez de ello, usa 'background-color: red;'.

Similarmente, declaraciones como 'margin: 0;' están bien y son cortas, pero  **sé explícito**. Si lo que quieres de verdad aplicar es solo el margen en el inferior de un elemento entonces es más apropiado usar 'margin-bottom: 0;'.

Sé explícito en que propiedad estableces y ten cuidado de no desconfigurar otras por error al usar un shorthand. Por ejemplo, si quieres solo eliminar el margen inferior de un elemento no tiene sentido establecer todos los márgenes a 0 con 'margin:0;'.

Los shorthands son buenos, pero pueden hacer caer en malas prácticas fácilmente.

### '!important'

Está bien utilizar '!important' sólo en clases _helper_. Añadir '!important' preventivamente es correcto, Por ejemplo: '.error{ color:red !important;}', como ya sabrás  **siempre**  querrás que esta regla tenga prioridad.

Usa '!important' cuidadosamente. Para salir de malas situaciones de especificación no es recomendado. Rehaz tu CSS e intenta combatir estos problemas reconstruyendo tus selectores. Mantener tus selectores cortos y evitando IDs ayudará enormemente.

## Codificación

Para evitar cualquier posible problema con la codificación de caracteres, es muy recomendable forzar la **codificación UTF-8** en la hoja de estilo principal usando la directiva @charset. Asegúrate que es el primer elemento de la hoja de estilo y que no hay ningún otro carácter de cualquier tipo antes.

## Comillas

Los valores CSS siempre deben ir entre **comillas simples (')** siempre que sean necesarias. Además de la coherencia con otros lenguajes, son más fáciles de escribir en los teclados _qwerty_ y ayudan a la legibilidad general. Las URLs siempre irán entre comillas .

## Números

El número es un tipo de datos que incluye de todo, desde números sin unidades a longitudes, pasando por duraciones, frecuencias y ángulos, entre otros. Esto permite que se puedan realizar cálculos en estas medidas.

### Ceros

Siempre se deben mostrar los ceros a la izquierda antes de un valor decimal menor que uno. Nunca mostrar ceros finales.

### Unidades

Cuando se trata de longitudes, el 0 nunca debe llevar el nombre de la unidad. Los _breakpoints_ en los @media los especificaremos en 'em'.

### Cálculos

Los cálculos numéricos de nivel superior deben ir siempre entre **paréntesis**  lo cual, no solo mejorará drásticamente la legibilidad, sino que también evitará algunos casos extremos, ya que fuerza a evaluar los contenidos entre paréntesis.

## Números mágicos y absolutos

Un _número mágico_ es un número usado porque 'funciona'. Son malos porque raramente funcionan de verdad y no son muy seguros o flexibles. Tienden a solucionar síntomas y no problemas.

Por ejemplo, usar '.dropdown-nav li:hover ul{ top: 37px; }' para mover un desplegable bajo la navegación en _hover_ está mal, ya que 37px es un _número mágico_. 37px sólo funciona aquí porque en este escenario en particular el '.dropdown-nav' tiene 37px de alto.

En vez de eso, deberías usar '.dropdown-nav li:hover ul{ top: 100%; }' que quiere decir que no importa el alto de '.dropdown.nav', el desplegable siempre se colocará a 100% del borde superior.

Piensa cada vez que escribes un número para que _encaje_ en el layout; si puedes evitarlo usando 'aliases' (Por ejemplo 'top:100%' para indicar 'todo a partir del borde superior') o, aún mejor, sin medida alguna.

Escribir medidas para que _encajen_ en el layout es un compromiso que no necesariamente querrás mantener.

## Convenciones para los nombres

Mayormente utilizamos clases delimitadas por guiones (Por ejemplo '.foo-bar' y no '.foo\_bar' ni '.foobar'), con notaciones BEM (Block Element, Modifier) para piezas más complejas.

BEM es una metodología para nombrar y clasificar selectores CSS de manera que los hacemos más estrictos, transparentes e informativos.

La convención de nombre sigue este patrón:
```css
.bloque {}

.bloque__elemento {}

.bloque--modificador {}
```
'.bloque' representa el primer nivel de una abstracción o componente.

'.bloque\_\_element' representa un descendente de '.bloque' que se ayuda de '.bloque' como un conjunto.

'.bloque--modificador' representa un estado diferente de '.bloque'.

Una analogía del funcionamiento de las clases BEM sería:
```css
.persona {}

.persona--mujer {}

.persona__mano {}

.persona__mano--izquierda {}

.persona__mano--derecha {}
```
Aquí vemos como el objeto básico que estamos describiendo es una persona, y que un tipo diferente de persona podría ser una mujer. También podemos ver que las personas tienen manos; son sub-partes de las personas, y que hay variaciones, como izquierda y derecha.

Ahora podemos nombrar nuestros selectores basado en sus objetos base y podemos también comunicar que función tiene el selector; es un sub-componente ('\_\_') o una variación ('--')?

Independientemente que uses BEM o no, siempre asegúrate que las clases son nombradas muy claramente; mantenlas tan cortas como sea posible pero tan largas como sea necesario. Asegúrate que cualquier objeto o abstracción tienen nombres vagos (Por ejemplo: '.ui-list', '.media') para permitir su reutilización siempre que sea posible. Las extensiones de objetos deben ser nombradas mucho más explícitamente (Por ejemplo: '.user-avatar-link). No te preocupes por la longitud o cantidad de clases; gzip comprimirá todo el código bien escrito _increíblemente_ bien.

### JS hooks

**Nunca uses una clase de CSS _de estilos_ como un hook de JS.**  Adjuntar comportamientos de JS a clases de estilo quiere decir que nunca podremos tener una sin la otra

Si necesitas enlazar a alguna etiqueta usa una clase específica de JavaScript. Simplemente es una clase que empiece por '.js-', por ejemplo '.js-toggle', '.js-drag-and-drop' y de esta manera podemos agregar ambas clases, JS y CSS, a nuestra etiqueta, pero nunca se sobrepondrán una a la otra.

### Internacionalización

Por el bien de la consistencia, es mejor usar siempre Inglés Americano en CSS. CSS, así como la mayoría (si no todos) de lenguajes, están escritos en Inglés Americano, con lo cual mezclar sintaxis como 'color:red' con clases como '.colour-picker {}' carece de consistencia.

En beneficio de la consistencia, siempre nombra clases y variables en el lenguaje en el que estás trabajando.

## Selectores

Mantén los selectores cortos, eficientes y portables.

Selectores basados en su posición son malos por varias razones. Por ejemplo, tomemos '.sidebar h3 span{}'. Este selector está basado en la posición y por ello no podemos mover ese 'span' fuera de un 'h3' fuera de un '.sidebar' y mantener el estilo.

Los selectores que son muy largos también introducen problemas de optimización. Cuantas más verificaciones hay en un selector (Por ejemplo '.sidebar h3 span' tiene tres verificaciones, '.content ul p a' tiene cuatro), más trabajo tiene el navegador.

Siempre que sea posible nos aseguraremos que los estilos no dependan de la posición en el CSS, nos aseguraremos de que los selectores sean buenos y cortos.

Los selectores en general deben mantenerse cortos, pero los nombres de las clases en sí mismas deben ser tan largas como lo necesiten. Una clase de '.user-avatar' siempre es mejor que '.usr-avt'

No hay que preocuparse por la 'semántica' de los nombres de las clases y elegir algo sensato y previsor.

### Selectores sobre-calificados

Un selector sobre calificado es como 'div.promo'. Probablemente podrías obtener el mismo resultado usando sólo '.promo'. Claro, algunas veces querrás calificar una clase con un elemento (Por ejemplo si tienes una clase genérica '.error' que debe verse diferente cuando se aplica a un elemento diferente (Por ejemplo: '.error{ color: red; }' 'div.error{ padding: 14px; }')), pero generalmente se evita siempre que sea posible.

Otro ejemplo de un selector sobre calificado sería 'ul.nav li a {}'. Al igual que arriba, podemos eliminar instantáneamente el 'ul' y ya que sabemos que '.nav' es una lista, podemos saber que cualquier 'a' _debe_ ir en un 'li', así que podemos cambiar 'ul.nav li a {}' por '.nav a {}'.

### Rendimiento de los selectores

Aunque es verdad que los navegadores son cada vez más rápidos renderizando CSS, la eficiencia es algo en lo que siempre deberíamos tener un ojo puesto. Selectores cortos, no anidados, sin usar el selector universal ('\*{}') y evitando selectores complejos de CSS3 ayudarán a evitar problemas de rendimiento.

## Clases en HTML

Haz las cosas fáciles de leer, separa tus clases en HTML con dos (2) espacios en blanco. Este espacio en blanco incrementado permitirá ubicar con mayor facilidad y mejorar la lectura de múltiples clases.

## Preprocesadores

Tanto Sass como Less hay que usarlos con cuidado. Los preprocesadores mejoran la creación de CSS, pero evita anidaciones exageradas. Anida sólo cuando sea necesario en CSS, Por ejemplo:
```css
.header {}

.header .site-nav {}

.header .site-nav li {}

.header .site-nav li a {}
```
Sería totalmente innecesario en un CSS normal, que viene de escribir incorrectamente:
```css
.header{
    .site-nav {
        li {
            a {}
        }
    }
}
```
Lo correcto sería escribirlo así:
```css
.header {}

.site-nav {
    li {}
    a {}
}
```
## Uso de Media Queries

El sistema de _Media Queries_, gracias a que usamos preprocesadores, debe ir dentro del selector, ya que juega un buen papel con la idea de _componentes_ (_components_).

Es posible que escuches que este acuerdo dará como resultado en CSS, bloques duplicados de _Media Queries_. Esto es definitivamente cierto. Sin embargo, se han realizado pruebas y la conclusión es que no importará una vez Gzip (o cualquier equivalente) haya hecho su trabajo.

## Comentarios

La sobrecarga cognitiva de trabajar con CSS es enorme. Con muchos matices a tener en cuenta y tantas cosas específicas del proyecto por recordar, la peor situación de la mayoría de los desarrolladores es ser la persona que no escribió el código. Recordar sus propias clases, reglas y objetos es manejable hasta cierto punto, pero cualquiera que herede un CSS apenas tiene posibilidades.

Como regla general, debemos comentar cualquier cosa que no es evidente sólo a partir del código. Es decir, no hay necesidad de decirle a alguien que color: red; hará algo rojo, pero si estamos utilizando 'overflow: hidden;' para limpiar los _floats_, en lugar de recortar el desbordamiento, esto algo que es probablemente valga la pena documentar.

### Tabla de contenidos

Una tabla de contenidos al inicio de la hoja de estilos detalla las secciones mantenidas en el documento.

Esto le dice al siguiente desarrollador que tome el proyecto exactamente qué puede esperar encontrar en el archivo. Cada ítem en la tabla de contenido marca el título de una sección.

#### Título de secciones

La tabla de contenidos sería inútil a menos que tuviera sus correspondientes títulos de secciones. Denotad una sección de la siguiente manera:
```css
/*------------------------------------*\
    #nav
\*------------------------------------*/
```
Asignar el prefijo '#' al nombre de la sección nos permite efectuar una búsqueda '#NOMBRE-SECCIÓN' y limitar esa búsqueda sólo a los títulos de sección.

Si trabajas con hojas de estilo muy grandes, deja unos saltos de línea entre cada sección. Este bloque en blanco permite ubicar las secciones haciendo un rápido _scroll_ por el documento.

### Alto nivel

Para grandes comentarios que documentan secciones o componentes enteros, usamos un comentario estilo **DocBlocks** que se ajusta a nuestro ancho de 80 columnas.

Un ejemplo de comentario sería:
```css
/**
 * Esto es un comentario estilo docBlock
 *
 * Esta es una descripción más larga del comentario, describiendo el código con más
 * detalle. Limitamos estas líneas a 80 caracteres de longitud
 *
 * Podemos tener etiquetado en el comentario, y de hecho es recomendable:
 *
   <div class=foo>
       <p>Lorem</p>
   </div>
 *
 * No ponemos un asterisco como prefijo en las líneas de código, ya que inhibiría
 * copiar y pegar.
 *
 */
```
### Bajo nivel

Muchas veces queremos hacer comentarios sobre las declaraciones específicas (es decir, líneas) en un conjunto de reglas. Para ello utilizamos un tipo de nota que se desarrolla en el comentario de alto nivel.
```css
/**
 * Esto es un comentario estilo docBlock
 *
 * Esta es una descripción más larga del comentario, describiendo el código con más
 * detalle. Limitamos estas líneas a 80 caracteres de longitud
 *
 * 1. Definición de la propiedad
 */

.foo {
    color : #f00; /*[1]*/
}
```
### Código de etiquetas

Si escribes un nuevo componente entonces deja algunas etiquetas relativas a su función en un comentario.

### Comentarios en línea

Podemos comentar líneas usando **doble barra '//'** dejando un comentario de bajo nivel. También se podrá usar este tipo de comentarios para especificar de manera muy breve entre líneas.

### Extracción comentarios

No hace falta decir que no hay comentarios en entornos de producción, todos los CSS deben ser **minificados** sin comentarios.

# Arquitectura

Establecer la arquitectura del CSS es probablemente una de las cosas más difíciles que tendrás que hacer en la vida de un proyecto. Mantener esa arquitectura coherente y significativa es aún más difícil.

Afortunadamente, uno de los principales beneficios de utilizar un preprocesador CSS es tener la capacidad de dividir el código en varios archivos sin afectar al rendimiento. Gracias a la directiva @import, es perfectamente seguro (y de hecho recomendable) usar tantos archivos como sean necesarios en el desarrollo, compilándolo todo en una sola hoja de estilo cuando vaya a producción.

Divide el código en carpetas significativas para que sea sencillo encontrar las cosas más tarde, cuando se tenga que volver al código de nuevo.

Hay una gran cantidad de arquitecturas populares para los proyectos CSS: OOCSS, Atomic Design, similares a Bootstrap, Foundation. Todas ellas tienen sus méritos, pros y contras.

Utilizamos un método que resulta ser bastante similar a SMACSS, que se centra en mantener las cosas simples y evidentes.

La arquitectura, en la mayoría de los casos, es muy específica para cada proyecto. Siéntete libre de descartar o de adaptar la solución propuesta para que encuentres un sistema que se adapte a tus necesidades.

## Componentes

Hay una gran diferencia entre hacer que algo funcione y hacerlo bien. CSS es un lenguaje bastante desordenado. **Cuánto menos CSS tengamos, mejor**. No queremos tratar con megas de código CSS. Para mantener las hojas de estilo cortas y eficientes es una buena idea pensar en una interfaz como en una colección de componentes.

Los componentes pueden ser cualquier cosa, siempre y cuando:

- Haga una cosa y solo una cosa.
- Sea reutilizable y se reutilice a lo largo del proyecto.
- Sea independiente.

Por ejemplo, un formulario de búsqueda debería ser tratado como un componente. Debería ser reutilizable, en diferentes lugares, en diferentes páginas y en varias situaciones. No debe depender de su posición en el DOM (pie de página, barra lateral, contenido principal…).

La mayor parte de cualquier interfaz puede concebirse en forma de pequeños componentes y recomiendo encarecidamente que lo hagas. Esto no solo reducirá la cantidad de CSS necesario para todo el proyecto, sino que también se convierte en un código mucho más fácil de mantener que un desorden caótico donde todo está hecho un lío.

## El Patrón 7-1

7 carpetas, 1 archivo. Básicamente, tienes todas las partes almacenadas en 7 carpetas diferentes, y un único archivo en el directorio raíz (usualmente llamado main) que importa todas estas partes para ser compiladas en una hoja de estilo CSS.
```
- abstracts/
- base/
- components/
- layout/
- pages/
- themes/
- vendor/
- main
```
Idealmente, podemos llegar a algo como esto:
```
src/
|
|– abstracts/
|   |– \_variables   # Variables
|   |– \_functions   # Funciones
|   |– \_mixins      # Mixins
|
|– base/
|   |– \_reset       # Reset/normalize
|   |– \_typography  # Reglas tipográficas
|   …                # Etc.
|
|– components/
|   |– \_buttons     # Botones
|   |– \_inputs      # Inputs
|   …                    # Etc.
|
|– layout/
|   |– \_navigation  # Navegación
|   |– \_header      # Encabezamiento
|   |– \_footer      # Pie de página
|   …                    # Etc.
|
|– pages/
|   |– \_home        # Estilos específicos para la página de inicio
|   …                    # Etc.
|
|– themes/
|   |– \_default     # Tema por defecto
|   …                    # Etc.
|
|– vendors/
|   |– \_bootstrap   # Bootstrap
|   |– \_jquery-ui   # jQuery UI
|   …                # Etc.
|
|– main             # Archivo principal
```
### Carpeta _abstracts_

_Abstracts_ agrupa todas las herramientas usadas a lo largo del proyecto. Cada función, variable y mixin global debe ir aquí. La regla de oro para esta carpeta es que no debe emitir una sola línea de CSS cuando se compila por sí solo.

### Carpeta _base_

_Base_ contiene lo que podríamos llamar el código estándar para el proyecto. Es posible encontrar algunas reglas tipográficas, y la definición de algunos estilos estándar para los elementos HTML de uso común.

### Carpeta _layout_

_Layout_ contiene lo que participa en la disposición de sitio. Esta carpeta puede tener hojas de estilo para las principales partes del sitio (encabezado, pie de página, navegación, barra lateral...), el grid o los formularios.

### Carpeta _components_

Para los pequeños componentes, existe la carpeta 'components/'. Mientras que _Layout_ está más centrada en la estructura global, _Components_ se centra en los widgets. Contiene módulos específicos como un slider, un loader, un widget o cualquier cosa por el estilo. Por lo general habrá una gran cantidad de archivos en _Components_.

### Carpeta _pages_

Si hay estilos específicos de página, es mejor ponerlos en 'pages/', en un archivo de nombre de la página. Por ejemplo, no es raro tener estilos muy específicos para la página de inicio de ahí la necesidad de un archivo '\_home' en 'pages/'.

### Carpeta _themes_

En caso de disponer de diferentes temas entre la aplicación o sitio se tendrán en 'themes/'. Diferencias entre distintas plantillas para proyectos específicos.  No tiene por qué usarse en todos los proyectos.

### Carpeta _vendor_

_Vendor_ contiene todos los archivos CSS de las bibliotecas externas. Es una buena manera de decir 'Esto no es de mío, no es mi código, no es mi responsabilidad'.  Si hay que sobrescribir una parte de terceros, la carpeta llamada 'vendors-extensions/' incluirá los valores que se sobrescriben. Por ejemplo, 'vendors-extensions/\_bootstrap' es un archivo que contiene todas las variables destinadas sobrescribir los valores por defecto de Bootstrap. Esto es para evitar la edición del proveedor propios archivos, que por lo general no es una buena idea.

### Archivo principal

El archivo principal (normalmente llamado _main_) debe ser el único archivo de todo el código que no empieza con guion bajo. **Este archivo debería contener nada más que @import y comentarios**. Los archivos deben de importarse según la carpeta que los contiene, una después de la otra en el siguiente orden:

1. vendor/
2. abstracts/
3. base/
4. layout/
5. components/
6. pages/
7. themes/

Con el fin de mantener la legibilidad, el archivo principal debe respetar las siguientes pautas:

- Un archivo para cada @import.
- Un @import por línea.
- No añadir una línea en blanco entre dos archivos importados que pertenezcan a la misma carpeta.
- Dejar una línea en blanco después del último archivo importado de una carpeta.
- Las extensiones de archivo y los guiones principales se omiten.

No se recomienda importar los archivos de manera global, porque importa los archivos siguiendo orden alfabético que, por lo general, no suele ser lo deseado, especialmente cuando se trata de un lenguaje que depende del orden en el que está el código fuente.

## El archivo de la vergüenza

Hay un concepto interesante que se ha popularizado que consiste en poner todas las declaraciones CSS, código temporal, pruebas, hacks y cosas de las que no nos sentimos muy orgullosos en un archivo de la _vergüenza_. Este archivo, titulado dramáticamente '\_shame' (localizado en la carpeta con el mismo nombre), se importará después de todos los otros archivos, al final de la hoja de estilo. **No tiene que por aparecer en el proyecto** si no es necesario.  Obviamente se necesitan unas reglas y criterios:

- Si es un hack, va en '\_shame'.
- Comenta todos los hacks detalladamente.
  - ¿A que parte del código va dirigido?
  - ¿Por qué se necesita ?
  - ¿Cómo soluciona esto el problema?
  - ¿Cómo se podría solucionar con más tiempo?
- No culpemos al desarrollador, si se han explicado las razones de porque se ha hecho será valido.
- Intenta limpiar '\_shame' cuando tengas algo de tiempo.

# Herramientas

Cada vez más tenemos un completo ecosistema de frameworks, plugins, librerías y herramientas.

## Bootstrap

Uno de los _frameworks CSS_ de maquetación más usados. Usaremos todas sus ventajas para nuestra maquetación (variables, mixins, grid...) gracias al @import.

## Autoprefixer

Estar pendiente de escribir prefijos para cada navegador puede ser muy tedioso, además de ensuciar nuestro código. Por ello, como ya comentamos, no los usaremos y dejaremos que, gracias a este _postprocesador CSS_, automáticamente se agreguen los de las últimas versiones de los navegadores más usados.

## Css Comb

Es un formateador de código que reordena los valores CSS de manera consistente por tipo, y además **queda bonito**. Se puede configurar en diferentes IDEs y de diferentes maneras (plugins, node.js…)
