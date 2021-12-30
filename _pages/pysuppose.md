---
permalink: /projects/pysuppose
title: "PySuppose"
toc: true
---

Estar en el lugar correcto, en el momento correcto. Cuando recibí esta oferta
de trabajo mis esfuerzos estaban puestos en aprender más y más sobre computación
de alto rendimiento. Acababa de comprarme una notebook con una GPU de Nvidia
para aprender a programar en CUDA cuando me ofrecieron reescribir un algoritmo 
de deconvolución en Python, convertirlo en un paquete de uso científico y 
acelerarlo haciendo uso de dos GTX 1080.

Una premisa sencilla: una técnica de deconvolución que utiliza muchas fuentes
virtuales para formar un objeto real. A cada paso, el algoritmo evalúa la 
función de respuesta del dispositivo de adquisición (PSF) en las posiciones
actuales y compara el resultado con la imagen objetivo. La optimización se lleva
a cabo mediante un algoritmo genético.

La evaluación condiciona fuertemente el tiempo requerido (ahí entra en juego
el aprovechamiento de la GPU). El algoritmo genético acepta múltiples variantes
que condicionan la convergencia. 

El desarrollo tuvo dos etapas de desarrollo relacionadas, pero independientes:

### Desarrollo en Python de un motor para algoritmos genéticos (PySuppose)
Desarrollé una librería capaz de gestionar
- Librería completamente funcional con backend y frontend
- Conexión a rutinas desarrolladas en C y CUDA mediante CTYPES
- Desarrollo de rutinas en CUDA para la deconvolución del algoritmo Suppose
- Multithreading como mediador de la interacción entre las partes
- Paralelización en múltiples GPU
- 
### Desarrollo de un paquete para el aprovechamiento de la Unidad de Mapeo de Texturas (TMU) de la GPU (Catmu)
- Integración de la nueva herramienta en PySuppose
- 
### Publicaciones realizadas:
- M. Toscani, A. Mazzeo, S. Martínez, O. Martínez, A. Lacapmesure and G. B. Vazquez, "Fuentes de error, artificios, aceleración y validación del algoritmo de deconvolución con super-resolución para imágenes de microscopía," 2020 IEEE Congreso Bienal de Argentina (ARGENCON), 2020, pp. 1-7, doi: 10.1109/ARGENCON49523.2020.9505479.
- (Próximamente) Combining deep learning with SUPPOSe and Compressed Sensing for SNR-enhanced localization of overlapping emitters 
