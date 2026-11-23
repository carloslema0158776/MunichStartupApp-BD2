# MunichStartupApp — Base de Datos II

Proyecto académico de **Base de Datos II** orientado al análisis de inversiones en startups mediante un **Data Warehouse** y una aplicación de escritorio.

## ¿De qué trata?

MunichStartupApp integra información sobre startups, inversores, instituciones, financiación e inversiones. A partir de un modelo operacional (**OLTP**), se diseña un **almacén de datos dimensional** para consultar indicadores, generar reportes y explorar tendencias de inversión.

## Tecnologías utilizadas

- **PostgreSQL / SQL** — esquemas OLTP y Data Warehouse.
- **Pentaho Data Integration (Spoon)** — transformaciones ETL para cargar y relacionar dimensiones y hechos.
- **Java Swing + JDBC** — interfaz gráfica y consultas a PostgreSQL.
- **Apache PDFBox** — exportación de reportes a PDF.
- **Apache NetBeans / Ant** — proyecto de aplicación de escritorio.

## Arquitectura

El Data Warehouse utiliza un **esquema estrella** con la tabla de hechos `dw.fact_inversion`, que almacena el monto invertido y las claves de sus dimensiones:

- `dw.dim_startup`: características de las empresas emergentes.
- `dw.dim_inversor`: información del inversor y sus roles.
- `dw.dim_institucion`: entidades participantes.
- `dw.dim_financiacion`: características y periodos de financiación.
- `dw.dim_tiempo`: fechas y atributos temporales para análisis.

Las transformaciones ETL emplean, entre otras técnicas, `STRING_AGG` para consolidar roles, `COALESCE` para valores faltantes, `ROW_NUMBER` para identificadores y búsquedas a dimensiones para asociar las inversiones.

## Funcionalidades de MunichStartupApp

- Panel ejecutivo con total invertido, número de inversiones y entidades destacadas.
- Gráficos de inversión por startup, institución, tipo de inversor y periodo.
- Reportes por startup, institución, inversor y tiempo.
- Filtros por ubicación, estado de startup, tipo de institución, inversor, año y mes.
- Exportación de reportes en PDF.

## Estructura prevista

```text
MunichStartupApp/
├── src/                   # Código fuente Java Swing
├── nbproject/             # Configuración de NetBeans
├── build.xml              # Compilación Ant
sql/
├── startup_oltp.sql       # Modelo operacional
├── startup_dw.sql         # Esquema dimensional
└── startup_dw_consultas.sql
etl/
├── proyecto_final_spoon.ktr
└── hecho_inversion_proyecto_final.ktr
```

## Ejecución local

1. Instalar **PostgreSQL**, un **JDK compatible**, **NetBeans** y **Pentaho Data Integration**.
2. Crear la base de datos local `Startup_DW` y ejecutar el esquema OLTP y el dimensional.
3. Cargar datos de prueba autorizados en OLTP y ejecutar las transformaciones ETL configurando las conexiones locales.
4. Configurar el acceso JDBC mediante `MUNICH_DB_URL`, `MUNICH_DB_USER` y `MUNICH_DB_PASSWORD`.
5. Abrir el proyecto Java en NetBeans y ejecutar `munichstartupapp.MunichStartupApp`.

> **Nota:** Los scripts de creación y las transformaciones forman parte de una entrega académica. Su ejecución integral depende de disponer de datos de prueba compatibles y configurar las conexiones locales. No se ha realizado una prueba de ejecución de extremo a extremo aquí.

## Seguridad y publicación

Se han detectado credenciales incrustadas en la configuración original; deben sustituirse por configuración local antes de publicar el código. No se deben subir contraseñas, rutas privadas ni bases pobladas que contengan datos personales. Este README describe el contenido original proporcionado; la presencia de cada archivo en el repositorio debe verificarse en el listado publicado.
