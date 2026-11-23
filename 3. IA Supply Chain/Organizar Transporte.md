Actúa como especialista en optimización de transporte, planificación de rutas y Excel.

Necesito resolver un problema de Vehicle Routing Problem, VRP, y entregar el resultado exclusivamente en un archivo Excel .xlsx. El Excel debe contener tanto los datos de entrada como la solución propuesta, los cálculos, la validación de restricciones y una explicación ejecutiva.

## 1. Objetivo

Planificar las rutas de mañana para:

- 8 clientes: A, B, C, D, E, F, G y H.
- 3 camiones.
- 24 entregas en total.
- 3 entregas por cliente.
- Salida y regreso al almacén AL.
- Prioridad alta para los clientes A y B.
- Minimizar:
  1. kilómetros totales;
  2. horas de conducción y operación;
  3. horas extra;
  4. coste total;
  5. desequilibrio de carga entre los camiones.

Cada cliente debe ser atendido y todas las entregas deben quedar asignadas.

## 2. Datos operativos

### Entregas

- Cada cliente recibe 3 entregas.
- Cada entrega pesa 800 kg.
- Cada entrega ocupa 2 pallets.
- Demanda total por cliente:
  - 2.400 kg;
  - 6 pallets.
- Demanda total:
  - 19.200 kg;
  - 48 pallets.

### Capacidad de cada camión

- Capacidad máxima: 3.500 kg.
- Capacidad máxima: 12 pallets.
- Número de camiones: 3.

### Horarios

- Ventana cliente A: 08:00–10:00.
- Ventana cliente B: 08:00–10:00.
- Resto de los clientes: sin ventana específica indicada. Utilizar como límite el horario operativo del camión.
- Horario disponible de los camiones: 07:00–16:00.
- Tiempo de descarga: 20 minutos por cliente visitado.
- Todos los camiones salen y regresan al almacén AL.

### Conversión de distancia a tiempo

- 18 km equivalen a 25 minutos.
- Velocidad media equivalente: 43,2 km/h.
- Tiempo de viaje en minutos = distancia × 25 / 18.

## 3. Matriz de distancias en kilómetros

La matriz es simétrica.

| Origen/Destino | AL | A | B | C | D | E | F | G | H |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| AL | 0 | 12 | 30 | 30 | 46 | 26 | 46 | 38 | 54 |
| A  | 12 | 0 | 18 | 18 | 34 | 38 | 34 | 50 | 42 |
| B  | 30 | 18 | 0 | 20 | 16 | 32 | 20 | 32 | 24 |
| C  | 30 | 18 | 20 | 0 | 16 | 40 | 16 | 52 | 24 |
| D  | 46 | 34 | 16 | 16 | 0 | 48 | 12 | 48 | 8 |
| E  | 26 | 38 | 32 | 40 | 48 | 0 | 48 | 12 | 56 |
| F  | 46 | 34 | 20 | 16 | 12 | 48 | 0 | 52 | 8 |
| G  | 38 | 50 | 32 | 52 | 48 | 12 | 52 | 0 | 56 |
| H  | 54 | 42 | 24 | 24 | 8 | 56 | 8 | 56 | 0 |

## 4. Supuestos que deben utilizarse

- Las 3 entregas de un mismo cliente pueden consolidarse en una única visita.
- Por tanto, cada cliente genera:
  - una parada;
  - 2.400 kg;
  - 6 pallets;
  - 20 minutos de descarga.
- Debido a la capacidad de 12 pallets y 3.500 kg, un camión puede transportar como máximo la demanda consolidada de un cliente por viaje:
  - dos clientes supondrían 4.800 kg, superando los 3.500 kg;
  - por tanto, cada viaje transportará la mercancía de un único cliente.
- Un mismo camión puede realizar varios viajes durante el día, regresando al almacén entre viajes para recargar.
- El tiempo de carga en el almacén no se ha proporcionado. Utilizar inicialmente 0 minutos, pero incluir en Excel una celda editable llamada “Tiempo de carga por viaje” para realizar simulaciones.
- Priorizar las entregas A y B dentro de sus ventanas de 08:00 a 10:00.
- Si la llegada se produce antes de las 08:00, contabilizar el tiempo de espera.
- No inventar carreteras, coordenadas, tráfico ni distancias diferentes de las proporcionadas.
- Utilizar siempre la matriz de distancias facilitada.
- Si no existe una solución totalmente viable, identificar claramente la restricción incumplida y proponer la mínima modificación operativa necesaria.

## 5. Método de resolución

Resolver el problema como un Multi-Trip Capacitated Vehicle Routing Problem with Time Windows:

- Multi-Trip CVRP.
- Capacidad limitada por peso y pallets.
- Ventanas horarias para A y B.
- Tres vehículos.
- Múltiples viajes por vehículo.
- Salida y regreso a AL en cada viaje.

Puedes utilizar:

- programación lineal entera;
- búsqueda exhaustiva;
- heurística de ahorro de Clarke-Wright adaptada;
- algoritmo nearest-neighbour con mejora 2-opt;
- algoritmo genético;
- OR-Tools si está disponible.

La solución debe ser reproducible y no debe basarse únicamente en una estimación visual.

## 6. Costes editables

Incluir en el Excel una hoja de parámetros con celdas editables para:

- Coste por kilómetro.
- Coste por hora normal.
- Coste por hora extra.
- Tiempo de carga por viaje.
- Hora de inicio.
- Hora de fin.
- Peso por entrega.
- Pallets por entrega.
- Número de entregas por cliente.
- Capacidad de peso del camión.
- Capacidad de pallets del camión.

Si no se facilitan importes de coste, utilizar inicialmente:

- Coste por kilómetro: 1,20 €/km.
- Coste por hora normal: 25 €/hora.
- Coste por hora extra: 37,50 €/hora.

Marcar claramente estos valores como “supuestos editables”.

## 7. Estructura obligatoria del Excel

Crear un archivo llamado:

Planificacion_Rutas_8_Clientes_3_Camiones.xlsx

El archivo debe contener las siguientes hojas.

### Hoja 1: Resumen ejecutivo

Incluir:

- número de clientes;
- número de entregas;
- número de camiones;
- número total de viajes;
- kilómetros totales;
- horas totales;
- coste total;
- utilización media de peso;
- utilización media de pallets;
- horas extra;
- entregas dentro de ventana;
- entregas fuera de ventana;
- indicador general:
  - VIABLE;
  - VIABLE CON RIESGOS;
  - NO VIABLE.

Añadir un resumen de la solución por camión.

### Hoja 2: Datos y parámetros

Incluir todos los parámetros operativos y costes.

Diferenciar por colores:

- celdas de entrada manual;
- celdas calculadas;
- resultados;
- alertas o incumplimientos.

### Hoja 3: Matriz de distancias

Incluir la matriz completa AL–H.

Crear también una matriz de tiempos calculada mediante:

Tiempo en minutos = Distancia × 25 / 18

### Hoja 4: Demanda clientes

Una fila por cliente con:

- cliente;
- prioridad;
- entregas;
- kg por entrega;
- pallets por entrega;
- kg totales;
- pallets totales;
- inicio de ventana;
- fin de ventana;
- tiempo de descarga;
- estado de asignación.

### Hoja 5: Plan de rutas

Una fila por tramo o movimiento, con las columnas:

- Camión.
- Viaje.
- Secuencia.
- Origen.
- Destino.
- Cliente.
- Hora de salida.
- Tiempo de viaje.
- Hora de llegada.
- Inicio de descarga.
- Fin de descarga.
- Tiempo de espera.
- Distancia.
- Peso transportado.
- Pallets transportados.
- Utilización de peso.
- Utilización de pallets.
- Regreso al almacén.
- Hora de fin del viaje.
- Cumplimiento de ventana.
- Cumplimiento de capacidad.
- Observaciones.

Usar fórmulas de Excel siempre que sea posible.

### Hoja 6: Resumen por camión

Una fila por camión con:

- clientes asignados;
- secuencia de viajes;
- número de viajes;
- hora de inicio;
- hora de finalización;
- km totales;
- tiempo de viaje;
- tiempo de descarga;
- tiempo de carga;
- tiempo de espera;
- horas normales;
- horas extra;
- coste por kilómetros;
- coste de horas normales;
- coste de horas extra;
- coste total;
- utilización media;
- estado de viabilidad.

### Hoja 7: Validación

Comprobar automáticamente:

- todos los clientes están asignados;
- existen exactamente 24 entregas;
- cada cliente recibe 3 entregas;
- ningún viaje supera 3.500 kg;
- ningún viaje supera 12 pallets;
- A está atendido entre 08:00 y 10:00;
- B está atendido entre 08:00 y 10:00;
- los camiones terminan antes de las 16:00;
- todos los viajes empiezan y terminan en AL;
- no existen clientes duplicados o sin asignar.

Mostrar cada control como:

- OK;
- WARNING;
- ERROR.

### Hoja 8: Comparativa

Crear al menos dos escenarios:

1. Escenario optimizado.
2. Escenario alternativo equilibrando mejor el trabajo entre los tres camiones.

Comparar:

- kilómetros;
- duración;
- horas extra;
- coste;
- cumplimiento de ventanas;
- utilización;
- riesgo operativo.

Recomendar el mejor escenario y justificar la decisión.

### Hoja 9: Gantt

Crear un gráfico de Gantt operativo con:

- eje horizontal de 07:00 a 16:00;
- una línea por camión;
- viajes;
- conducción;
- descarga;
- espera;
- carga en almacén.

Utilizar colores diferentes para cada actividad.

## 8. Fórmulas y controles

Incluir fórmulas, no solamente valores estáticos.

Ejemplos:

- Peso total cliente = Entregas × kg por entrega.
- Pallets totales = Entregas × pallets por entrega.
- Tiempo de viaje = Distancia × 25 / 18 / 1440.
- Hora llegada = Hora salida + Tiempo de viaje.
- Hora fin descarga = Inicio descarga + 20 / 1440.
- Utilización peso = Peso / 3.500.
- Utilización pallets = Pallets / 12.
- Horas extra = MAX(0; Hora final - 16:00).
- Cumplimiento capacidad = SI(Y(Peso<=3500;Pallets<=12);"OK";"ERROR").
- Cumplimiento ventana = comprobar llegada e inicio de servicio contra la ventana asignada.

Utilizar fórmulas compatibles con Excel y evitar referencias rotas.

## 9. Presentación

El Excel debe ser profesional y apto para una reunión operativa:

- encabezados claros;
- filtros;
- paneles congelados;
- formatos de hora HH:MM;
- formato de moneda en euros;
- formato condicional;
- rojo para incumplimientos;
- ámbar para riesgos;
- verde para cumplimiento;
- gráficos legibles;
- leyenda de colores;
- columnas ajustadas;
- sin celdas con errores #N/A, #VALUE!, #REF! o #DIV/0!.

## 10. Resultado obligatorio

No respondas únicamente con una explicación textual.

Genera y entrega el archivo Excel .xlsx completo y descargable.

Antes de terminar:

1. abre o valida el archivo generado;
2. comprueba todas las fórmulas;
3. confirma que las 24 entregas están incluidas;
4. confirma que A y B cumplen la ventana 08:00–10:00;
5. confirma que ningún viaje supera peso o pallets;
6. confirma que los tres camiones regresan a AL;
7. confirma que el archivo no contiene errores de fórmula.

Incluye dentro de la hoja “Resumen ejecutivo” una conclusión operativa y una lista de riesgos y acciones recomendadas.
