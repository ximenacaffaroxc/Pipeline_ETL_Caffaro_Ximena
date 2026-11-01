# Pipeline_ETL_Caffaro_Ximena

RetailPro | Análisis de Datos y Modelado de Ventas

Descripción del proyecto

RetailPro es un proyecto orientado al análisis de datos comerciales, cuyo objetivo es organizar información de ventas mediante un modelo de datos estructurado y facilitar su análisis a través de indicadores de negocio.

El proyecto contempla el trabajo con datos de ventas, clientes, productos, categorías y fechas, con el propósito de construir una base analítica que permita estudiar el comportamiento comercial y realizar comparaciones entre distintos períodos.

Este trabajo forma parte de un portfolio de Data Analytics y refleja la aplicación de conceptos de modelado de datos, análisis de información y construcción de métricas.

Objetivos del proyecto

Objetivo general

Desarrollar una estructura de datos que permita analizar las ventas de un entorno retail, facilitando la interpretación de información comercial y la elaboración de indicadores para la toma de decisiones.

Objetivos específicos

Organizar la información comercial mediante un modelo de datos dimensional.

Relacionar los datos de ventas con las dimensiones de clientes, productos, categorías y fechas.

Construir indicadores para medir el desempeño de las ventas.

Analizar la evolución de las ventas a lo largo del tiempo.

Comparar resultados comerciales entre períodos.

Facilitar la consulta e interpretación de los datos mediante herramientas de análisis.

Herramientas y tecnologías

Las tecnologías y conceptos identificados en la documentación disponible son:

Tecnología / Herramienta

Aplicación

SQL

Tecnología prevista para el trabajo con consultas y datos relacionales. Su implementación debe confirmarse con los scripts del proyecto.

Power BI

Modelado de datos y análisis de información comercial.

DAX

Creación de columnas calculadas y medidas analíticas.

Modelo dimensional

Organización de los datos mediante un esquema en estrella.

GitHub

Almacenamiento y documentación del proyecto.

Nota: La documentación adjunta confirma el uso de Power BI y DAX. La utilización efectiva de SQL Server, SQL Server Management Studio y herramientas específicas de ETL debe confirmarse con la documentación técnica original.

Modelo de datos

El proyecto documenta un modelo dimensional con estructura de esquema en estrella.

La tabla central es Fact_Ventas, que se relaciona con las dimensiones utilizadas para contextualizar y analizar la información comercial.

Tablas del modelo

Tabla

Tipo

Función

Fact_Ventas

Hechos

Contiene la información de ventas y el campo total_venta.

Dim_Clientes

Dimensión

Permite contextualizar las ventas por cliente.

Dim_Fechas

Dimensión

Permite realizar análisis temporales.

Dim_categorias

Dimensión

Permite analizar las ventas por categoría.

Dim_Productos

Dimensión

Permite analizar la información por producto.

Las relaciones documentadas son de tipo 1 (uno a muchos) y se encuentran activas.

Esquema conceptual

                 Dim_Clientes
                       |
                       |
Dim_Fechas ------ Fact_Ventas ------ Dim_categorias
                       |
                       |
                 Dim_Productos

Este diseño permite analizar una misma medida de ventas desde distintas perspectivas comerciales.

Proceso ETL

Un proceso ETL comprende tres etapas: extracción, transformación y carga.

1. Extracción (Extract)

Consiste en obtener los datos desde las fuentes de origen.

Información pendiente de confirmar:

Sistemas o archivos utilizados como fuente.

Formatos de los datos originales.

Tablas o archivos de entrada.

2. Transformación (Transform)

Comprende la preparación y organización de los datos para su posterior análisis.

En la documentación del modelo analítico se identifica:

Organización de la información mediante dimensiones y tabla de hechos.

Construcción de una tabla calendario.

Creación de atributos temporales.

Desarrollo de medidas analíticas con DAX.

3. Carga (Load)

Consiste en incorporar los datos transformados al entorno de destino.

Información pendiente de confirmar:

Base de datos de destino.

Tablas de carga.

Método de carga.

Frecuencia o modalidad de actualización.

Análisis temporal y medidas DAX

Una parte documentada del proyecto consiste en la creación de una tabla calendario denominada Dim_Fechas.

Esta tabla se genera utilizando el rango de fechas de Fact_Ventas[fecha_venta] y contiene los siguientes atributos:

Año.

Número de mes.

Nombre del mes.

Trimestre.

Número de semana.

También se marca como tabla de fechas para habilitar correctamente las funciones de inteligencia temporal.

Medidas desarrolladas

Medida

Descripción

Total Ventas

Calcula la suma de Fact_Ventas[total_venta].

Ventas Computación

Calcula las ventas correspondientes a la categoría Computación.

Ventas YTD

Calcula las ventas acumuladas del año.

Ventas LY

Recupera las ventas del período equivalente del año anterior.

% Crecimiento Anual

Calcula la variación porcentual entre las ventas actuales y las del año anterior.

Código DAX documentado

Total de ventas

Total Ventas =
SUM(Fact_Ventas[total_venta])

Ventas de Computación

Ventas Computación =
CALCULATE(
    [Total Ventas],
    Fact_Ventas[categoria] = "Computación"
)

Ventas acumuladas del año

Ventas YTD =
TOTALYTD(
    [Total Ventas],
    Dim_Fechas[Date]
)

Ventas del año anterior

Ventas LY =
CALCULATE(
    [Total Ventas],
    SAMEPERIODLASTYEAR(Dim_Fechas[Date])
)

Porcentaje de crecimiento anual

% Crecimiento Anual =
VAR VentasActual = [Total Ventas]
VAR VentasAnterior = [Ventas LY]
RETURN
    DIVIDE(
        VentasActual - VentasAnterior,
        VentasAnterior
    )

Estructura del repositorio

La estructura pública verificada actualmente es:

Pipeline_ETL_Caffaro_Ximena/
│
├── Pipeline_ETL_Ximena Caffaro.pdf
│
└── README.md

Archivo

Descripción

Pipeline_ETL_Ximena Caffaro.pdf

Documento de referencia del proyecto.

README.md

Documentación general del repositorio.

No se identificaron scripts SQL, archivos de datos ni archivos adicionales en el listado público consultado.

Scripts SQL

 Análisis en Power BI

La documentación adjunta describe la construcción del modelo dimensional, la tabla calendario y las medidas DAX para el análisis de ventas.

El modelo incluye una matriz de validación con:

Mes como fila.

Año como columna.

Total de ventas.

Ventas YTD.

Ventas LY.

Porcentaje de crecimiento anual.

Resultados y aprendizajes

El desarrollo documentado permitió trabajar sobre una estructura analítica orientada al análisis comercial.

Entre los principales resultados y conocimientos aplicados se destacan:

Diseño de un modelo de datos en esquema estrella.

Identificación de tablas de hechos y dimensiones.

Comprensión de relaciones uno a muchos.

Construcción de una dimensión calendario.

Aplicación de funciones DAX de agregación y contexto de filtro.

Implementación de indicadores de ventas.

Aplicación de funciones de inteligencia temporal.

Comparación de resultados entre períodos.

Validación de medidas mediante una matriz de análisis.

Estas prácticas permiten desarrollar competencias relevantes para el trabajo en Data Analytics y Business Intelligence.

Autora

Ximena Caffaro

Proyecto desarrollado como parte de un portfolio profesional orientado a Data Analytics, modelado de datos y análisis de información comercial.

Repositorio

Pipeline_ETL_Caffaro_Ximena - GitHub
