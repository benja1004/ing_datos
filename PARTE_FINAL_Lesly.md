PRUEBA CHI CUADRADA:
Es una prueba de hipótesis no paramétrica utilizada para determinar si existe una relación estadísticamente significativa o asociación entre dos variables categóricas. Permite evaluar si las frecuencias observadas en cada categoría difieren de manera sustancial de las frecuencias que se esperarían si ambas variables fueran totalmente independientes entre sí. Se aplica ampliamente en investigaciones donde los datos se organizan en tablas de contingencia.

Estadístico Chi-cuadrado (χ²): cuantifica la discrepancia entre las frecuencias observadas en la muestra y las frecuencias esperadas bajo la hipótesis nula de independencia o de bondad de ajuste. Se calcula mediante la fórmula: χ² = Σ [(Oᵢ − Eᵢ)² / Eᵢ], donde O ′ representa los valores observados y Eᵢ representa los valores esperados. Cuando la diferencia entre lo observado y lo esperado es reducida, el valor de χ² tiende a cero, lo que sugiere que las variaciones se deben únicamente al azar. Por el contrario, un valor grande de χ² indica una diferencia significativa, lo que conduce al rechazo de la hipótesis nula. El p-valor correspondiente se obtiene al comparar el valor calculado con la distribución Chi-cuadrado considerando los grados de libertad específicos del análisis, los cuales en tablas de contingencia se calculan como (filas − 1) × (columnas − 1).

Expectativas o Resultados Esperados: Representan los valores teóricos o frecuencias que se anticipa obtener bajo la asunción de una hipótesis nula (H₀), la cual postula la ausencia de relación, diferencia o efecto entre las variables analizadas. En el contexto de las pruebas de independencia mediante Chi-cuadrado, las frecuencias esperadas (Eᵢ) reflejan la distribución ideal de las observaciones si las variables bajo estudio fueran numéricamente independientes.

ENFOQUE DE REMUESTREO: 
Supuestos y Condiciones de Aplicación:
Independencia de las observaciones: Las observaciones deben ser estrictamente independientes entre sí. Esto implica que cada individuo o unidad experimental debe ser registrado una sola vez y pertenecer a una única casilla de la tabla de contingencia, evitando medidas repetidas o datos emparejados.
Tamaño muestral y frecuencias esperadas suficientes: El tamaño de la muestra debe ser lo suficientemente grande para asegurar la validez de la aproximación a la distribución Chi-cuadrado. Como regla general, las frecuencias esperadas en cada celda de la tabla de contingencia no deben ser menores a 5. Si existen celdas con valores esperados inferiores a 5, la prueba pierde precisión, por lo que se recomienda recurrir a técnicas alternas como la prueba exacta de Fisher o utilizar un enfoque de remuestreo (bootstrapping o pruebas de permutación).

Ejemplo: En relación del nivel educativo y el género

HIPÓTESIS NULA: No hay relación donde el género determina el nivel educativo.

HIPÓTESIS ALTERNATIVA: Existe una relación donde el género determina el nivel educativo.

FRECUENCIA OBSERVADA
![alt text](imagen1.png)

FÓRMULA DE PRUEBA DE INDEPENDENCIA

![alt text](imagen2.png)

FRECUENCIA ESPERADA
![alt text](imagen3.png)

FÓRMULA DEL RESIDUO DE PEARSON 
![alt text](imagen4.png)

Observado: 30
Esperado: 27.5
Cálculo: R = (30 - 27.5)/ RAÍZ(27.5) = 2.5/5.244 = 0.477


TABLA DEL RESIDUO DE PEARSON 

![alt text](imagen5.png)

FÓRMULA DEL RESIDUO DE PEARSON 

![alt text](imagen6.png)

r x c = filas x columnas 

TABLA DEL RESIDUO DE PEARSON 

![alt text](imagen7.png)

X = 0.227 + 0.132 + 0.109 + 0.357 + 0.227 + 0.132 + 0.109 + 0.357
X = 1.649
Explorar diferentes opciones para aprender de ellas y recopilar nueva información sobre el rendimiento de cada alternativa.

ALGORITMO MULTI-ARM BANDIT
Reasigna el tráfico de forma automática y en tiempo real, enviando más usuarios o recursos a la variante ganadora.

EXPLOTACIÓN
Quedarse con la mejor opción que uno observa hasta ahora para maximizar los beneficios inmediatos basados en la experiencia previa.


EPSILON - GREEDY
Epsilon (ε) es el parámetro que define qué porcentaje del tiempo nos atrevemos a probar éxito e investigar nuevas opciones (exploración), frente al tiempo dedicado a elegir la mejor alternativa actual (explotación).

ε = 1 (Exploración total)
A pesar de que haya tenido más pulsaciones el botón rojo, se seguirán mostrando los 3 al mismo tiempo, repartiendo el tráfico equitativamente entre todas las variantes sin importar su desempeño histórico.

ε = 0 (Explotación total)
Conformarse exclusivamente con la primera opción que dé resultados positivos, asignándole todo el tráfico sin descubrir si existía una alternativa superior.

EVOLUCIÓN BAYESIANA
A medida que se acumula evidencia, el algoritmo aprende y actualiza sus distribuciones a priori, estrechando progresivamente la curva de probabilidad de cada opción para ajustar la asignación de recursos con mayor certidumbre.

POTENCIA Y TAMAÑO DE MUESTRA
Conceptos y términos clave para determinar la potencia estadística y el tamaño adecuado de la muestra:

Tamaño mínimo del efecto detectable (MDE): Es la magnitud mínima de la diferencia o impacto que esperamos ser capaces de detectar mediante una prueba estadística, como por ejemplo "una mejora del 20 % en las tasas de clics".
Potencia estadística (1 - β): Es la probabilidad de detectar verdaderamente el tamaño de un efecto dado con un tamaño de muestra determinado, evitando así cometer un error de Tipo II (falso negativo).
Nivel de significación (α): El umbral de riesgo o nivel de significación estadística bajo el cual se realizará la prueba, definiendo la máxima probabilidad tolerable de cometer un error de Tipo I (falso positivo).
