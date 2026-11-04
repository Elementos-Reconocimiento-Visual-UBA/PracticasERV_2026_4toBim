# Guía de EDA: satélite 

**El problema:** a partir de una imagen satelital, decir qué hay en el suelo. Es lo que se usa para hacer mapas de uso del suelo, seguir la deforestación o medir cuánto crece una ciudad.

**Qué hay en el dataset:** EuroSAT, imágenes del satélite Sentinel-2 de 64 × 64 píxeles, 300 por clase. Cada píxel son 10 m, así que cada imagen muestra un cuadrado de unos 640 m de lado. Hay 10 clases: cultivo anual, cultivo permanente, pastura, vegetación herbácea, bosque, río, mar o lago, autopista, industrial y residencial.

## Pistas para el EDA

Estas pistas no les dicen qué calcular: les dicen **dónde mirar**. Lo que encuentren es lo que tiene que guiar sus features.

- **El color de cada clase.** Pongan lado a lado el color promedio de cada clase. ¿Cuáles parecen distintas y cuáles son "el mismo verde"? ¿qué clases va a reconocer un modelo que solo mira el color, y cuáles no?
- **El agua.** ¿Es siempre azul? Comparen varias imágenes de mar o lago con varias de bosque: ¿hay algunas que se parezcan en color? Si se parecen en color, ¿en qué otra cosa se diferencian?
- **Los cuatro verdes.** Cultivo anual, cultivo permanente, pastura y vegetación herbácea. Tapen el color (miren las imágenes en gris): ¿se distinguen mejor o peor? ¿Qué cambia entre ellas, el color o el "dibujo"?
- **La autopista.** Es la clase más difícil. Miren varias: ¿cuánto de la imagen ocupa la ruta y cuánto lo que hay alrededor? ¿Con qué otras clases se puede confundir por lo que hay **alrededor**?
- **Autopista y río.** Las dos son una franja que cruza la imagen. A 64 × 64, ¿de cuántos píxeles de ancho es una autopista? Si prueban detectar líneas rectas, ¿las encuentra en imágenes tan chicas? Miren el resultado antes de usarlo como feature.
- **La escala.** pueden jugar con ella?

Si encuentran algo que el color o el LBP **no miden** tal cual, ahí tienen su **feature propia**.

Podrian llegar al 85%

## Las 2 preguntas que tienen que responder

1. ¿Qué clases **no** se pueden separar solo con el color? ¿Qué agregó la textura (LBP, OTRO COLOR, FEATURE PROPIA)? Muéstrenlo con su tabla de configuraciones.
2. Autopista y río: ¿se confunden en su modelo? ¿Qué las distingue, y alguna de sus features lo captura? (Respondan solo si les sucede esto)

*Respóndanlas en las Conclusiones.*
