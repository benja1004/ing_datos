# Pruebas A/B y pruebas de hipótesis



Basada en el capítulo 3 de *Practical Statistics for Data Scientists*

## 1. Introducción

Los experimentos estadísticos permiten estudiar el efecto de una modificación y comparar alternativas a partir de datos. En ciencia de datos se utilizan, por ejemplo, para evaluar diseños de páginas web, precios y anuncios. Sin embargo, que una alternativa obtenga un resultado mayor en una muestra no demuestra, por sí solo, que sea mejor en la población. La diferencia también puede aparecer como consecuencia de la variación aleatoria.

Esta monografía tiene como objetivo explicar las pruebas A/B y las pruebas de hipótesis, así como la relación entre ambas. Se desarrolla una adaptación en español de las secciones correspondientes del capítulo 3 de Bruce, Bruce y Gedeck (2020, pp. 88–96), acompañada de ejemplos del libro e interpretaciones didácticas. El alcance se concentra en estos dos temas; los procedimientos de remuestreo y el cálculo de valores p corresponden a otras partes del trabajo grupal.

## 2. Pruebas A/B

Una prueba A/B es un experimento que compara dos tratamientos, productos o procedimientos mediante una medida de resultado. Un tratamiento es la condición a la que se expone una unidad experimental; no necesariamente se refiere a un medicamento. Puede ser un precio, un título de una página o un diseño. Los sujetos, por su parte, son las unidades que reciben esa condición, como personas, visitantes web o semillas (Bruce et al., 2020, p. 88).

Con frecuencia, A representa la opción habitual y B una propuesta nueva. La opción habitual funciona como control: proporciona una referencia para interpretar el resultado de la modificación. No obstante, las letras A y B solo identifican las alternativas; no indican de antemano cuál será superior.

### 2.1. Asignación aleatoria y grupo de control

La asignación aleatoria distribuye los sujetos entre los tratamientos mediante el azar. Su propósito es reducir los sesgos de selección y favorecer grupos comparables. No asegura que ambos grupos sean idénticos: todavía pueden existir diferencias accidentales en su composición. Por eso, incluso en un experimento bien diseñado, los resultados pueden variar por azar.

El control permite comparar las alternativas en condiciones semejantes. Si una tienda cambia su página y después vende más, el incremento también podría relacionarse con una campaña publicitaria o con una temporada de mayor demanda. Comparar simultáneamente la versión habitual y la nueva ayuda a separar estas influencias del cambio estudiado (Bruce et al., 2020, pp. 90–91).

### 2.2. La medida de evaluación

Antes de iniciar el experimento debe elegirse una medida principal relacionada con el objetivo. Si interesa aumentar las compras, puede utilizarse la tasa de conversión, es decir, la proporción de visitantes que compran. Si interesa el rendimiento económico, podría elegirse el ingreso por visita. Estas medidas responden a preguntas diferentes: una opción puede producir más compras, pero no necesariamente más ingresos por visitante.

Bruce et al. (2020, p. 91) advierten que seleccionar la medida después de observar los resultados abre la puerta al sesgo del investigador. En otras palabras, se podría escoger únicamente el indicador que favorece a la alternativa preferida. La decisión sobre qué significa “mejor” debe formar parte del diseño inicial del experimento.

### 2.3. Ejemplos de aplicación del libro

El libro menciona comparaciones entre dos tratamientos de suelo, dos precios, dos títulos web y dos anuncios. En el caso de los títulos, la pregunta es cuál genera más clics. La figura siguiente representa esta idea: se reparten visitantes al azar, cada grupo observa una versión y se registra la misma medida de respuesta.

```mermaid
flowchart LR
    V[Visitantes de la página] --> R[Asignación aleatoria]
    R --> A[Grupo A: título habitual]
    R --> B[Grupo B: título alternativo]
    A --> MA[Medir proporción de clics]
    B --> MB[Medir proporción de clics]
```

Figura 1. Esquema propio de una prueba A/B, inspirado en el ejemplo de títulos web de Bruce et al. (2020, pp. 88–89, figura 3-2). No reproduce la imagen original.

Un ejemplo con datos aparece en la tabla 3-1 del libro, donde se comparan dos precios en un experimento de comercio electrónico. La información se presenta a continuación, con los totales y las tasas calculados a partir de los datos originales.

| Resultado | Precio A | Precio B |
|---|---:|---:|
| Compras (conversiones) | 200 | 182 |
| Sin compra | 23 539 | 22 406 |
| Total de observaciones | 23 739 | 22 588 |
| Tasa de conversión | 0,842 % | 0,806 % |

Tabla 1. Adaptación de la tabla 3-1 de Bruce et al. (2020, p. 90). Los totales y porcentajes son cálculos propios.

La tasa de A se obtiene dividiendo 200 entre 23 739 y multiplicando por 100; la de B, dividiendo 182 entre 22 588. A presenta una ventaja observada de aproximadamente 0,037 puntos porcentuales. Como los grupos tienen tamaños distintos, es más informativo comparar tasas que únicamente contar compras. Aun así, esta diferencia descriptiva no basta para concluir que A tenga una tasa poblacional mayor: es necesario evaluar la incertidumbre mediante una prueba apropiada.

## 3. Pruebas de hipótesis

Las pruebas de hipótesis permiten evaluar si los datos observados son compatibles con una suposición de referencia. En el contexto de un experimento A/B, ayudan a examinar si la variación aleatoria constituye una explicación razonable de la diferencia entre grupos. Su utilidad consiste en evitar que una fluctuación accidental se interprete inmediatamente como un efecto del tratamiento (Bruce et al., 2020, pp. 93–94).

La prueba A/B y la prueba de hipótesis cumplen funciones diferentes dentro del mismo proceso. La primera organiza la comparación y permite recoger los datos; la segunda aporta un marco para analizarlos. Además, las pruebas de hipótesis pueden aplicarse a otros problemas estadísticos y no se limitan a experimentos A/B.

### 3.1. Hipótesis nula e hipótesis alternativa

La hipótesis nula, representada como H₀, establece la suposición de referencia. En una comparación bilateral de tasas de conversión puede expresar que las tasas poblacionales son iguales. Esto no significa que las proporciones observadas en las muestras deban coincidir exactamente: bajo igualdad poblacional también pueden aparecer diferencias muestrales debidas al azar.

La hipótesis alternativa, H₁, expresa la posibilidad que se contrapone a la nula. Si p_A y p_B representan las tasas de conversión poblacionales de las dos opciones, las hipótesis de una comparación bilateral se escriben así:

> H₀: p_A = p_B.
> H₁: p_A ≠ p_B.

El análisis parte de un modelo bajo H₀ y examina qué tan compatible resulta la diferencia observada con ese modelo. Si la evidencia cumple el criterio de rechazo establecido, se rechaza H₀. Si no lo cumple, no se rechaza. Esta última decisión no demuestra que las alternativas sean iguales: expresa que los datos no proporcionan evidencia suficiente para rechazar la hipótesis nula.

### 3.2. Pruebas unilaterales y bilaterales

Una prueba unilateral considera una dirección específica. Por ejemplo, si se investiga si la nueva opción B aumenta la tasa de conversión respecto de A, la alternativa plantea que la tasa de B es mayor. En esta situación, las hipótesis son:

> H₀: p_B ≤ p_A.
> H₁: p_B > p_A.

Una prueba bilateral, en cambio, busca diferencias en cualquiera de las dos direcciones. Se utiliza cuando interesa saber si B cambia la tasa, tanto si la incrementa como si la reduce. En ese caso se emplean las hipótesis de igualdad y desigualdad presentadas anteriormente. El libro desarrolla esta distinción a partir de la decisión de conservar una opción habitual o sustituirla por una nueva (Bruce et al., 2020, p. 95).

La elección debe responder a la pregunta de investigación y realizarse antes de observar los resultados. Elegir la dirección después de descubrir qué grupo obtuvo una tasa mayor introduciría un sesgo. Por ello, formular las hipótesis no es un trámite posterior, sino una parte del diseño del análisis.

### 3.3. Ejemplo del libro: las rachas de una moneda

Para explicar por qué podemos interpretar mal el azar, el libro propone pedir a varias personas que inventen una secuencia de 50 lanzamientos de una moneda y que después realicen 50 lanzamientos reales. Las secuencias reales tienden a incluir rachas más largas de caras o sellos que las inventadas. Esto ocurre porque, al inventar una serie, solemos alternar los resultados demasiado pronto para que parezcan aleatorios (Bruce et al., 2020, pp. 93–94).

```text
C  C  C  C  C  S  C  S  S  C

C = cara; S = sello. Secuencia ilustrativa.
```

Figura 2. Ilustración propia del concepto de racha. La secuencia mostrada no corresponde a resultados reportados en el libro.

La enseñanza es que una racha llamativa no demuestra por sí misma la existencia de una causa especial. De manera semejante, un título web puede superar a otro en una muestra sin que exista una ventaja poblacional. Las pruebas de hipótesis permiten evaluar esa observación dentro de un modelo de variación aleatoria, en lugar de depender únicamente de la impresión que produce el resultado.

## 4. Interpretación de los temas

A partir de la lectura, se entiende que comparar resultados implica dos responsabilidades: realizar una comparación adecuada e interpretar sus diferencias con cuidado. La asignación aleatoria, el control y la elección previa de una medida contribuyen a la primera. La formulación de hipótesis y el análisis de la evidencia contribuyen a la segunda.

En el ejemplo de los precios, contar 200 compras para A y 182 para B no es suficiente para afirmar que A sea mejor. Primero deben considerarse los tamaños de los grupos; después debe evaluarse si la diferencia entre tasas es compatible con el azar. Además, una mayor tasa de compra no equivale necesariamente a una mayor rentabilidad. La conclusión debe corresponder a la medida que se decidió estudiar.

## 5. Conclusiones

Las pruebas A/B permiten comparar dos alternativas bajo un diseño experimental. Su interpretación mejora cuando los sujetos se asignan al azar, las condiciones son comparables y la medida principal se define antes de recoger los datos.

Las pruebas de hipótesis complementan esta comparación al evaluar los resultados respecto de una hipótesis nula. Distinguir entre hipótesis nula y alternativa, así como entre pruebas unilaterales y bilaterales, permite formular con claridad la pregunta que se desea responder.

Finalmente, una diferencia observada no debe confundirse con una demostración automática de superioridad. El aporte principal de estos temas es aprender a tomar decisiones a partir de evidencia, reconociendo que los resultados de una muestra también están sujetos a variación aleatoria.

## Referencia bibliográfica

Bruce, P., Bruce, A., & Gedeck, P. (2020). *Practical statistics for data scientists: 50+ essential concepts using R and Python* (2nd ed.). O’Reilly Media.

Secciones consultadas: “A/B Testing”, pp. 88–92, y “Hypothesis Tests”, pp. 93–96. La numeración corresponde a las páginas impresas del libro. Texto adaptado y explicado en español; figuras de elaboración propia.

## Anexo. Ejemplo en Python

Este código utiliza las compras y los totales de la tabla 3-1 del libro (p. 90). Es una ampliación didáctica propia, no una transcripción del código de los autores. Se ejecuta con Python 3 y no requiere paquetes externos. Compara las tasas mediante una prueba z bilateral aproximada, sin corrección de continuidad.

Se supone que los grupos se asignaron al azar y que las observaciones son independientes, con una respuesta binaria por unidad. La aproximación normal es razonable con estos conteos de compras y no compras. La hipótesis nula plantea tasas poblacionales iguales; la alternativa, tasas diferentes. Se fija un nivel de significación de 0,05 antes del análisis.

```python
from math import sqrt, erfc

compras_a, n_a = 200, 23739
compras_b, n_b = 182, 22588
tasa_a = compras_a / n_a
tasa_b = compras_b / n_b
alfa = 0.05

# Proporcion comun y error estandar bajo H0
p = (compras_a + compras_b) / (n_a + n_b)
error = sqrt(p * (1-p) * (1/n_a + 1/n_b))
z = (tasa_a - tasa_b) / error
p_valor = erfc(abs(z) / sqrt(2))

print(f"A: {tasa_a:.3%}; B: {tasa_b:.3%}")
print(f"Diferencia: {100*(tasa_a-tasa_b):.3f} puntos porcentuales")
print(f"z: {z:.3f}; valor p: {p_valor:.3f}")
if p_valor < alfa:
    print("Se rechaza H0")
else:
    print("No se rechaza H0")
```

### Resultado e interpretación

El resultado es A = 0,842 %, B = 0,806 %, diferencia = 0,037 puntos porcentuales, z = 0,437 y valor p = 0,662. Las diferencias se calculan antes de redondear. Como 0,662 es mayor que 0,05, no se rechaza la hipótesis nula con esta prueba. No se ha demostrado que las tasas sean iguales ni que una opción sea más rentable.

En el código, *p* estima la proporción común bajo H₀, *error* mide la variabilidad esperada de la diferencia y *z* expresa la diferencia en unidades de ese error. La función *erfc* permite calcular el área de las dos colas de la distribución normal estándar. El valor p no es la probabilidad de que H₀ sea verdadera.

Los métodos y la dirección del contraste importan: una prueba unilateral o un procedimiento de remuestreo pueden producir otro valor p. Este anexo ilustra una elección concreta y complementa la explicación conceptual del capítulo. Archivo ejecutable: [ejemplo_ab_angel.py](ejemplo_ab_angel.py).
