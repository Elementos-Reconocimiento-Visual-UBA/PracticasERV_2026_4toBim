# Guía de EDA: porotos

**El problema:** a partir de una foto de una hoja de poroto, decir si está **sana**, si tiene **mancha angular** o si tiene **roya**. Por ejemplo, son dos enfermedades que arruinan cosechas enteras en África y en América Latina, y detectarlas temprano con un celular es un caso real.

**Qué hay en el dataset:** fotos sacadas con celular en el campo, en Uganda (Makerere AI Lab), 300 por clase, achicadas a 128 × 128.

## Pistas para el EDA

Estas pistas no les dicen qué calcular: les dicen **dónde mirar**. Lo que encuentren es lo que tiene que guiar sus features.

- **El fondo**. Miren varias fotos de hojas sanas: ¿de qué color es la tierra? Ahora piensen en un histograma de color de toda la foto: ¿puede distinguir "marrón de tierra" de "marrón de enfermedad"? Midan cuánto "marrón" tiene una hoja sana, y comparen con las enfermas.
- **Separar la hoja**. ¿Se puede separar la hoja del fondo ? Si después quieren contar manchas, ¿qué pasa si cuentan en toda la foto? ¿Cuentan también las sombras del suelo?
- **Las dos enfermedades**. Roya y mancha angular son las dos "marrón sobre verde", y es el par que más se confunde. Hagan zoom en varias de cada una: ¿en qué se diferencian las manchas? ¿Cantidad, tamaño, forma, si tienen borde amarillo? ¿Alguna de esas diferencias se puede convertir en un número?
- **La escala**. A 128 × 128, ¿de cuántos píxeles es una pústula de roya? 
- **La luz**. Hay fotos a pleno sol y fotos a la sombra. Comparen el brillo promedio entre fotos de la **misma** clase: ¿cambia más dentro de una clase o entre clases? ¿Conviene confiar en el brillo?

Si encuentran algo que el color o el LBP **no miden** tal cual, ahí tienen su **feature propia**.

Deberian poder llegar aprox al 85%

## Las 2 preguntas que tienen que responder

1. ¿Todo el marrón de una foto es enfermedad? ¿Cómo afecta eso a sus features, y qué hicieron al respecto?
2. ¿Qué par de clases se confunde más en su matriz de confusión? Mirando las imágenes, ¿qué tienen en común esos errores?

*Respóndanlas en las Conclusiones.*
