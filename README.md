# 🧠 Proyecto: Análisis de Transacciones Financieras con PySpark y Delta Lake

## 📋 Descripción
Este proyecto implementa una arquitectura **Lakehouse** utilizando **Apache Spark** sobre **Databricks**, con el objetivo de procesar, limpiar y analizar datos de transacciones financieras.  
A través de un flujo estructurado en tres capas —**Bronze**, **Silver** y **Gold**— se transforman los datos desde su forma cruda hasta obtener información agregada y lista para el análisis.

---

## 🏗️ Estructura del proyecto

### 1️⃣ Capa Bronze
- Carga inicial de los datos en formato **Delta Lake**.
- Conversión desde un archivo CSV a una tabla Delta persistente.
- Verificación de conteo y esquema.

### 2️⃣ Capa Silver
- **Limpieza de datos:** eliminación de duplicados y nulos.
- **Transformaciones:** 
  - Tipificación y conversión de columnas.
  - Creación de nuevas variables derivadas (`Status`, `MontoCategoria`, `log_Amount`, `HoraAprox`, etc.).
- **Enriquecimiento:** unión (*join*) con una tabla de usuarios simulada (`ref_usuarios`), agregando información de edad, monto promedio y nivel de riesgo.

### 3️⃣ Capa Gold
- **Agregaciones:** cálculo de métricas estadísticas por estado de transacción y hora.
- **Indicadores resumen:** monto promedio, total, mínimo, máximo y desviación estándar por categoría.
- **Análisis temporal:** número de transacciones y montos promedio por hora aproximada.
- **Persistencia:** almacenamiento de los resultados en tablas Delta (`gold_resumen_transacciones` y `gold_temporal`).

---

## ⚙️ Tecnologías utilizadas

| Tecnología | Descripción |
|-------------|-------------|
| 🧩 **Apache Spark (PySpark)** | Procesamiento distribuido de datos |
| 🪣 **Delta Lake** | Almacenamiento transaccional sobre Data Lake |
| ☁️ **Databricks** | Plataforma para análisis y orquestación del pipeline |
| 🐍 **Python 3.x** | Lenguaje principal para ETL |
| 📊 **SQL / Spark SQL** | Consultas y agregaciones analíticas |

---

| Sección | Descripción |
|----------|--------------|
| **1. Importación de librerías** | Carga de módulos de PySpark y funciones SQL |
| **2. Capa Bronze** | Lectura del dataset, creación de tabla Delta y verificación |
| **3. Capa Silver** | Limpieza, derivación de columnas y join con usuarios |
| **4. Capa Gold** | Agregaciones y generación de indicadores finales |
| **5. Consultas SQL** | Ejecución de queries analíticas en Databricks |
| **6. Visualizaciones** | Análisis temporal y comparativo |

---

## 💾 Tablas generadas

| Tabla | Descripción | Capa |
|--------|--------------|------|
| `lakehouse_fraude.bronze_transacciones` | Datos crudos convertidos a Delta | Bronze |
| `lakehouse_fraude.ref_usuarios` | Usuarios simulados con nivel de riesgo | Silver |
| `lakehouse_fraude.gold_resumen_transacciones` | Métricas globales de transacciones | Gold |
| `lakehouse_fraude.gold_temporal` | Análisis por hora y estado de transacción | Gold |

## 🚀 Cómo ejecutar el notebook

1. **Subir el archivo** a tu espacio de Databricks.  
2. **Conectar a un cluster** (Spark 3.x, Runtime compatible con Delta Lake).  
3. **Ejecutar las celdas** secuencialmente desde la capa Bronze hasta Gold.  
4. **Ver los resultados** en las tablas Delta creadas o con consultas SQL:


