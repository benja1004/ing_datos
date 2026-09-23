# Teoría – Capítulo 3 - Parte 2: Experimentos Estadísticos y Pruebas de Significancia

Este capítulo introduce los fundamentos de las pruebas de significancia estadística, el remuestreo (*resampling*), el valor *p* y la prueba **t**, herramientas utilizadas para determinar si las diferencias observadas entre grupos pueden atribuirse al azar o representan un efecto estadísticamente significativo.

---

# 1. Resampling (Remuestreo)

El **remuestreo** (*resampling*) es una técnica estadística que consiste en generar múltiples muestras a partir de un conjunto de datos observado para estimar la variabilidad de un estadístico y evaluar hipótesis sin depender estrictamente de supuestos teóricos sobre la distribución de los datos.

## Tipos principales de remuestreo

### Bootstrap

El **Bootstrap** genera nuevas muestras **con reemplazo** a partir de los datos originales. Se utiliza para estimar:

- Error estándar.
- Intervalos de confianza.
- Estabilidad de un estimador.

### Permutation Test (Prueba de Permutación)

La **Prueba de Permutación** realiza remuestreo **sin reemplazo** y evalúa si dos o más grupos provienen de la misma población.

Su principal ventaja es que **no requiere asumir normalidad** en los datos.

## Hipótesis en una prueba de permutación

- **Hipótesis nula (H₀):** No existe diferencia entre los grupos; cualquier diferencia observada se debe al azar.
- **Hipótesis alternativa (H₁):** Existe una diferencia real entre los grupos.

## Procedimiento del Permutation Test

1. Combinar todos los datos en un solo conjunto.
2. Mezclar aleatoriamente las observaciones.
3. Dividir nuevamente los datos respetando el tamaño original de cada grupo.
4. Calcular el estadístico de interés (por ejemplo, diferencia de medias).
5. Repetir el proceso muchas veces para construir la **distribución de permutación**.
6. Comparar el valor observado con la distribución generada.

## Distribución de permutación

Después de repetir el procedimiento **R** veces, se obtiene una distribución empírica del estadístico:

<math block value="\\{T_1,T_2,\\ldots,T_R\\}"/>

Esta distribución representa los resultados esperados si la hipótesis nula fuera verdadera.

## Ventajas del Permutation Test

- No requiere asumir una distribución normal.
- Es intuitivo y fácil de implementar con programación.
- Permite evaluar la significancia directamente a partir de los datos observados.

---

# 2. Significancia Estadística

La **significancia estadística** indica qué tan probable es observar un resultado igual o más extremo que el obtenido, suponiendo que la hipótesis nula es verdadera.

Su objetivo es determinar si la evidencia observada es suficiente para rechazar la hipótesis nula.

## Valor p (p-value)

El **valor p** es la probabilidad de obtener un resultado tan extremo como el observado bajo la hipótesis nula.

<math block value="p=P(\\text{Resultado tan extremo como el observado}\\mid H_0)"/>

### Interpretación

- **Valor p pequeño:** La evidencia es poco compatible con H₀.
- **Valor p grande:** Los datos son compatibles con H₀.

> El valor p **no** representa la probabilidad de que la hipótesis nula sea verdadera.

## Nivel de significancia (α)

El **nivel alfa** es un umbral previamente definido para tomar una decisión estadística.

Valores comunes:

| Nivel α | Interpretación |
|---------|----------------|
| 0.10 | 10% de riesgo de Error Tipo I. |
| 0.05 | Nivel más utilizado en investigación. |
| 0.01 | Evidencia estadística más estricta. |

## Regla de decisión

<math block value="\\text{Si }p<\\alpha,\\ \\text{se rechaza }H_0"/>

<math block value="\\text{Si }p\\ge\\alpha,\\ \\text{no se rechaza }H_0"/>

No rechazar H₀ **no significa** demostrar que H₀ sea verdadera; únicamente indica que no existe evidencia suficiente para rechazarla.

## Errores estadísticos

### Error Tipo I (Falso Positivo)

Rechazar H₀ cuando en realidad es verdadera.

<math block value="P(\\text{Error Tipo I})=\\alpha"/>

### Error Tipo II (Falso Negativo)

No rechazar H₀ cuando en realidad es falsa.

Su probabilidad suele representarse por:

<math block value="\\beta"/>

La **potencia estadística** de una prueba es:

<math block value="1-\\beta"/>

## Significancia estadística vs. significancia práctica

Una diferencia puede ser **estadísticamente significativa** pero tener un efecto muy pequeño en la práctica, especialmente cuando el tamaño de muestra es muy grande.

Por ello, además del valor p, es recomendable analizar:

- Magnitud del efecto.
- Diferencia de medias o proporciones.
- Intervalos de confianza.

---

# 3. Prueba t (T-Test)

La **prueba t de Student** es una prueba de hipótesis utilizada para comparar las medias de dos grupos y determinar si la diferencia observada puede explicarse por la variabilidad aleatoria.

## Hipótesis

Para comparar dos medias:

<math block value="H_0:\\ \\mu_1=\\mu_2"/>

<math block value="H_1:\\ \\mu_1\\neq\\mu_2"/>

## Estadístico t

El estadístico **t** estandariza la diferencia entre medias considerando la variabilidad de las muestras.

<math block value="t=\\frac{\\bar{x}_1-\\bar{x}_2}{SE}"/>

Donde:

- <math value="\\bar{x}_1,\\bar{x}_2"/> = medias de los grupos.
- <math value="SE"/> = error estándar de la diferencia de medias.

## Distribución t de Student

La distribución t:

- Tiene forma similar a la distribución normal.
- Posee colas más anchas.
- Depende de los **grados de libertad**.

Cuando el tamaño de muestra aumenta, la distribución t se aproxima a la distribución normal.

## Grados de libertad (Degrees of Freedom)

Los grados de libertad representan la cantidad de información independiente disponible para estimar la variabilidad.

En una prueba t para dos muestras independientes:

<math block value="df=n_1+n_2-2"/>

En la prueba de Welch, los grados de libertad se estiman mediante una fórmula que considera varianzas diferentes entre grupos.

## Tipos de prueba t

### t-Test de Student

Se utiliza cuando se asume que ambos grupos tienen varianzas iguales.

### t-Test de Welch

Se utiliza cuando las varianzas pueden ser diferentes entre grupos.

Es la versión más utilizada en ciencia de datos porque resulta más robusta ante diferencias de varianza.

## Interpretación del resultado

Una prueba t devuelve:

- Estadístico t.
- Valor p.
- Grados de libertad.

La decisión se toma comparando el valor p con el nivel de significancia α.

---

# Relación entre Permutation Test y T-Test

Ambos métodos evalúan la misma hipótesis: si existe una diferencia significativa entre dos grupos.

| Permutation Test | T-Test |
|------------------|--------|
| Remuestreo sin reemplazo. | Basado en una distribución teórica. |
| No requiere normalidad. | Supone independencia y una aproximación mediante la distribución t. |
| Construye una distribución empírica. | Calcula un estadístico t y un valor p. |
| Flexible para distintos tipos de datos. | Muy eficiente para comparar medias. |

En la práctica, ambos pueden producir conclusiones similares cuando los supuestos del T-Test se cumplen y el tamaño de muestra es suficiente.

---

# Conceptos clave

- **Resampling:** Técnica para generar múltiples muestras a partir de los datos observados.
- **Permutation Test:** Prueba no paramétrica que evalúa diferencias entre grupos mediante permutaciones aleatorias.
- **Hipótesis nula (H₀):** Supone ausencia de diferencia o efecto.
- **Hipótesis alternativa (H₁):** Supone existencia de una diferencia o efecto.
- **Valor p:** Probabilidad de obtener un resultado igual o más extremo bajo H₀.
- **Nivel α:** Umbral para decidir si un resultado es estadísticamente significativo.
- **Error Tipo I:** Detectar un efecto inexistente (falso positivo).
- **Error Tipo II:** No detectar un efecto existente (falso negativo).
- **T-Test:** Prueba estadística para comparar medias de dos grupos utilizando el estadístico t.
- **Distribución t:** Distribución de referencia utilizada para calcular la significancia del estadístico t.
- **Grados de libertad:** Parámetro que determina la forma de la distribución t según el tamaño de la muestra.
