---
permalink: /projects/catmu
title: "CaTMU"
gallery1:
  - url: /assets/images/catmu/catmu4.png
    image_path: /assets/images/catmu/catmu4.png
    alt: "Convolución por expresión"
    title: "Convolución por expresión"
  - url: /assets/images/catmu/catmu5.png
    image_path: /assets/images/catmu/catmu5.png
    alt: "Convolución por LUT"
    title: "Convolución por LUT"
  - url: /assets/images/catmu/catmu8.png
    image_path: /assets/images/catmu/catmu8.png
    alt: "Ventajas de la convolución LUT"
    title: "Ventajas de la convolución LUT"
  - url: /assets/images/catmu/catmu6.png
    image_path: /assets/images/catmu/catmu6.png
    alt: "Caracterización de errores"
    title: "Caracterización de errores"
  - url: /assets/images/catmu/catmu7.png
    image_path: /assets/images/catmu/catmu7.png
    alt: "Caracterización de errores"
    title: "Caracterización de errores"
  - url: /assets/images/catmu/catmu9.png
    image_path: /assets/images/catmu/catmu9.png
    alt: "Caracterización de errores"
    title: "Caracterización de errores"
gallery2:
  - url: /assets/images/catmu/catmu1.png
    image_path: /assets/images/catmu/catmu1.png
    alt: "Tiempos en CPU"
    title: "Tiempos en CPU"
  - url: /assets/images/catmu/catmu2.png
    image_path: /assets/images/catmu/catmu1.png
    alt: "Tiempos en GPU"
    title: "Tiempos en CPU"
  - url: /assets/images/catmu/catmu3.png
    image_path: /assets/images/catmu/catmu1.png
    alt: "Tiempos en GPU + TMU"
    title: "Tiempos en GPU + TMU"
---

Mi trabajo sobre el algoritmo Suppose me llevó a investigar a fondo las
herramientas disponibles en la GPU. En general, en la GPU es preferible realizar
cálculos antes que utilizar una LUT (Lookup Table), salvo ciertos casos.

![Mapeo de texturas](https://upload.wikimedia.org/wikipedia/commons/f/f2/Texture_mapping_demonstration_animation.gif){: .align-left}

Un nuevo requerimiento de PySuppose limitó la posiblidad de hacer cálculos,
obligandome a buscar una solución por el camino de la LUT. Encontré entonces un
poderoso recurso de la GPU: la Unidad de Mapeo de Texturas. Una pieza de 
hardware incorporado en la GPU con la capacidad de acceder de forma eficiente y
cacheada a la memoria, interpolar valores y devolver resultados.

{% include gallery id="gallery1" caption="Presentación al equipo de desarrollo" %}

Decidí armar un paquete externo a PySuppose para explorar esta herramienta y
validar los resultados obtenidos (por ejemplo caracterizar el error cometido).
Durante el desarrollo cambié la forma en que me comunicaba con la GPU, 
facilitando el multithreading posterior y con ello el uso de múltiples tarjetas.

PySuppose y su librería significó para el algoritmo Suppose una reducción de 
tiempos en un factor 80. CaTMU redujo esos nuevos tiempos 10 veces más.

{% include gallery id="gallery2" caption="Presentación de reducción de tiempos en la RAFA 2020" %}

Para mi agrado, este nuevo paquete externo a PySuppose sirvió para propósitos
que no esperaba. CaTMU fue combinado con técnicas de deep learning, Suppose y
Compressed Sensing en un nuevo trabajo a cargo de Axel Lacapmesure, cuya
publicación ya pasó el peer review y se encuentra en post-producción.
