---
permalink: /projects/gigapixel
title: "Gigapixel"
categories: Proyectos Experiencia
tags: 
  - Python 
  - C
  - Docker
  - JavaScript 
  - TypeScript 
  - Flask 
  - Bootstrap
  - Arduino 
  - Electrónica 
  - Tornería 
  - Taller 
  - Óptica
toc: true
hidden: true
---

El proyecto desde su origen consistió en el diseño y desarrollo de un
Microscopio de Pticografía de Fourier (FPM) y el software para la adquisición,
reconstrucción y análisis de las muestras.

### El prototipo de factibilidad

Mi participación del proyecto comenzó en las materias de Laboratorio 6 y 7.
El requerimiento principal era la entrega de un informe de factibilidad.
El software de reconstrucción se encontraba operativo (realizado por mi
compañero). Empecé trabajando en el diseño y construcción del microscopio en sí.

Haciendo uso del taller del laboratorio fabriqué un prototipo en aluminio capaz
de sostener la óptica (un microscopio conjugado infinito) sobre la fuente de 
iluminación (una matriz de leds de 32x32). La electrónica y el software de
control existentes corrían sobre una Raspberry, expuesta como servicio web en la
red. Juntando este desarrollo con el software de adquisición realizamos las
primeras reconstrucciones.

### La primera exploración de las muestras

Dado que las muestras reconstruídas son realmente pesadas (del orden del 
gigapixel), se necesito un visor del tipo piramidal para la exploración de las
mismas. Realicé una primera interfaz de visualización web utilizando 
OpenSeaDragon y herramientas web como Bootstrap. La primera entrega, el informe
de factibilidad, sólo conoció este primer visualizador/anotador.

### El análisis de la fase reconstruida

Como parte de la materia Laboratorio 7, estudié la dependencia de la fase
reconstruída con el indice de refracción de los materiales y su espesor. Realicé
simulaciones y caractericé los resultados obtenidos.

### El nuevo anotador de muetras Gigapixel

Por pandemia, y también por la falta de algunos insumos, nos volcamos al
desarrollo remoto. En ese contexto, realicé un anotador web de muestras (pensado
para la tarea propuesta, pero también de uso genérico y con potencial para
muestras médicas). Este nuevo anotador usa una herramienta de front-end llamada
W2UI para la interfaz gráfica, OpenSeaDragon para las muestras piramidáles y
PaperJS para las tareas de anotación. Permite la anotación por capas y comunica
los resultados a un backend de base de datos para el almacenamiento.

### Mejorando el anotador

En paralelo comencé una segunda versión del anotador, ahora en TypeScript.
Espero poder dejar un mejor producto final para que este anotador pueda ser
utilizado por la comunidad en general.

### El nuevo microscopio, ahora con materiales de Thorlabs Cerna

Utilizando piezas de Thorlabs preparamos una nueva entrega del microscopio,
ahora mucho más robusto. Trabajando en conjunto con un grupo de diseñadoras
industriales agregamos al microscopio una carcaza y nuevas funcionalidades.

Para la versión a entregar fue indispensable simplificar los drivers y el
algoritmo de adquisición. Para la cámara utilicé directamente el SDK. Mediante
CTypes conecté el driver existente de la cámara (.so) con Python. Para la
iluminación opté por reformular la electrónica. En lugar de utilizar el driver
existente (pensado para renderizar imágenes y por lo tanto sujeto a un barrido)
por uno propio implementado en Arduino. Armé un "shield" provisorio e investigué
los métodos de control de la pantalla hasta dar con la solución. Luego, se
adquirió un "shield" de Adafruit para mejorar la versión entregada.

### Interfaz de adquisición Web

En primer lugar desarrollé una interfaz de adquisición por consola (utilizando
el paquete Click de Python). Definí bien las interfaces necesarias y luego pasé
al desarrollo web. Usando plantillas diseñadas con Bootstrap y un backend en
Flask implementé una solución para controlar la adquisición, configurar los
parámetros y facilitar al usuario final el uso del microscopio.

