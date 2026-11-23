# Organizar Transporte

Actúa como un experto en optimización de transporte, planificación de rutas y Vehicle Routing Problem (VRP).

Necesito resolver y representar visualmente el siguiente problema de distribución.

## 1. Escenario

Tenemos:
- 1 almacén central: AL
- 8 clientes: A, B, C, D, E, F, G, H
- 3 camiones
- Cada cliente necesita 3 entregas
- Total: 24 entregas
- Cada entrega: 200 kg / 2 pallets
- Capacidad de cada camión: 1.200 kg / 12 pallets
- Jornada operativa: 07:00–16:00
- Cada ruta debe comenzar y terminar en AL
- Tiempo de descarga por entrega: 20 minutos
- Coste conducción: 1,20 €/km
- Coste horas extra: 37,50 €/hora
- Los clientes A y B tienen prioridad.
- Cliente A tiene ventana horaria 08:00–10:00.
- Considera que 18 km equivalen aproximadamente a 25 minutos de conducción.

## 2. Matriz de distancias

Distancias en km:

|     | AL | A | B | C | D | E | F | G | H |
|-----|----|---|---|---|---|---|---|---|---|
| AL  | 0  | 12| 30| 30| 46| 26| 46| 38| 54|
| A   | 12 | 0 | 18| 18| 34| 38| 34| 50| 42|
| B   | 30 | 18| 0 | 20| 16| 32| 20| 32| 24|
| C   | 30 | 18| 20| 0 | 16| 40| 16| 52| 24|
| D   | 46 | 34| 16| 16| 0 | 48| 12| 48| 8 |
| E   | 26 | 38| 32| 40| 48| 0 | 48| 12| 56|
| F   | 46 | 34| 20| 16| 12| 48| 0 | 52| 8 |
| G   | 38 | 50| 32| 52| 48| 12| 52| 0 | 56|
| H   | 54 | 42| 24| 24| 8 | 56| 8 | 56| 0 |

## 3. Objetivo de optimización

Determina cómo organizar las rutas para mañana.

Prioriza los objetivos en este orden:

1. Cumplir las ventanas horarias, especialmente A 08:00–10:00.
2. Cumplir las 24 entregas.
3. No superar la capacidad del camión en ningún momento.
4. Minimizar kilómetros totales.
5. Minimizar horas totales de conducción.
6. Minimizar horas extra.
7. Minimizar el coste total de transporte.

Ten en cuenta que un camión puede volver a AL para recargar y realizar una nueva ruta durante la misma jornada si resulta necesario.

## 4. Resultado esperado

No quiero únicamente una explicación textual.

Primero calcula una solución de rutas factible y después genera una representación visual clara.

### A. Resumen ejecutivo

Indica:

- kilómetros totales
- tiempo total estimado
- coste estimado de conducción
- horas extra, si existen
- coste total
- número de entregas realizadas
- utilización aproximada de cada camión

### B. Plan por camión

Para cada camión muestra explícitamente la secuencia:

CAMIÓN 1
AL → Cliente X → Cliente Y → Cliente Z → AL
AL → Cliente ... → AL

CAMIÓN 2
AL → ...

CAMIÓN 3
AL → ...

Si existen varias rutas o viajes para un mismo camión, mostrarlos como:
- Ruta 1
- Ruta 2
- Ruta 3

Para cada parada indica:
- cliente
- hora estimada de llegada
- hora estimada de salida
- pallets entregados
- kg entregados
- km desde la parada anterior
- km acumulados
- pallets restantes en el camión

### C. Visualización principal

Genera una visualización tipo mapa/esquema logístico.

Debe aparecer:
- AL como almacén central
- Clientes A, B, C, D, E, F, G y H
- Los 3 camiones
- Las rutas completas de cada camión

Utiliza un color diferente para cada camión:
- Camión 1: azul
- Camión 2: naranja
- Camión 3: verde

Dibuja líneas y flechas conectando las paradas siguiendo el orden real:

AL → parada 1 → parada 2 → parada 3 → ... → AL

Sobre cada cliente muestra:
- nombre del cliente
- número de orden de la parada
- hora aproximada de llegada

Las líneas deben representar el recorrido, no simplemente conectar todos los clientes.

Si un camión realiza más de una ruta desde AL, debe verse claramente el regreso al almacén y el inicio de la siguiente ruta.

Añade una leyenda identificando Camión 1, Camión 2 y Camión 3.

IMPORTANTE:
La matriz proporciona distancias pero no coordenadas geográficas. Por tanto, NO inventes posiciones geográficas reales. Utiliza un esquema de red logística (network diagram) para mostrar las rutas.

### D. Timeline operativo

Debajo del mapa genera una línea temporal de 07:00 a 16:00 con tres filas:

Camión 1 | [conducción] [cliente] [descarga] [conducción] ...
Camión 2 | [...]
Camión 3 | [...]

Diferencia visualmente:
- conducción
- descarga
- estancia en AL / recarga
- tiempo de espera
- horas extra

### E. Tabla final

Genera una tabla:

| Camión | Ruta | Salida AL | Clientes | Regreso AL | Km | Tiempo | Entregas | Pallets | Coste |
|--------|------|-----------|----------|------------|----|--------|----------|---------|-------|

Incluye una fila TOTAL.

## 5. Validación obligatoria

Antes de dar la solución final verifica:

- 8 clientes servidos.
- Exactamente 24 entregas.
- 48 pallets entregados.
- 4.800 kg entregados.
- Ningún camión transporta simultáneamente más de 12 pallets / 1.200 kg.
- Cliente A recibe servicio dentro de 08:00–10:00.
- Todas las rutas comienzan y terminan en AL.
- Los cálculos de kilómetros utilizan exclusivamente la matriz proporcionada.
- Los tiempos de conducción utilizan la relación 18 km = 25 minutos.
- Cada entrega añade 20 minutos de descarga.

Si alguna condición no puede cumplirse, NO la ignores:
identifica el conflicto, explica la causa y propone la modificación mínima necesaria.

## 6. Presentación

El resultado debe ser apto para presentarlo a un responsable de transporte u operaciones.

Primero muestra visualmente la solución y después explica las decisiones.

El objetivo principal es poder entender en menos de 30 segundos:

1. Qué hace el Camión 1.
2. Qué hace el Camión 2.
3. Qué hace el Camión 3.
4. Qué clientes visita cada uno.
5. En qué orden.
6. A qué hora.
7. Cuándo vuelve cada camión a AL.
8. Si se cumplen las 24 entregas dentro de la jornada.
