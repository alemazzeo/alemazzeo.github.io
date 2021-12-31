---
permalink: /projects/pysuppose
title: "PySuppose"
toc: true
---

### Estar en el lugar correcto, en el momento correcto

Cuando recibí esta oferta de trabajo mis esfuerzos estaban puestos en aprender 
más y más sobre computación  de alto rendimiento. Acababa de comprarme una 
notebook con una GPU de Nvidia para aprender a programar en CUDA cuando me 
ofrecieron reescribir un algoritmo de deconvolución en Python, convertirlo en 
un paquete de uso científico y acelerarlo haciendo uso de dos GTX 1080.

### El algoritmo Suppose

Una premisa sencilla: una técnica de deconvolución que utiliza muchas fuentes
virtuales para formar un objeto real. A cada paso, el algoritmo evalúa la 
función de respuesta del dispositivo de adquisición (PSF) en las posiciones
actuales y compara el resultado con la imagen objetivo. La optimización se lleva
a cabo mediante un algoritmo genético.

La evaluación condiciona fuertemente el tiempo requerido (ahí entra en juego
el aprovechamiento de la GPU). El algoritmo genético acepta múltiples variantes
que condicionan la convergencia. 

### Características de PySuppose

- Item 1
- Item 2
- Item 3

### Publicación científica
M. Toscani, A. Mazzeo, S. Martínez, O. Martínez, A. Lacapmesure and G. B. Vazquez, "Fuentes de error, artificios, aceleración y validación del algoritmo de deconvolución con super-resolución para imágenes de microscopía," 2020 IEEE Congreso Bienal de Argentina (ARGENCON), 2020, pp. 1-7, doi: 10.1109/ARGENCON49523.2020.9505479.

