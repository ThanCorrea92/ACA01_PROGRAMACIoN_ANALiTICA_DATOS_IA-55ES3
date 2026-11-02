# Corrección de tablas para index.md

**Regla de oro:** edita de **abajo hacia arriba** (tabla 10 → tabla 1) para que los números de línea de las tablas siguientes no se muevan.

En cada caso, **borra desde la línea inicial hasta la final (ambas incluidas, son las líneas de guiones `-----`)** y pega el código. Deja una línea en blanco antes y después de la tabla.

Los números de línea corresponden al `index.md` actual del repositorio (2,270 líneas).


---

## Tabla 10. Contraste de hipótesis (sección 13.1)

**Reemplazar líneas 2031 a 2088** de `index.md`.

~~~markdown
| # | Hipótesis | Veredicto | Evidencia clave |
|---|---|---|---|
| H1 | Más educación → más ingresos altos | **Confirmada** | 15.9 % (bachiller) → 41.3 % (pregrado) → 61.4 % (posgrado). El mayor salto es completar el pregrado. |
| H2 | Relación no lineal con la edad | **Confirmada** | U invertida: 1.1 % → 39.4 % (45–54) → 20.5 % (65+). |
| H3 | Más horas → más ingresos, con rendimientos decrecientes | **Confirmada** | Máximo en 50–60 h (44.1 %); cae a 35.7 % en > 60 h; el efecto requiere experiencia (mapa edad × horas). |
| H4 | Existe brecha de género y parte se explica por otras variables | **Confirmada con matiz** | 30.4 % vs 10.9 %; entre casados 44.6 % vs 44.8 %; en no casados persiste (8.2 % vs 4.7 %). El Anexo A: razón de odds 3.56 → 1.14. |
| H5 | Ocupación y empleador segmentan los ingresos | **Confirmada** | De 1.2 % (servicio doméstico) a 47.8 % (directivos); `Self-emp-inc` 55.4 %. La educación rinde distinto según la ocupación. |
| H6 | Capital: raro, concentrado y muy asociado a ingresos altos | **Confirmada** | 8.3 % con ganancias; el 1 % concentra 56 % del total; ≥ 5,000 USD → 90.1 % de ingresos altos. |
| H7 | `fnlwgt` no tiene relación con el ingreso | **Confirmada** | Correlación de Spearman −0.01; cajas casi idénticas entre grupos. |
~~~


---

## Tabla 9. Perfiles profesionales (sección 12)

**Reemplazar líneas 1964 a 2018** de `index.md`.

~~~markdown
| Perfil | Evidencia que utiliza | Aplicación concreta |
|---|---|---|
| **Administración de empresas** (Jhonathan) | Prima de la educación (15.9 % → 41.3 % → 61.4 %); segmento «casado/a con pregrado+» (71.8 %, 3.0 veces el promedio); `Self-emp-inc` 55.4 %; capital concentrado en el 8 % de la población | **Segmentación de clientes y talento:** definir un perfil de alto poder adquisitivo (banca privada, inversión, seguros), diseñar planes de financiación de estudios y rutas de carrera en RR. HH., y plantear auditorías de equidad salarial comparando personas comparables. |
| **Ingeniería de sistemas** (Camilo y Diego) | Limpieza paso a paso y documentada; validaciones automáticas con `assert`; copia intacta de los datos originales; fuente de datos trazable | **Proceso de datos reproducible y auditable:** el mismo código puede reutilizarse con nuevos extractos y es la base del trabajo previo a un modelo (selección y construcción de variables). |
| **Ingeniería de telecomunicaciones** (Johan) | Detección de saturación (`99,999`, `age = 90`); `fnlwgt` como ruido sin relación con el ingreso; escala logarítmica para el capital; peso muestral y prueba de sensibilidad | **Fiabilidad de la señal:** decidir qué variables *transmiten información* antes de modelar, tratar valores truncados como saturación de sensor y usar escalas logarítmicas ante rangos amplios; la misma lógica aplica a datos de red (tráfico, latencia, fallas). |
| **Diseño multimedia** (Luisa) | Paleta Okabe-Ito, color consistente, títulos que enuncian el hallazgo, barras de error, figura-resumen de la sección 11 | **Comunicación de datos accesible:** convertir los hallazgos en una historia para audiencias no técnicas (un tablero o infografía de una página), evitando gráficos que exageran diferencias con muestras pequeñas. |
~~~


---

## Tabla 8. Variables nuevas (sección 6)

**Reemplazar líneas 878 a 915** de `index.md`.

~~~markdown
| Variable nueva | Construcción | Para qué sirve |
|---|---|---|
| `ingreso_alto` y `pct_alto` | 1 (o 100) si `income == ">50K"`, 0 en caso contrario | Su promedio es directamente la *tasa* de ingresos altos |
| `nivel_educativo` | 5 niveles a partir de `education_num` | Resume 16 categorías en etapas con significado |
| `grupo_edad`, `grupo_horas` | Rangos ordenados | Capturan relaciones no lineales y neutralizan el *heaping* |
| `casado` | 1 si `Married-civ-spouse` o `Married-AF-spouse` | Resume 7 estados civiles en un indicador de hogar conyugal (`Married-spouse-absent` cuenta como no casado porque no comparte hogar) |
| `tipo_ocupacion` | Agrupa 14 ocupaciones en 5 familias + «No reporta» | Lectura de negocio |
| `origen` | EE. UU. / Otro país / No reporta | Reduce 41 países (muchos con pocos casos) |
| `categoria_capital` | Ganancia ≥ 5,000 / Ganancia &lt; 5,000 / Pérdida / Sin movimiento | Convierte una variable con 91 % de ceros en categorías interpretables |
| `log_capital_gain` | `log(1 + x)` | Comprime una cola extrema |
| `flag_tope_edad`, `flag_tope_capital` | Indicadores de valores truncados | Evita tratarlos como mediciones reales |
~~~


---

## Tabla 7. Scorecard de calidad (sección 5.5)

**Reemplazar líneas 827 a 860** de `index.md`.

~~~markdown
| Aspecto | Problema | Magnitud | Tratamiento |
|---|---|---|---|
| Faltantes | `"?"` como código de faltante en `workclass`, `occupation`, `native_country` | 2,799 / 2,809 / 857 filas (≤ 5.8 %) | Categoría explícita `"No reporta"` (faltante informativo) |
| Duplicados | Filas duplicadas exactas | 52 filas (0.11 %) | Eliminadas; efecto ≈ 0.01 pp sobre la tasa objetivo |
| Redundancia | `education` ≡ `education_num` | 100 % redundantes | Se usa una sola en cada análisis |
| Coherencia | `relationship` vs `sex` | 4 casos atípicos | Conservados (pueden ser legítimos) |
| Valores truncados | `capital_gain=99,999`, `age=90` | 244 y 55 filas | Se marcan con una columna indicadora |
| Redondeo | *Heaping* en 40 h/semana | ~47 % de las filas | Agrupación por rangos |
| Distribución | Capital con muchísimos ceros y cola extrema | 91.7 % de ceros en ganancias | Categorías y logaritmo |
| Balance | Clase `>50K` minoritaria | 76.1 % vs 23.9 % (3.2 a 1) | Se comparan tasas, no conteos |
~~~


---

## Tabla 6. Hallazgos e inconsistencias (sección 5.3)

**Reemplazar líneas 702 a 747** de `index.md`.

~~~markdown
| Hallazgo | Evidencia | Decisión y justificación |
|---|---|---|
| Formato de texto | Ninguna celda con espacios sobrantes; `income` con solo dos valores | Se aplica `strip()` de forma preventiva al limpiar. |
| **Redundancia** `education` ↔ `education_num` | Cada código tiene exactamente una etiqueta | Son la misma información: usaremos `education_num` para cálculos y una versión agrupada para gráficos. **Nunca ambas** en un modelo. |
| Coherencia `relationship` ↔ `sex` | 1 caso «Husband» femenino y 3 «Wife» masculinos (4 de 48,842) | **Se conservan.** La relación se define respecto a quien encabeza el hogar y puede reflejar parejas del mismo sexo; no hay evidencia para llamarlos error. Impacto despreciable. |
| **Truncamiento (*top-coding*)** | `age = 90` (55 casos): la edad máxima está *recortada*. `capital_gain = 99,999` (244 casos): **el 100 % tiene ingresos altos**, así que 99,999 no es un monto real sino un código de «ganancia muy alta». | Se conservan, pero se **marcan** para no tratarlos como mediciones reales. |
| *Heaping* en horas | ~47 % reporta exactamente 40 h; también se agrupan en 50, 45, 60 y 35 | Es redondeo al declarar, no error. Justifica agrupar las horas en rangos. |
| Plausibilidad | Solo 1 caso con pregrado y menos de 19 años | Inusual pero posible (educación acelerada); se conserva. |
~~~


---

## Tabla 5. Rutas para obtener el dataset

**Reemplazar líneas 330 a 349** de `index.md`.

~~~markdown
| Ruta | Mecanismo | Ventaja | Limitación |
|---|---|---|---|
| **A. GitHub (usada)** | `pd.read_csv` sobre el archivo *raw* de [`jbrownlee/Datasets`](https://github.com/jbrownlee/Datasets) (`adult-all.csv`) | Una sola línea, sin cuenta ni API; es el archivo original de UCI (entrenamiento + prueba, 48,842 filas) | No trae encabezados: los asignamos nosotros según la documentación de UCI |
| B. OpenML | `fetch_openml("adult", version=2)` de scikit-learn | Trae nombres de columnas | Requiere acceso a openml.org |
| C. UCI directo | Descarga de `adult.data` y `adult.test` desde `archive.ics.uci.edu` | Fuente primaria | Hay que unir dos archivos y corregir un punto final (`<=50K.`) en el de prueba |
~~~


---

## Tabla 4. Diccionario de datos

**Reemplazar líneas 209 a 268** de `index.md`.

~~~markdown
| Variable | Tipo | Descripción |
|---|---|---|
| `age` | Numérica entera | Edad en años (rango del dataset: 17 a 90). |
| `workclass` | Categórica | Clase de empleador: privado, gobierno, independiente (incorporado o no), sin pago, nunca ha trabajado. |
| `fnlwgt` | Numérica | *Final weight*: número de personas de la población que representa cada registro (peso de muestreo del censo). |
| `education` | Categórica ordinal | Máximo nivel educativo alcanzado (16 categorías). |
| `education_num` | Numérica ordinal | Codificación numérica de `education` (1 = preescolar … 16 = doctorado). |
| `marital_status` | Categórica | Estado civil (7 categorías). |
| `occupation` | Categórica | Ocupación (14 categorías). |
| `relationship` | Categórica | Rol dentro del hogar (esposo/a, hijo/a, no familiar, etc.). |
| `race` | Categórica | Raza reportada (5 categorías). |
| `sex` | Categórica | Sexo reportado (Male / Female). |
| `capital_gain` | Numérica | Ganancias de capital del año (USD). |
| `capital_loss` | Numérica | Pérdidas de capital del año (USD). |
| `hours_per_week` | Numérica entera | Horas trabajadas por semana. |
| `native_country` | Categórica | País de origen (41 categorías). |
| **`income`** | **Objetivo** | `<=50K` o `>50K` de ingreso anual. |
~~~


---

## Tabla 3. Hipótesis de trabajo

**Reemplazar líneas 175 a 205** de `index.md`.

~~~markdown
| # | Hipótesis |
|---|---|
| H1 | A mayor nivel educativo, mayor probabilidad de ingresos altos. |
| H2 | La relación con la edad no es lineal: crece durante la vida laboral y se atenúa al final. |
| H3 | Trabajar más horas se asocia con ingresos altos, pero con rendimientos decrecientes. |
| H4 | Existe una brecha de género en ingresos y parte de ella puede explicarse por otras variables. |
| H5 | El tipo de ocupación y la clase de empleador segmentan fuertemente los ingresos. |
| H6 | Las ganancias de capital son poco frecuentes, están muy concentradas y se asocian fuertemente con ingresos altos. |
| H7 | La variable `fnlwgt` (peso muestral del censo) no tiene relación con el ingreso. |
~~~


---

## Tabla 2. Por qué importa (ámbitos)

**Reemplazar líneas 144 a 162** de `index.md`.

~~~markdown
| Ámbito | Uso de este tipo de análisis |
|---|---|
| Políticas de empleo y educación | Estimar qué niveles de formación y perfiles laborales se asocian con mayor remuneración. |
| Estrategia comercial | Segmentar poblaciones por poder adquisitivo para diseñar ofertas, precios y canales. |
| Recursos humanos y equidad | Detectar desigualdades salariales y entender sus posibles causas estructurales. |
| Ciencia de datos / IA | Preparar los datos y entender sesgos antes de construir un modelo de clasificación. |
~~~


---

## Tabla 1. Integrantes del equipo

**Reemplazar líneas 36 a 65** de `index.md`.

~~~markdown
| Integrante | Profesión | Ciudad | Lente analítico que aporta al proyecto |
|---|---|---|---|
| Luisa Fernanda Vega Pulecio | Diseñadora de multimedia | Bogotá | Narrativa visual, accesibilidad y comunicación de hallazgos |
| Camilo Andrey Rojas García | Ingeniero de sistemas | Mocoa | Orden del proceso, validación de datos y reproducibilidad |
| Diego Fernando López León | Ingeniero de sistemas | Bogotá | Calidad de datos y código claro y mantenible |
| Johan Sebastian Díaz Jiménez | Ingeniero de telecomunicaciones | Bogotá | Señal vs. ruido, saturación (*clipping*) y escalas logarítmicas |
| Jhonathan Correa Valencia | Administrador de empresas | Pereira | Segmentación, decisiones de negocio y recomendaciones |
~~~
