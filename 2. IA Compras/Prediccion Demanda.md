

Semama 1 2 3 4 5 6 7 8 9 10
Ventas 500 410 0 454 0 347 496 335 497 382

Te proporciono una tabla donde se muestras las ventas por semana de un producto.
Hay 10 semanas. Calcula las predición de ventas para la semana 11.
No expliques los calculos. Solo muestra el resultado. 


Muestra como la prediccion basada en los siguientes métodos:
- Regresión Lineal Simple: Incluye todos los datos.
- Regresión Lineal (Ajustada): 	Excluye valores 0 por atípicos/falta de stock.
- Promedio Móvil (Últimas 3 semanas)	Basado en semanas 8, 9 y 10.
- Promedio Histórico Simple: Incluye todos los datos.
- Promedio Histórico (Ajustado)	Excluye valores 0


Instrucción: Actúa como un analista de datos experto en Python. Genera un script completo utilizando matplotlib, numpy y pandas para representar gráficamente una comparativa de pronósticos de ventas.

Datos de Entrada:

Histórico (Semanas 1 a 10): [500, 410, 0, 454, 0, 347, 496, 335, 497, 382]

Horizonte de proyección: Semanas 11 a 15.

Modelos a Representar:

Ventas Históricas: Línea continua negra con marcadores circulares.

Regresión Lineal Simple (Todos los datos): Proyección ajustada por mínimos cuadrados considerando las 10 semanas.

Regresión Lineal Ajustada (Excluyendo ceros): Proyección ajustada eliminando las semanas 3 y 5 (valores 0 por rotura de stock).

Promedio Móvil (3 semanas): Valor constante basado en la media de las semanas 8, 9 y 10.

Promedio Histórico Simple: Valor constante basado en la media de las 10 semanas.

Promedio Histórico Ajustado: Valor constante basado en la media de las 8 semanas con ventas mayores a 0.

Requisitos Visuales de la Gráfica:

Estilo general: Gráfica limpia y profesional de alta resolución (dpi=300), tamaño 12x6.

Líneas de proyección: Utiliza líneas discontinuas con marcadores para cada modelo de predicción, diferenciando claramente cada uno con colores estándar.

Divisoria: Incluye una línea vertical punteada en la semana 10.5 que marque el "Inicio Proyección".

Ejes y Leyendas: Configura los ticks del eje X del 1 al 15, añade rejilla tenue (grid), título descriptivo, etiquetas de ejes en español y una leyenda organizada en la esquina superior izquierda sobre fondo blanco semitransparente.

Formato de salida: El código debe ser ejecutable directamente y guardar la imagen final en formato PNG.