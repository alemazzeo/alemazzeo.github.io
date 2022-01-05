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

Desarrollé el paquete PySuppose para permitir diferentes niveles de interacción.
En primer lugar, la interfaz facilita el uso principal del paquete: cargar una
muestra y aplicar el algoritmo para aumentar la resolución. 

En un segundo nivel existe la posibilidad de modificar partes específicas del 
algoritmo para poder experimentar con la convergencia del mismo. Podemos agrupar
dichas partes en dos subgrupos: el algoritmo genético y la generación de los
individuos iniciales.

Todo esto es posible gracias a un motor principal, que reune y verifica las
partes, además de permitir el agregado de pluggins para tareas específicas: 
visualización, debug, almacenamiento, etc.

En un nivel más avanzado se encuentran las librerías externas para la 
optimización de las evaluaciones, que se llevan a cabo cientos de veces en cada 
paso del algoritmo. El paquete PySuppose cuenta con su propia librería compilada
con CUDA para utilizar múltiples GPUs. Significó una reducción del tiempo de
cómputo de aproximadamente 80 veces. Esta sección dio lugar a un desarrollo
específico, CaTMU, pero ese ya tiene su propia entrada.

### Publicación científica
M. Toscani, A. Mazzeo, S. Martínez, O. Martínez, A. Lacapmesure and G. B. Vazquez, "Fuentes de error, artificios, aceleración y validación del algoritmo de deconvolución con super-resolución para imágenes de microscopía," 2020 IEEE Congreso Bienal de Argentina (ARGENCON), 2020, pp. 1-7, doi: 10.1109/ARGENCON49523.2020.9505479.

