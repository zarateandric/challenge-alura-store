# 🚀 Análisis de Tiendas "Alura Store"

**Objetivo del Proyecto:** Analizar el rendimiento de 4 tiendas de la cadena "Alura Store" para identificar a la menos eficiente y presentar una recomendación de venta al Sr. Juan, basada 100% en datos.

## 📊 Resumen del Análisis y Recomendación Final

Tras un análisis exhaustivo de 9,435 registros de ventas, se llegó a la siguiente conclusión:

**Recomendación: Se recomienda vender la Tienda 4.**

**Justificación Clave:** Aunque todas las tiendas tienen un volumen de ventas (cantidad de pedidos) y una satisfacción de cliente (calificaciones) casi idénticos, la **Tienda 4** genera los **ingresos totales más bajos**.

El análisis profundo de productos reveló que esto se debe a un **"Ticket Promedio" bajo**: sus productos más vendidos (ej. "Cubertería", "Dashboards con Power BI") son de mucho menor valor que los de tiendas de alto rendimiento (ej. "TV LED UHD 4K" en la Tienda 1).

---

## 📈 Visualizaciones Destacadas

A continuación, se presentan los gráficos clave que respaldan la recomendación:

### 1. Ingresos Totales por Tienda
Este gráfico confirma que la Tienda 4 es la que menos ingresos genera del grupo.

![Ingresos Totales por Tienda](<img width="915" height="553" alt="image" src="https://github.com/user-attachments/assets/9cd7a77f-3988-482f-99c0-ac9a199e3852" />)

### 2. Ingresos por Ciudad y Tienda (Análisis Geográfico)
Este análisis de barras agrupadas muestra que la Tienda 4 (barra roja) tiene un rendimiento inferior en los dos mercados más importantes: **Bogotá y Medellín**.

![Ingresos Totales por Ciudad y Tienda](<img width="1489" height="790" alt="image" src="https://github.com/user-attachments/assets/533035b1-7326-4f34-a9f6-102f762ad321" />
)

### 3. Mix de Categorías de la Tienda 4
Este gráfico circular muestra que el mix de categorías de la Tienda 4 es saludable y diversificado, similar al de otras tiendas. Esto confirma que el problema no es la categoría, sino el precio de los productos específicos.

![Proporción de Ventas por Categoría - Tienda 4](<img width="858" height="661" alt="image" src="https://github.com/user-attachments/assets/677fb608-e72b-4e9d-8541-2e7305100c22" />
)

---

## 🛠️ Metodología y Pasos del Proyecto

El análisis completo se encuentra en el notebook `AluraStoreLatam-Challenge.ipynb` y siguió los siguientes pasos:

1.  **Carga y Unificación:** Se cargaron los 4 archivos CSV (uno por tienda) y se unificaron en un DataFrame maestro usando `pandas.concat()`.
2.  **Validación de Datos:** Se utilizó `.info()` para verificar la ausencia de datos nulos y los tipos de datos correctos.
3.  **Análisis Macro (KPIs):** Se usó `.groupby().agg()` para calcular las métricas principales por tienda:
    * Ingresos Totales
    * Ventas Totales (Volumen)
    * Calificación Promedio
    * Costo de Envío Promedio
4.  **Análisis Micro (Causa Raíz):** Se usó `groupby()` por Categoría y Producto para encontrar el "por qué" del bajo rendimiento de la Tienda 4.
5.  **Análisis Geográfico:** Se utilizó `.unstack()` para pivotar los datos y comparar el rendimiento por ciudad.
6.  **Informe Final:** Se redactó una conclusión ejecutiva para el Sr. Juan.

---

## 💻 Tecnologías Utilizadas

* **Python 3.12.12**
* **Pandas:** Para la manipulación y análisis de datos.
* **Matplotlib:** Para la generación de todas las visualizaciones.
* **Google Colab:** Como entorno de desarrollo interactivo.

