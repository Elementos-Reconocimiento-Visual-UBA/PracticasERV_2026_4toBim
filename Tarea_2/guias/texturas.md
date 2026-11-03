# Guía de EDA: texturas

**El problema:** a partir de una foto, decir qué patrón tiene: cuadriculado, agrietado, con puntos, grilla, panal, rayado, tejido o zigzag. 

**Qué hay en el dataset:** 8 de las 47 clases del *Describable Textures Dataset* (DTD), 120 fotos por clase, sacadas de internet. Cada foto se corta en 4 recortes de 128 × 128. Los 4 recortes de una misma foto quedan **siempre** en el mismo conjunto (entrenamiento, validación o prueba), porque si no el modelo vería "casi la misma imagen" al entrenar y al evaluar.

## Pistas para el EDA

Estas pistas no les dicen qué calcular: les dicen **dónde mirar**. Lo que encuentren es lo que tiene que guiar sus features.

- **El color.** ¿Tienen las rayadas un color en común? ¿Y las de puntos? ¿Qué esperan que pase con un histograma de color? Y una pregunta más fina: si suman el color a sus features de textura, ¿el modelo mejora, queda igual o empeora? ¿Por qué podría empeorar algo al agregarle información?
- **La escala.** ¿Las rayas son finas en unas fotos y gruesas en otras? Comparen el LBP con un solo radio contra varios radios juntos: ¿con un solo tamaño de vecindario alcanza?
- **La orientación.** Miren 10 fotos rayadas: ¿las rayas van siempre en la misma dirección? Si una feature mide "cuánto cambia la imagen hacia la derecha", ¿qué le pasa cuando la foto está girada? ¿Cómo podrían resumir varias direcciones en algo que no dependa del giro?
- **La periodicidad.** Algunas texturas **se repiten** con un período fijo y otras no. Miren el espectro de Fourier de una imagen de cada clase: ¿cuáles tienen picos marcados y cuáles una mancha difusa?
- **Las confusiones.** Grilla y tejida, agrietada y panal: miren varias de cada par lado a lado. ¿Qué tienen en común? ¿Qué las diferencia, si es que algo las diferencia?

Si encuentran algo que el color o el LBP **no miden** tal cual, ahí tienen su **feature propia**. En este dataset es donde más se nota: el LBP solo se queda corto.

Pueden llegar al 65% tal vez más con buenas features

## Las 2 preguntas que tienen que responder

1. La orientación de la textura cambia entre fotos de la misma clase. ¿Qué hicieron para que sus features no dependan de eso? ¿Se nota en los resultados?
2. ¿Qué clases son periódicas, y cómo se ve eso en el espectro de Fourier? ¿Sirvió alguna feature basada en eso?

*Respóndanlas en las Conclusiones.*
