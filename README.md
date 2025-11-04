# 🚀 Análisis de Rendimiento de Tiendas "Alura Store"

Este repositorio contiene el análisis de datos completo para el proyecto "Alura Store", cuyo objetivo es identificar a la tienda menos eficiente de una cadena de 4 sucursales para recomendar su venta.

## 📜 Tabla de Contenidos

  * [1. El Desafío del Negocio]
  * [2. Metodología de Análisis]
      * [2.1. Carga y Unificación de Datos]
      * [2.2. Análisis de KPIs (Vista Macro)]
      * [2.3. Análisis de Causa Raíz (Vista Micro)]
      * [2.4. Análisis Geográfico (Desafío Extra)]
  * [3. Hallazgos Clave y Visualizaciones]
  * [4. Recomendación Final]
  * [5. Tecnologías Utilizadas]

-----

## 1\. El Desafío del Negocio

El Sr. Juan, propietario de la cadena "Alura Store", necesita tomar una decisión estratégica: desea vender una de sus 4 tiendas para financiar un nuevo emprendimiento. El objetivo de este análisis es evaluar de manera integral el rendimiento de cada tienda (basado en ventas, reseñas, productos y logística) para identificar a la **"menos eficiente"** y así proporcionar una recomendación basada 100% en datos.

-----

## 2\. Metodología de Análisis

El análisis completo se encuentra en el notebook `analisis_alura_store.ipynb`. El proceso se dividió en cuatro fases principales:

### 2.1. Carga y Unificación de Datos

Los datos se recibieron en 4 archivos CSV separados, uno por cada tienda.

1.  Se cargó cada archivo en un DataFrame de Pandas.
2.  Se creó una columna `Tienda` en cada DataFrame para etiquetar el origen de los datos.
3.  Se unificaron los 4 DataFrames en un solo `df_master` usando `pd.concat()`.
4.  Se realizó una validación con `.info()`, confirmando **0 valores nulos** y tipos de datos correctos.

### 2.2. Análisis de KPIs (Vista Macro)

Para obtener una "vista de helicóptero", se agruparon los datos por `Tienda` y se calcularon 4 métricas clave usando `.agg()`:

  * **Ingresos Totales:** La suma de la columna `Precio`.
  * **Ventas Totales:** El conteo de transacciones (`Producto`).
  * **Calificación Promedio:** La media de la columna `Calificación`.
  * **Costo de Envío Promedio:** La media de la columna `Costo de envío`.

### 2.3. Análisis de Causa Raíz (Vista Micro)

El análisis macro reveló una paradoja: la **Tienda 4** tenía los **ingresos más bajos**, pero el **mismo volumen de ventas** y **excelentes calificaciones**. Para entender el *por qué*, se profundizó el análisis:

  * **Análisis de Categorías:** Se usó `groupby(['Tienda', 'Categoría del Producto'])` para ver si la Tienda 4 vendía categorías diferentes.
  * **Análisis de Productos:** Se usó `groupby(['Tienda', 'Producto'])` para encontrar los productos más y menos vendidos en cada tienda, revelando la causa raíz del problema.

### 2.4. Análisis Geográfico (Desafío Extra)

Finalmente, se exploró la dimensión espacial para ver si el rendimiento variaba por ciudad.

  * Se agruparon los ingresos usando `groupby(['Lugar de Compra', 'Tienda'])`.
  * Se utilizó `.unstack()` para pivotar la tabla.
  * Se generó un gráfico de barras agrupado para comparar el rendimiento de las 4 tiendas en cada ciudad clave.

-----

## 3\. Hallazgos Clave y Visualizaciones

El análisis arrojó 4 hallazgos principales que fundamentan la recomendación final:

**Hallazgo 1: La Tienda 4 es la que menos ingresos genera.**
El gráfico de barras de ingresos totales muestra que la Tienda 4 está significativamente por debajo de las demás en rentabilidad.
<img width="915" height="553" alt="ingresos_totales_tienda" src="https://github.com/user-attachments/assets/2421f621-e136-4c16-bacd-efe6a2ccb8fb" />



**Hallazgo 2: El problema NO es el volumen de ventas ni el servicio.**
El análisis de KPIs (`resumen_tiendas`) demostró que todas las tiendas tienen un volumen de ventas casi idéntico (aprox. 2359 transacciones). Además, sus calificaciones promedio son virtualmente iguales (todas rondan 4.0 estrellas).

**Hallazgo 3: La causa raíz es el "Ticket Promedio" (Mix de Productos).**
Al comparar los productos más vendidos, se descubrió la razón:
<img width="858" height="661" alt="proporcion_ventas" src="https://github.com/user-attachments/assets/c3ee0e73-e85f-4d77-a99c-b9fa913c3241" />


  * **Tienda 1 (Altos Ingresos):** Vende productos de alto valor como "TV LED UHD 4K" y "Secadora de ropa".
  * **Tienda 4 (Bajos Ingresos):** Vende productos de bajo valor como "Cubertería" y "Dashboards con Power BI".

**Hallazgo 4: La Tienda 4 falla en los mercados clave.**
El análisis geográfico confirmó que la Tienda 4 (barra roja) tiene el peor rendimiento de ingresos en los dos mercados más importantes: **Bogotá y Medellín**.<img width="1489" height="790" alt="ingresos_por_ciudad_tienda" src="https://github.com/user-attachments/assets/5fd9696a-62f0-443c-bb61-5950ac948382" />


-----

## 4\. Recomendación Final

Basado en la evidencia, se presentó el siguiente informe al Sr. Juan:

> **Asunto: Recomendación de Venta de Tienda Alura Store**
>
> **Recomendación Final: Vender la Tienda 4.**
>
> **Justificación:**
> La **Tienda 4** es la candidata ideal para la venta al ser la **menos eficiente desde el punto de vista financiero**.
>
> Aunque mantiene un volumen de ventas saludable y una operación logística eficiente (bajos costos de envío y buenas reseñas), su rentabilidad es la más baja del grupo.
>
> Este bajo rendimiento no se debe a una mala gestión o falta de clientes, sino a un **mix de productos enfocado en artículos de bajo precio**. Mientras que otras tiendas capitalizan sus ventas con productos de alto valor, la Tienda 4 no logra generar ingresos proporcionales a su volumen de operación.
>
> Vender la Tienda 4 representa la decisión con el **menor impacto negativo en la facturación total** de Alura Store y libera capital de la unidad de negocio que genera menos valor por transacción.

-----


## 5\. Tecnologías Utilizadas

  * **Python 3.12.12+**
  * **Pandas:** Para la carga, manipulación y análisis de datos.
  * **Matplotlib:** Para la generación de todas las visualizaciones estáticas.
  * **Google Colab:** Como entorno de desarrollo interactivo para el análisis.

