Este es un prompt completo y reutilizable. Incluye tanto el contenido como las reglas de cálculo y diseño del Excel.

Actúa como un experto en Procurement, gestión de proveedores, industria del vidrio y modelización avanzada en Excel.

Tu objetivo es crear un archivo Excel profesional y completamente funcional para construir una Matriz de Kraljic de una PYME fabricante y transformadora de **vidrio** para construcción.

El archivo debe estar pensado tanto para utilizarse como herramienta real de Procurement como para emplearse en una formación dirigida a PYMEs del sector del **vidrio, Climalit y materiales de construcción**.

## 1. Objetivo del archivo

Crea un dataset ficticio, pero realista, con 30 categorías de compra de una PYME fabricante de vidrio.

El Excel debe permitir:

- Evaluar el impacto de cada categoría en el negocio.
- Evaluar su riesgo de suministro.
- Calcular automáticamente un `Impact Score`.
- Calcular automáticamente un `Supply Risk Score`.
- Clasificar automáticamente cada categoría en uno de los cuatro cuadrantes de la Matriz de Kraljic.
- Cambiar los pesos y umbrales del modelo.
- Identificar una estrategia de compras recomendada para cada categoría.
- Sustituir posteriormente los datos ficticios por información real de una empresa.

La unidad principal de análisis debe ser la categoría de compra, no el proveedor individual.

## 2. Estructura del libro Excel

Crea las siguientes cuatro hojas, en este orden:

1. `Resumen`
2. `Dataset`
3. `Parametros`
4. `Guia y fuentes`

Todas las fórmulas deben permanecer visibles, editables y trazables.

No conviertas los resultados calculados en valores fijos.

## 3. Hoja “Dataset”

Incluye 30 categorías de compra. Utiliza categorías realistas como las siguientes:

1. Vidrio float 4 mm
2. Vidrio float 6 mm
3. Vidrio Low-E
4. Vidrio de control solar
5. Vidrio laminado estándar
6. Vidrio templado subcontratado
7. PVB estándar
8. PVB acústico especial
9. Intercalario de aluminio
10. Intercalario warm edge
11. Sellante estructural de silicona
12. Butyl o sellante primario
13. Desecante molecular
14. Gas argón
15. Perfiles de aluminio
16. Herrajes para cerramientos
17. Junquillos y perfiles de PVC
18. Cajas de madera y caballetes
19. Film protector y cantoneras
20. EPIs
21. Discos y herramientas de corte
22. Repuestos del horno de templado
23. Repuestos de la línea IGU
24. Mantenimiento preventivo de hornos
25. Electricidad
26. Gas natural
27. Transporte nacional de vidrio
28. Transporte especial con A-frame
29. Servicios de calibración
30. Material de oficina y limpieza

Genera datos ficticios coherentes para todas ellas.

Por ejemplo:

- El vidrio float debe tener un gasto elevado, varios proveedores y bajo o moderado riesgo.
- El vidrio Low-E debe tener gasto e impacto elevados, con menos proveedores y mayor dependencia técnica.
- El PVB acústico debe tener pocos proveedores, lead time alto y dificultad de sustitución.
- Los repuestos del horno deben tener bajo o moderado gasto, proveedor único, lead time muy alto y coste de parada elevado.
- Los EPIs y materiales de oficina deben tener bajo impacto y bajo riesgo.
- La electricidad y el gas deben mostrar gasto y volatilidad elevados.
- Los transportes especiales deben tener más riesgo que el transporte nacional estándar.

## 4. Columnas del dataset

Incluye las siguientes columnas:

1. ID
2. Categoría de compra
3. Familia
4. Gasto anual (€)
5. % del gasto total
6. Impacto en margen (1-5)
7. Criticidad para producción (1-5)
8. Coste de parada (1-5)
9. Score de gasto
10. Impact Score
11. Número de proveedores homologados
12. Concentración en el proveedor principal
13. Lead time en días
14. Sustituibilidad (1-5)
15. Riesgo del proveedor (1-5)
16. Volatilidad de precio (1-5)
17. Riesgo geográfico (1-5)
18. Score del número de proveedores
19. Score de concentración
20. Score de lead time
21. Supply Risk Score
22. Cuadrante Kraljic
23. Estrategia recomendada
24. Ejemplo o acción práctica
25. Fuente principal del dato
26. Responsable u owner
27. Notas

Utiliza una escala de 1 a 5, donde:

- 1 representa impacto o riesgo muy bajo.
- 5 representa impacto o riesgo muy alto.

En la variable `Sustituibilidad`:

- 1 significa que la categoría resulta muy fácil de sustituir.
- 5 significa que resulta muy difícil de sustituir.

## 5. Conversión del gasto a una escala de 1 a 5

Calcula automáticamente el `Score de gasto` utilizando los siguientes umbrales:

- Gasto igual o superior a 750.000 €: score 5.
- Gasto igual o superior a 400.000 € e inferior a 750.000 €: score 4.
- Gasto igual o superior a 200.000 € e inferior a 400.000 €: score 3.
- Gasto igual o superior a 100.000 € e inferior a 200.000 €: score 2.
- Gasto inferior a 100.000 €: score 1.

Los umbrales deben estar almacenados en la hoja `Parametros`, para que puedan modificarse.

## 6. Fórmula del Impact Score

Calcula el impacto mediante esta fórmula ponderada:

`Impact Score = Score de gasto × 40% + Impacto en margen × 25% + Criticidad para producción × 20% + Coste de parada × 15%`

Redondea el resultado a dos decimales.

Los pesos deben encontrarse en la hoja `Parametros`, no escritos directamente como valores fijos dentro de todas las fórmulas.

La suma de los pesos de impacto debe ser del 100%.

## 7. Conversión del número de proveedores

Convierte automáticamente el número de proveedores homologados en un score de riesgo:

- 1 proveedor: score 5.
- 2 proveedores: score 4.
- Entre 3 y 4 proveedores: score 3.
- Entre 5 y 7 proveedores: score 2.
- 8 o más proveedores: score 1.

## 8. Conversión de la concentración

Convierte automáticamente el porcentaje comprado al proveedor principal:

- Concentración igual o superior al 80%: score 5.
- Entre el 65% y el 79%: score 4.
- Entre el 50% y el 64%: score 3.
- Entre el 30% y el 49%: score 2.
- Menos del 30%: score 1.

## 9. Conversión del lead time

Convierte automáticamente el lead time en un score:

- Más de 60 días: score 5.
- Entre 31 y 60 días: score 4.
- Entre 15 y 30 días: score 3.
- Entre 8 y 14 días: score 2.
- 7 días o menos: score 1.

## 10. Fórmula del Supply Risk Score

Calcula el riesgo de suministro con la siguiente fórmula:

`Supply Risk Score = Score número de proveedores × 20% + Score concentración × 20% + Score lead time × 15% + Sustituibilidad × 20% + Riesgo proveedor × 15% + Volatilidad de precio × 5% + Riesgo geográfico × 5%`

Redondea el resultado a dos decimales.

Los pesos deben almacenarse en la hoja `Parametros`.

La suma de los pesos de riesgo debe ser del 100%.

## 11. Clasificación automática Kraljic

Utiliza inicialmente estos umbrales:

- Impacto alto: `Impact Score ≥ 3,00`
- Riesgo alto: `Supply Risk Score ≥ 3,00`

Los dos umbrales deben ser editables en la hoja `Parametros`.

Clasifica automáticamente las categorías:

- `Estratégico`: impacto alto y riesgo alto.
- `Apalancado`: impacto alto y riesgo bajo.
- `Cuello de botella`: impacto bajo y riesgo alto.
- `No crítico`: impacto bajo y riesgo bajo.

La clasificación debe actualizarse automáticamente cuando se modifiquen los datos, los pesos o los umbrales.

## 12. Estrategias recomendadas

Asigna automáticamente una estrategia según el cuadrante:

### Estratégico

- Colaboración a largo plazo.
- Planificación conjunta de capacidad.
- Gestión de riesgos y resiliencia.
- Innovación conjunta.
- Análisis contractual.
- Revisión periódica del proveedor.

### Apalancado

- Licitaciones competitivas.
- Negociación por volumen.
- Benchmark de precios.
- Should-cost.
- Acuerdos marco.
- Indexación basada en materias primas o energía.

### Cuello de botella

- Stock de seguridad.
- Planes de contingencia.
- Contratos de suministro garantizado.
- Identificación y homologación de alternativas.
- Reducción de la dependencia técnica.
- Seguimiento de señales tempranas de riesgo.

### No crítico

- Consolidación de proveedores.
- Catálogos electrónicos.
- Automatización de pedidos.
- Tarjetas de compra o P-cards.
- Reducción del coste administrativo.
- Automatización del proceso procure-to-pay.

## 13. Hoja “Parametros”

Incluye bloques diferenciados para:

### Pesos del Impact Score

- Score de gasto: 40%.
- Impacto en margen: 25%.
- Criticidad para producción: 20%.
- Coste de parada: 15%.

### Pesos del Supply Risk Score

- Número de proveedores: 20%.
- Concentración: 20%.
- Lead time: 15%.
- Sustituibilidad: 20%.
- Riesgo proveedor: 15%.
- Volatilidad de precio: 5%.
- Riesgo geográfico: 5%.

### Umbrales

- Umbrales utilizados para convertir el gasto en score.
- Umbral de impacto alto.
- Umbral de riesgo alto.
- Reglas de conversión del número de proveedores.
- Reglas de concentración.
- Reglas de lead time.

Marca claramente las celdas editables.

Añade, si es posible, una comprobación visual de que los pesos de cada score suman el 100%.

## 14. Hoja “Resumen”

Crea un resumen ejecutivo que incluya:

- Gasto anual total.
- Número total de categorías.
- Impact Score medio.
- Supply Risk Score medio.
- Número de categorías por cuadrante.
- Gasto anual acumulado por cuadrante.

Muestra los cuatro cuadrantes con una matriz visual:

- Apalancados: alto impacto y bajo riesgo.
- Estratégicos: alto impacto y alto riesgo.
- No críticos: bajo impacto y bajo riesgo.
- Cuello de botella: bajo impacto y alto riesgo.

Utiliza colores consistentes:

- Estratégicos: rojo suave.
- Apalancados: azul suave.
- Cuello de botella: amarillo suave.
- No críticos: verde suave.

Incluye una tabla con:

- Categoría.
- Impact Score.
- Supply Risk Score.

Añade una explicación ejecutiva indicando que:

- Kraljic debe aplicarse inicialmente por categoría de compra.
- La matriz es una ayuda para tomar decisiones, no un sustituto del criterio profesional.
- Las categorías situadas cerca de los umbrales deben revisarse cualitativamente.
- La clasificación debe validarse con Compras, Operaciones, Calidad, Finanzas y el equipo técnico.

## 15. Hoja “Guia y fuentes”

Explica para cada variable:

- Qué significa.
- De qué fuente interna puede obtenerse.
- Qué fuente externa puede utilizarse.
- Con qué frecuencia debería actualizarse.
- Quién debería ser responsable.

Incluye, al menos, estas fuentes:

- ERP.
- Sistema de compras.
- Contabilidad y Finanzas.
- Histórico de pedidos y facturas.
- Contratos.
- Maestro de proveedores.
- Inventario y almacén.
- Producción y mantenimiento.
- Calidad e incidencias.
- Logística y OTIF.
- Evaluaciones de proveedores.
- Información financiera externa.
- Índices de materias primas y energía.
- Estudios de mercado.
- Noticias.
- Información geopolítica.
- Datos ESG y de cumplimiento.

Incluye unas instrucciones breves:

1. Sustituir los datos ficticios por datos reales.
2. Revisar las escalas de 1 a 5 con un equipo transversal.
3. Ajustar los pesos y umbrales cuando sea necesario.
4. Revisar especialmente las categorías próximas a la frontera.
5. Definir acciones y responsables por categoría.
6. Actualizar la matriz al menos cada seis meses o cuando exista un cambio relevante.

Añade una nota indicando que todos los datos del ejemplo son ficticios y se incluyen únicamente con fines formativos.

## 16. Formato profesional

Aplica las siguientes reglas de diseño:

- Utiliza una paleta profesional en azul oscuro, azul medio y colores suaves para los cuadrantes.
- Encabezados con fondo azul y texto blanco.
- Congela la fila de encabezados.
- Activa filtros en la tabla del dataset.
- Mantén un ancho de columnas legible.
- Utiliza formato de moneda para el gasto.
- Utiliza formato de porcentaje para concentración y peso sobre el gasto.
- Muestra los scores con dos decimales.
- Aplica formato condicional a la columna `Cuadrante Kraljic`.
- Marca en amarillo claro las entradas que puede modificar el usuario.
- Marca en azul claro las columnas calculadas mediante fórmulas.
- Evita texto cortado y columnas excesivamente estrechas.
- Convierte el dataset en una tabla estructurada de Excel.

## 17. Requisitos técnicos y de validación

Antes de entregar el archivo:

- Comprueba que existen exactamente 30 categorías.
- Comprueba que las fórmulas están presentes en las 30 filas.
- Comprueba que el porcentaje total del gasto suma el 100%.
- Comprueba que los pesos de impacto suman el 100%.
- Comprueba que los pesos de riesgo suman el 100%.
- Comprueba que no existen errores `#REF!`, `#VALUE!`, `#DIV/0!`, `#NAME?` o `#N/A`.
- Comprueba que cada categoría queda clasificada en un cuadrante.
- Comprueba que los resultados del resumen coinciden con el dataset.
- Abre o renderiza las hojas principales para revisar visualmente el resultado.
- Entrega el resultado en formato `.xlsx`.

Guarda el archivo con el nombre:

`Matriz_Kraljic_PYME_Vidrio.xlsx`

El resultado debe ser una plantilla funcional, didáctica y reutilizable, no simplemente una tabla estática.
