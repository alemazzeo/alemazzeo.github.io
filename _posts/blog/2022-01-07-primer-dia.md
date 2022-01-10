---
title: "Sumarse a un proyecto en curso"
categories: Blog
tags:
  - Python
  - Buenas prácticas de desarrollo
  - Listas comprendidas
---

Podemos estar de acuerdo que la experiencia personal que tengamos en 
programación, los tutoriales que hayamos seguido o incluso los trabajos
personales que hayamos realizado no nos preparan para unirnos a un equipo de
desarrollo con un proyecto en curso.

Si es nuestra primera experiencia de trabajo colaborativo puede preocuparnos el 
no sentirnos aptos para la tarea, no comprender las consignas o siquiera saber 
por dónde empezar. Quiero contar algunas experiencias de este tipo que parecen
ser bastante comunes y razonables en esta nota y quizás en otras.

Suele suceder que la propuesta de trabajo que recibimos (escrita o explicada por
personal técnico) sea insuficiente para imaginarnos cómo nos vamos a desenvolver
o qué vamos a hacer el primer día.

Si el proyecto se encuentra en curso y mínimamente estructurado, es muy probable
que nos tengan una tarea específica para comenzar (a menos que hayamos mentido
en nuestro CV y tengamos un cargo como lider del proyecto).

{% include video id="rBSM4TAgK-E" provider="youtube" %}

Pongo por caso un ejemplo real. Nos integramos a un equipo que trabaja con IA y
tiene un gran volumen de datos sin procesar. Los datos se encuentran dispersos
en un montón de directorios, con errores de tipeo, con una codificación no UTF-8
que desconocíamos. Nos odian? No. Es re normal este escenario.

Algunos proyectos requieren en sus inicios que clonemos algún repositorio,
preparemos algún entorno virtual u otras tareas inciales. Trataré de incluir
recomendaciones para estas tareas en otro post. Por ahora vayamos al ejemplo que
di recién, donde nos alcanza con que nos proporcionen un zip con los datos a
estudiar y que sepamos escribir un script en Python.

La primera etapa siempre debería ser la investigación y las pequeñas pruebas de
factiblidad. Quizás tengamos que salir a buscar como se hacen algunas cosas y
otras ya las conozcamos pero las tengamos que refrescar o poner a prueba.

Es momento de mirar el cuadro en pared que lleva la frase de Donald Knuth:
"La optimización prematura es la raíz de todos los males". No empecemos por
pensar una estructura de archivos para tratar este problema. No busquemos el
código más eficiente, no probemos más de una forma válida de hacer una cosa
mientras hay otras tareas aún sin resolver.

Empecemos por un archivo suelto, un `prueba.py`. Cómo dije arriba tenemos varias
cosas para ir completando pero no quiero mostrar como se hace el trabajo
completo. En su lugar prefiero ver como una misma tarea se va mejorando en cada
momento de nuestro trabajo.

Necesitamos encontrar montones de archivos con extensión .txt dentro de 
subdirectorios. Googleamos un poco y recordamos que hay varias opciones 
(`os.walk`, `glob.glob`, `pathlib`)y nos quedamos con una, por ejemplo 
[pathlib](https://docs.python.org/es/3.10/library/pathlib.html).

Hacemos entonces una prueba básica:

```python
import pathlib

path = pathlib.Path("ruta_destino")

for x in path.rglob(""):
    print(x)
```

Lo probamos haciendo `python prueba.py` y vemos en consola una lista de
archivos .txt con sus rutas correspondientes. Funciona. Continuamos trabajando
con el resto de las pruebas que necesitamos hacer, todas en `prueba.py`.

Llegado un punto, queremos combinar las piezas. Por ejemplo, para cada ruta
hallada queremos (por algún motivo) aplicar algún filtro. Ya tenemos la lógica
de ese filtro probada en una sentencia `if`.

Para continuar probando nuestro desarrollo podríamos hacer algo así:

```python
for ruta_archivo in resultado_busqueda:
    if <logica ya implementada>:
        <hacer cosas>
```

y efectivamente nos serviría para hacer pruebas rápidas. Estaríamos avanzando
súper rápido en probar nuestras ideas e investigar las posiblidades.

En algún momento la mayoría de las ideas estarán probadas, ya tendremos frescas
las herramientas a utilizar y vamos a querer hacer un script de verdad. Empieza
una divertida etapa de refactorizaciones (las primeras, no las definitivas).
Esta etapa podría continuar hasta el infinito, así que tendremos que 
conformarnos con algunas y no retrasar la primera muestra de nuestro trabajo.

Por ejemplo, si en algún momento mientras armamos el "primer entregable" notamos 
que necesitamos <sic> copiar y pegar nuestro `for ... if` en más de un lugar, 
sabremos que era un resultado que nos convenía almacenar el resultado. Vale por 
ejemplo hacer lo siguiente:

```python
resultados_filtrados = []
for ruta_archivo in resultado_busqueda:
    if <cierta_condicion>:
        resultados_filtrados.append(ruta_archivo)
```

Pero con el tiempo notaremos que hay un esquema que nos empuja a hacer las cosas
de una forma mejor, las listas comprendidas:

```python
resultados_filtrados = [
    ruta_archivo
    for ruta_archivo in resultado_busqueda
    if <cierta_condicion>
]
```

Produce el mismo resultado, pero ya veremos que nos obliga a hacer las cosas de
otra forma. Por ejemplo, no nos permite poner una logica complicada de selección
en un mismo bloque (nos empuja a crear una función que haga de filtro). Y a eso
quería llegar.

Si necesitamos probar diferentes filtros notaremos que lo mejor sería tener una 
función que reciba la ruta del archivo. Eso nos permite realizar el cambio más 
fácilmente, pero también poner a prueba el filtro en contextos controlados 
(unit-testing). Nuestro código mejora:

```python
resultados_filtrados = [
    ruta_archivo
    for ruta_archivo in resultado_busqueda
    if funcion_filtro(ruta_archivo)
]
```

Lo mismo si necesitamos aplicarle una transformación a la ruta antes de que sea
almacenada:

```python
resultados_filtrados = [
    transforma(ruta_archivo)
    for ruta_archivo in resultado_busqueda
    if funcion_filtro(ruta_archivo)
]
```

Ahora la tarea es clara de leer (hay una *lista* que proviene de *transformar*
aquellos resultados que cumplan con un *filtro*). Y la transformación y el 
filtro son funciones que podemos probar fuera de nuestro código. Además, en el
esquema de escribir listas comprendidas no podemos hacer cualquier cosa. Con el
tiempo uno ve que el uso de esta herramienta nos empuja a programar de formas
parecidas, claras, en cierto modo predecibles.

Y llegado este punto alguien me podría decir: "pero yo ni conocía las listas
comprendidas, nunca hubiese llegado a este punto". Yo tampoco, y de eso se trata
esta experiencia que quería contar. El trabajo en equipo comienza por cumplir
tareas específicas. Las personas que te acompañan miran tu código y te sugieren
estos cambios en forma gradual. El que está al lado quizás sabe muchísimo más
que vos de un tema, pero lo ves callado ante la presentación de otros, porque 
también está aprendiendo algo nuevo en ese momento.

Nadie se va a enojar por tu forma de hacer las cosas la primera vez que las 
hagas si estás dispuesto a escuchar lo que tengan para decirte. La labor de un
buen lider en ese momento será encontrar la dosis justa de mejoras que podés
asimilar (no te tiene que dejar seguir exactamente como venís ni tampoco tirarte
50 recomendaciones por la cabeza).

En un próximo post quiero comentar el escenario donde el acople es un poco más
largo (hay que instalar dependencias, clonar repositorios y reportar errores en
el primer día).

Saludos!
