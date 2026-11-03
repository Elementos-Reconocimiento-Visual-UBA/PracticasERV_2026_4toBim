# Guía de EDA: histología

**El problema:** A partir de un pedacito de un corte de tejido visto al microscopio, decir qué tejido es. Por ejemplo, en un tumor de colon, saber cuánto hay de tumor, de estroma o de linfocitos ayuda al médico a estimar el pronóstico del paciente.

**Qué hay en el dataset:** cortes de cáncer colorrectal, 300 por clase, achicados a 128 × 128. Los cortes están teñidos con **hematoxilina y eosina**: los **núcleos** de las células salen **violeta oscuro** y el citoplasma y las fibras salen **rosa**. Hay 8 clases: tumor, estroma, estroma complejo, linfocitos, restos, mucosa, grasa y fondo.

## Pistas para el EDA

Estas pistas no les dicen qué calcular: les dicen **dónde mirar**. Lo que encuentren es lo que tiene que guiar sus features.

- Hay dos clases que se ven casi en blanco. ¿Les hace falta textura para reconocer esas dos, o alcanza con el brillo? En este dataset el color solo ya llega lejos: la pregunta interesante es **qué clases quedan sin resolver** con el color.
- Cuánto violeta. Los núcleos son lo violeta oscuro. Midan cuánto de la imagen es núcleo en cada tejido. ¿Qué tejidos separa esa medida? Fíjense especialmente en **linfocitos y tumor**: ¿tienen mucho o poco violeta en comparación?
- Cómo es el violeta. Si la cantidad de núcleo no alcanza para separar dos tejidos, miren cómo son los núcleos: hagan zoom en linfocitos y en tumor. ¿Qué tamaño tienen y cómo están acomodados? ¿De cuántos píxeles es un núcleo?
- El rosa. Estroma, estroma complejo y restos son los que más se confunden. Miren varias de cada una lado a lado: ¿qué los diferencia? ¿Fibras ordenadas, células sueltas, desorden?
- El tinte. No sale igual en todos los cortes: algunos son más rosas y otros más violetas. ¿Cuánto cambia el color de una imagen a otra de la misma clase?
- La feature propia. Antes de agregar una, pregúntense: ¿lo que mide ya lo está midiendo el color o el LBP? Si sí, no va a sumar.

Si encuentran algo que el color o el LBP **no miden** tal cual, ahí tienen su **feature propia**.

Podrian llegar facil al 95%

## Las 2 preguntas que tienen que responder

1. ¿Hasta dónde llega el color solo, y qué clases necesitan textura? Muéstrenlo comparando la matriz de confusión de "solo color" con la de su mejor configuración.
2. ¿Qué escala (radio del LBP) funcionó mejor, y cómo se relaciona con el tamaño de los núcleos que vieron? (Si es que hacen LBP)

*Respóndanlas en las Conclusiones.*
