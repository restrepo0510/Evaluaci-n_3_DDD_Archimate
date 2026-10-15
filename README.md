# Gobierno de datos Hogar Andino Inmobiliaria S.A.S. 


- [1. Entendimiento del negocio y mapa de capacidades](#1-entendimiento-del-negocio-y-mapa-de-capacidades)
  - [1.1 V1: motivación de la solución, de la necesidad a la meta](#11-v1-motivación-de-la-solución-de-la-necesidad-a-la-meta)

  - [1.2 V2: mapa de capacidades](#12-v2-mapa-de-capacidades)

  - [1.3 V2B: dependencias de gobierno de datos, recursos y cursos de acción](#13-v2b-dependencias-de-gobierno-de-datos-recursos-y-cursos-de-acción)

  - [1.4 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan](#14-v3a-cadena-de-valor-del-negocio-eventos-y-capacidades-que-la-habilitan)
  
  - [1.5 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores](#15-v3b-proceso-e2e-de-gobierno-de-datos-cadena-de-valor-eventos-y-actores)
  
  - [1.6 V3C: proceso E2E y capacidades que realiza](#16-v3c-proceso-e2e-y-capacidades-que-realiza)
    
- [2. Descomposición de servicios del proceso E2E](#2-descomposición-de-servicios-del-proceso-e2e)
  - [2.1 V4a: del proceso E2E a los servicios de actividad](#21-v4a-del-proceso-e2e-a-los-servicios-de-actividad)
  
  - [2.2 V4b: descomposición en cuatro capas de servicio](#22-v4b-descomposición-en-cuatro-capas-de-servicio)
   
  - [2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos](#23-v4c-servicios-de-entidad-y-utilidad-roles-funciones-y-objetos-pasivos)

  - [2.4 V4D: capa anticorrupción e interoperabilidad](#24-v4d-capa-anticorrupción-e-interoperabilidad)
   
  - [2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)](#25-v4e-contract-first-contratos-de-los-servicios-de-actividad-capa-3)

  - [2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad](#26-v4f-contract-first-contratos-de-entidad-utilidad-e-interoperabilidad)
 
- [3. Dominios y lenguaje ubicuo](#3-dominios-y-lenguaje-ubicuo)
  - [3.1 V5: dominios y subdominios](#31-v5-dominios-y-subdominios)
    
  - [3.2 V7: lenguaje ubicuo](#32-v7-lenguaje-ubicuo)
    
  - [3.3 V7b: términos con varios significados](#33-v7b-términos-con-varios-significados)
    
  - [3.4 V10: Trazabilidad Vertical](#V10-trazabilidad-vertical)

# 1. Entendimiento del negocio y mapa de capacidades 

La Fase 1 responde seis preguntas, que se reparten entre las vistas así:
 
| Vista | Pregunta que responde |
|---|---|
| V1 | Por qué se necesita la aplicación: quién la necesita, qué problemas la justifican, qué metas persigue y qué requisitos, principios y restricciones se derivan |
| V2 | Qué es capaz de hacer la organización y en cuáles capacidades impacta la solución |
| V2b | Cómo dependen entre sí las capacidades de datos y qué recursos y cursos de acción las sostienen |
| V3a | Cuál es la cadena de valor del negocio, qué eventos la disparan y qué capacidades habilitan cada etapa |
| V3b | Cuál es el proceso E2E donde opera la aplicación, quién interviene y qué pasos apoya la solución |
| V3c | Qué capacidades realiza cada paso del proceso E2E |
 
Principio de modelado: una capacidad describe lo que la organización es capaz de hacer, no un proceso ni una actividad operativa. Por eso los nombres de las capacidades son sustantivos de habilidad ("Gestión de metadatos técnicos") y los pasos del proceso son verbos ("Importar metadatos técnicos").
 
Elementos de ArchiMate que se usan:
 
| Elemento | Capa | Uso en este modelo |
|---|---|---|
| Capability | Estrategia | Capacidades en tres niveles (Nivel 1, 2 y 3) |
| Value Stream | Estrategia | Etapas de la cadena de valor del negocio y de la cadena de gobierno de datos |
| Resource | Estrategia | Recursos que habilitan las capacidades de datos |
| Course of Action | Estrategia | Líneas de acción propuestas a partir de las metas de la entrevista |
| Stakeholder, Driver, Assessment, Goal, Outcome, Principle, Requirement y Constraint | Motivación | Quién necesita la aplicación y por qué: de la necesidad a la meta, los requisitos y las restricciones (V1) |
| Business Process | Negocio | Pasos del proceso E2E |
| Business Event | Negocio | Hechos que disparan una etapa o un paso |
| Business Actor y Business Role | Negocio | Quién ejecuta o responde por cada paso |
| Grouping | Otros | Franjas de la V2 |
 
Relaciones que se usan:
 
| Relación | Significado en este modelo |
|---|---|
| Composition | Una capacidad de Nivel 1 se compone de las de Nivel 2, y estas de las de Nivel 3 |
| Serving | La capacidad origen sirve a la capacidad o a la etapa destino; "A sirve a B" también se lee "B depende de A" |
| Realization | Un paso del proceso realiza una capacidad. En la V1, un resultado, un principio o un requisito realiza una meta, un resultado o un principio |
| Assignment | Un actor, rol o recurso se asigna a un paso o a una capacidad |
| Triggering | Secuencia entre etapas o pasos, o un evento que dispara una etapa o un paso |
| Association | Un curso de acción se ejecuta mediante una capacidad, o un evento se asocia con la etapa que dispara. En la V1, un interesado se asocia con un impulsor y un impulsor con una evaluación |
| Influence | Solo en la V1: una evaluación motiva una meta («motiva +») y una restricción limita un requisito («restringe») |
| Aggregation | Solo en la V1: una meta general se compone de sub-metas (se dibuja por anidamiento) |
 
---
 
## 1.1 V1: motivación de la solución, de la necesidad a la meta

![V1 - Motivación de la solución de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/main/motivacion/V1%20%C2%B7%20Motivaci%C3%B3n.png?raw=true)

### Qué muestra

La V1 responde una pregunta sencilla: ¿por qué hace falta esta aplicación? Parte de quién tiene la necesidad, pasa por lo que la origina y los problemas que hoy se viven, y llega a lo que se quiere lograr y a lo que la aplicación debe hacer y respetar. Son 56 elementos de la capa de Motivación de ArchiMate y 75 relaciones, todo en una sola vista.

### Cómo se lee

Se lee de arriba hacia abajo, en bandas, de la necesidad a la solución:

| Banda | Elementos | Qué responde |
|---|---|---|
| Interesados (internos y externos) | S1–S8 | ¿Quién tiene la necesidad? |
| Impulsores | D1–D5 | ¿Qué la origina? |
| Evaluaciones | A1–A9 | ¿Qué problema concreto se vive hoy? |
| Metas | G1, con G2–G6 dentro | ¿Qué se quiere lograr? |
| Resultados y principios | O1–O9, P1–P5 | ¿Cómo se sabrá que se logró y con qué criterios? |
| Requisitos | R1–R10 | ¿Qué debe hacer la aplicación? |
| Restricciones | C1–C4 | ¿Qué la limita? |

Dos detalles de dibujo: las sub-metas G2–G6 están dentro de G1 (así se muestra que G1 se compone de ellas, sin cinco líneas más) y el proveedor del CRM aparece dos veces, siempre como el mismo elemento, para no cruzar toda la vista con una línea.

Las líneas son de cuatro tipos:

| Relación | Cómo se ve en Archi | Dónde | Se lee |
|---|---|---|---|
| Asociación | Línea continua | Interesado–impulsor, impulsor–evaluación | «le importa» / «hace evidente» |
| Influencia «motiva +» | Discontinua, flecha abierta | Evaluación → meta | el problema empuja a lograr la meta |
| Influencia «restringe» | Discontinua, flecha abierta | Restricción → requisito | la restricción limita al requisito |
| Realización | Discontinua, triángulo vacío | Resultado o principio → meta; requisito → resultado o principio | «ayuda a lograr» |

El «+» indica que la evaluación favorece la meta; «restringe» no lleva signo porque limita en lugar de empujar.

> **Sobre los códigos.** Los de esta vista (S, D, A, G, O, P, R, C) son propios de la V1. En el resto del documento, S1–S4 son los sistemas fuente y P1–P9 los pasos del proceso E2E.

### De la necesidad a la meta

Cada meta nace de uno o más problemas actuales, y cada problema se hace evidente por un impulsor. Entre paréntesis van los impulsores asociados al problema:

| Meta | Problemas actuales que la motivan |
|---|---|
| G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | A9 · Documentación de cumplimiento incompleta (D1, D2) |
| G2 · Conocer los datos que maneja la empresa | A1 · No existe un diccionario de datos integrado (D4, D5)<br>A6 · Datos personales en canales informales sin inventario (D1, D3) |
| G3 · Clasificar los datos | A4 · Clasificación de datos intuitiva y sin documentar (D1, D3) |
| G4 · Describir los datos con un lenguaje común | A1 · No existe un diccionario de datos integrado (D4, D5)<br>A2 · Términos de negocio ambiguos y sin catálogo (D4)<br>A3 · Atributos sin responsable formal (D1)<br>A5 · Reglas de calidad dispersas y desiguales (D4) |
| G5 · Mantener el diccionario vigente y trazable | A7 · Cambios de estructura y de finalidad sin registro (D2, D5) |
| G6 · Contar con evidencia consultable del gobierno de datos | A8 · La cobertura de metadatos no se mide (D2) |

Un ejemplo completo: a Jurídica le importa el cumplimiento de la Ley 1581 (D1), que hoy se ve afectado porque la clasificación de los datos es intuitiva y no está documentada (A4). Eso motiva la meta de clasificar los datos (G3), que se logra con el resultado «atributos con clasificación registrada» (O3). El requisito que lo hace posible es registrar la clasificación de cada atributo (R2), y lo limita que las obligaciones legales están por verificar con Jurídica (C2).

### Interesados

| Código | Interesado | Qué necesita |
|---|---|---|
| S1 | Gerencia general | Reducir el riesgo legal y reputacional y contar con información confiable para decidir; ver avances medibles |
| S2 | Jurídica / protección de datos | Saber qué datos personales existen, cómo están clasificados y quién responde por ellos |
| S3 | Responsables de datos por área | Un lugar único donde definir y consultar el significado y la calidad de sus datos |
| S4 | Equipo de TI | Documentar la estructura técnica, ligarla al significado de negocio y saber qué impacto tiene un cambio |
| S5 | Titulares de los datos | Que sus datos se traten conforme a la ley y a la finalidad autorizada (no usan la aplicación) |
| S6 | Superintendencia de Industria y Comercio (SIC) | Que la empresa pueda demostrar cómo administra los datos personales; el formato y la obligación de reporte están por verificar |
| S7 | Seguridad de la información | Saber dónde están los datos privados y sensibles para priorizar controles |
| S8 | Proveedor del CRM | Controlar qué estructura de su plataforma expone; de él depende la entrega de los metadatos del CRM |

Todos son supuestos del escenario, salvo Seguridad de la información (S7), que es una propuesta del equipo por validar.

### Impulsores y problemas actuales

| Código | Impulsor | Qué lo origina |
|---|---|---|
| D1 | Cumplimiento de la Ley 1581 de 2012 | Obligación de proteger los datos personales; la aplicación apoya el cumplimiento, no lo garantiza |
| D2 | Rendición de cuentas ante la SIC | Poder demostrar con información clara cómo se administran los datos personales |
| D3 | Riesgo de exposición de datos personales | Hay datos personales en hojas de cálculo, carpetas, correo y WhatsApp, y atributos delicados (ingresos, mora, menores) |
| D4 | Calidad y coherencia de la información | La operación depende de datos consistentes y hoy hay campos ambiguos y digitación repetida |
| D5 | Fragmentación de sistemas y fuentes | Varios motores, proveedores y canales informales, sin un diccionario técnico central |

| Código | Problema actual | En qué consiste |
|---|---|---|
| A1 | No existe un diccionario de datos integrado | Lo técnico (en cada motor) y lo de negocio (conocimiento tácito) están separados |
| A2 | Términos de negocio ambiguos y sin catálogo | «Cliente», «activo» o «canon» significan cosas distintas según el área |
| A3 | Atributos sin responsable formal | Nadie aprueba las definiciones; TI conoce la estructura, pero no siempre el significado |
| A4 | Clasificación de datos intuitiva y sin documentar | Se clasifica por intuición, con casos dudosos (direcciones, ingresos, mora, datos de menores) |
| A5 | Reglas de calidad dispersas y desiguales | Cada sistema valida distinto y los errores se detectan después de ocurrir |
| A6 | Datos personales en canales informales sin inventario | Hojas, carpetas, correo y WhatsApp no tienen diccionario técnico; requieren inventario manual |
| A7 | Cambios de estructura y de finalidad sin registro | Se agregan o cambian campos, o el uso de un dato, sin aviso ni revisión de su clasificación |
| A8 | La cobertura de metadatos no se mide | No hay línea base de cuántos atributos tienen definición, responsable o clasificación |
| A9 | Documentación de cumplimiento incompleta | Autorizaciones dispersas y sin procedimiento de solicitudes; se resuelve sobre todo con procesos, fuera de la aplicación |

### Metas y resultados esperados

Las metas dicen qué se quiere lograr; los resultados, cómo se sabrá que se logró.

| Meta | Qué busca | Resultados que la realizan |
|---|---|---|
| G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | Meta general: dar información clara sobre qué datos hay, cómo están clasificados y quién responde por ellos. No sustituye los procesos legales ni de seguridad | Se compone de G2 a G6 |
| G2 · Conocer los datos que maneja la empresa | Inventario de atributos y fuentes, estructuradas y no estructuradas | O1 · Metadatos técnicos de S1–S4 importados<br>O2 · Fuentes no estructuradas inventariadas |
| G3 · Clasificar los datos | Una categoría por atributo (público, semiprivado, privado, sensible), con revisión jurídica | O3 · Atributos con clasificación registrada |
| G4 · Describir los datos con un lenguaje común | Definición, responsable, política de calidad, expresión regular y términos de negocio por atributo | O4 · Atributos con definición y responsable asignados<br>O5 · Atributos con política de calidad y regla de validación<br>O6 · Términos asociados a atributos y conflictos identificados<br>O7 · Diccionario integrado consultable por atributo |
| G5 · Mantener el diccionario vigente y trazable | Que los cambios, las importaciones y las decisiones queden registrados | O8 · Historial de importaciones y cambios disponible |
| G6 · Contar con evidencia consultable del gobierno de datos | Que Jurídica, Seguridad y la dirección puedan consultar y exportar la información | O9 · Metadatos consultables y exportables para revisión |

G2, G3 y G4 salen del enunciado; G5 y G6 son propuestas del equipo derivadas del escenario. Los indicadores de los resultados (por ejemplo, columnas importadas sobre columnas existentes) son candidatos y no llevan cifras, porque las del escenario son ficticias.

### Principios, requisitos y restricciones

| Código | Principio | Idea | Orienta a |
|---|---|---|---|
| P1 | El negocio es dueño del significado de sus datos | Define y aprueba el responsable de negocio; TI administra lo técnico | G4 |
| P2 | Mostrar lo faltante o dudoso como tal | Un atributo incompleto o «en revisión» no se presenta como correcto | G3, G4 |
| P3 | Gobernar metadatos sin modificar los sistemas operativos | Se documenta y gobierna; no se corrigen datos ni se reemplazan los sistemas | G1 |
| P4 | Un término, una definición vigente | Los conflictos de significado se hacen explícitos | G4 |
| P5 | La decisión jurídica es de Jurídica | La aplicación registra y propone; Jurídica valida la categoría final | G3 |

| Código | Requisito | Realiza | Origen |
|---|---|---|---|
| R1 | Importar metadatos técnicos desde los motores | O1, P3 | Enunciado |
| R2 | Registrar la clasificación de cada atributo | O3, P2, P5 | Enunciado |
| R3 | Registrar definición y responsable por atributo | O4, P1 | Enunciado |
| R4 | Registrar políticas de calidad y expresiones regulares | O5 | Enunciado |
| R5 | Gestionar el diccionario de datos integrado | O7 | Enunciado |
| R6 | Gestionar el catálogo de términos y asociarlos a atributos | O6, P4 | Enunciado |
| R7 | Registrar manualmente fuentes no estructuradas | O2 | Propuesta del equipo (por validar) |
| R8 | Registrar importaciones y detectar cambios de estructura | O8 | Propuesta del equipo (por validar) |
| R9 | Consultar y exportar metadatos | O9 | Propuesta del equipo (por validar) |
| R10 | Gestionar roles de edición y aprobación | O4, P1, P5 | Propuesta del equipo (por validar) |

| Código | Restricción | Limita a | Por qué |
|---|---|---|---|
| C1 | Solo lectura de estructura; sin leer datos personales | R1 | La herramienta lee metadatos, no los registros con datos personales |
| C2 | Obligaciones legales por verificar con Jurídica | R2 | Las categorías finales se contrastan con fuentes oficiales |
| C3 | Acceso a metadatos del CRM depende del proveedor | R1 | Los tiempos y permisos no los controla la empresa |
| C4 | Fuera de alcance: autorizaciones, solicitudes de titulares y depuración | R9 | Solo se interopera con esos procesos; no hay integración automática con la SIC |

### Justificación

La vista deja claro por qué se necesita la aplicación y hasta dónde llega. Las metas G2, G3 y G4 y los requisitos R1–R6 corresponden al alcance del enunciado; G5, G6 y R7–R10 son propuestas del equipo que hay que validar. Lo que la aplicación no cubre, como las restricciones y los problemas que se resuelven con procesos (A9), es coherente con las capacidades fuera de alcance de la V2 y con los servicios excluidos de la V4b: la aplicación documenta y gobierna metadatos, no corrige datos ni reemplaza los procesos legales, de seguridad o de operación.

### Supuestos y puntos por validar

- **Caso ficticio.** Hogar Andino se modela tal como lo planteó la entrevista; cifras, cargos y sistemas no son hechos reales.
- **Roles sin definir.** El cargo de oficial de protección de datos no existe todavía, y Seguridad de la información se trata como interesado propio aunque podría ser parte de TI. Quién propone, revisa y aprueba definiciones y clasificaciones (R10) queda por definir con la organización.
- **Alcance.** La aplicación solo lee estructura (C1) y no hay integración automática con la SIC: se exporta el informe y Jurídica lo presenta.
- **Meta realista.** «Cumplir la ley» no lo logra un software, por eso la meta es apoyar el cumplimiento (G1).
- **Categorías legales.** El enunciado atribuye la clasificación público, semiprivado, privado y sensible a la Ley 1581, pero esa distinción parece venir sobre todo de la Ley 1266 de 2008 (la 1581 define el dato sensible). Hay que confirmarlo con fuentes oficiales antes de citarlo (C2, P5).
- **Interesados externos.** Titulares y SIC no usan la aplicación: su necesidad se infiere de la ley y de la entrevista, no se validó con ellos.
- **Guion de la Fase 0.** Las preguntas del Bloque 6 repiten las del Bloque 7, aunque sus hallazgos hablan de indicadores; conviene corregir el guion.

<details>
<summary><b>Anexo: las 80 relaciones de la V1 y su justificación</b></summary>

| Tipo | Origen | Destino | Justificación |
|---|---|---|---|
| Asociación | S1 · Gerencia general | D1 · Cumplimiento de la Ley 1581 de 2012 | La gerencia responde ante la ley por el tratamiento de datos de la empresa. |
| Asociación | S1 · Gerencia general | D3 · Riesgo de exposición de datos personales | La gerencia asume el riesgo legal y reputacional de una exposición de datos. |
| Asociación | S1 · Gerencia general | D4 · Calidad y coherencia de la información | Necesita información coherente para operar y decidir. |
| Asociación | S2 · Jurídica / protección de datos | D1 · Cumplimiento de la Ley 1581 de 2012 | Jurídica vela por el cumplimiento de la Ley 1581 y orienta a las áreas. |
| Asociación | S2 · Jurídica / protección de datos | D2 · Rendición de cuentas ante la SIC | Jurídica prepara y valida la información que eventualmente se presente a la SIC. |
| Asociación | S3 · Responsables de datos por área | D4 · Calidad y coherencia de la información | Cada área sufre inconsistencias, reprocesos y términos ambiguos en sus propios datos. |
| Asociación | S3 · Responsables de datos por área | D5 · Fragmentación de sistemas y fuentes | Las áreas digitan y consultan datos en varios sistemas y canales. |
| Asociación | S4 · Equipo de TI | D5 · Fragmentación de sistemas y fuentes | TI administra los sistemas fragmentados y recibe el impacto de sus cambios. |
| Asociación | S5 · Titulares de los datos | D1 · Cumplimiento de la Ley 1581 de 2012 | La ley protege los derechos de los titulares sobre sus datos. |
| Asociación | S5 · Titulares de los datos | D3 · Riesgo de exposición de datos personales | Los titulares son quienes sufren la exposición de sus datos. |
| Asociación | S6 · Superintendencia de Industria y Comercio (SIC) | D1 · Cumplimiento de la Ley 1581 de 2012 | La SIC vigila el cumplimiento de la ley de protección de datos. |
| Asociación | S6 · Superintendencia de Industria y Comercio (SIC) | D2 · Rendición de cuentas ante la SIC | La SIC es la autoridad ante la cual la empresa rinde cuentas. |
| Asociación | S7 · Seguridad de la información | D3 · Riesgo de exposición de datos personales | Seguridad necesita saber dónde están los datos de mayor riesgo para protegerlos. |
| Asociación | S8 · Proveedor del CRM | D5 · Fragmentación de sistemas y fuentes | El CRM es una plataforma externa; su estructura sólo se obtiene a través del proveedor. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A3 · Atributos sin responsable formal | Cumplir exige saber quién responde por cada dato; hoy no hay responsable formal. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A4 · Clasificación de datos intuitiva y sin documentar | Aplicar la ley exige clasificar los datos; hoy la clasificación es intuitiva. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A6 · Datos personales en canales informales sin inventario | Los datos personales en canales informales escapan al control que exige la ley. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A9 · Documentación de cumplimiento incompleta | La obligación legal se evidencia con documentación que hoy está incompleta. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A7 · Cambios de estructura y de finalidad sin registro | Rendir cuentas requiere trazabilidad de cambios; hoy no se registran. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A8 · La cobertura de metadatos no se mide | No se puede demostrar avance sin medir la cobertura de metadatos. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A9 · Documentación de cumplimiento incompleta | Sin políticas y procedimientos documentados no hay evidencia que presentar. |
| Asociación | D3 · Riesgo de exposición de datos personales | A4 · Clasificación de datos intuitiva y sin documentar | Sin clasificar no se sabe qué datos privados o sensibles necesitan más protección. |
| Asociación | D3 · Riesgo de exposición de datos personales | A6 · Datos personales en canales informales sin inventario | Los canales informales son la mayor superficie de exposición. |
| Asociación | D4 · Calidad y coherencia de la información | A1 · No existe un diccionario de datos integrado | La información no es coherente cuando metadatos técnicos y de negocio están separados. |
| Asociación | D4 · Calidad y coherencia de la información | A2 · Términos de negocio ambiguos y sin catálogo | Términos ambiguos producen interpretaciones distintas del mismo dato. |
| Asociación | D4 · Calidad y coherencia de la información | A5 · Reglas de calidad dispersas y desiguales | Reglas de validación dispersas generan datos inconsistentes entre sistemas. |
| Asociación | D5 · Fragmentación de sistemas y fuentes | A1 · No existe un diccionario de datos integrado | Cada sistema tiene su propio diccionario técnico, sin integración entre ellos. |
| Asociación | D5 · Fragmentación de sistemas y fuentes | A7 · Cambios de estructura y de finalidad sin registro | La fragmentación hace que los cambios de estructura no se comuniquen. |
| Influencia | A1 · No existe un diccionario de datos integrado | G2 · Conocer los datos que maneja la empresa | Sin diccionario no se sabe con certeza qué datos existen en cada sistema. |
| Influencia | A1 · No existe un diccionario de datos integrado | G4 · Describir los datos con un lenguaje común | Describir exige unir lo técnico y lo de negocio en un solo lugar. |
| Influencia | A2 · Términos de negocio ambiguos y sin catálogo | G4 · Describir los datos con un lenguaje común | Un lenguaje común exige un catálogo de términos asociado a atributos. |
| Influencia | A3 · Atributos sin responsable formal | G4 · Describir los datos con un lenguaje común | Describir incluye asignar y mantener un responsable por atributo. |
| Influencia | A4 · Clasificación de datos intuitiva y sin documentar | G3 · Clasificar los datos | La clasificación intuitiva y sin registro motiva clasificar de forma sistemática. |
| Influencia | A5 · Reglas de calidad dispersas y desiguales | G4 · Describir los datos con un lenguaje común | Las políticas de calidad y expresiones regulares forman parte de la descripción del atributo. |
| Influencia | A6 · Datos personales en canales informales sin inventario | G2 · Conocer los datos que maneja la empresa | Hay que inventariar las fuentes no estructuradas para conocer todos los datos. |
| Influencia | A7 · Cambios de estructura y de finalidad sin registro | G5 · Mantener el diccionario vigente y trazable | Los cambios sin registro motivan mantener el diccionario vigente y trazable. |
| Influencia | A8 · La cobertura de metadatos no se mide | G6 · Contar con evidencia consultable del gobierno de datos | Sin cobertura medida no hay evidencia consultable del gobierno de datos. |
| Influencia | A9 · Documentación de cumplimiento incompleta | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | La documentación incompleta justifica la meta general; la aplicación sólo cubre la parte de metadatos. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G2 · Conocer los datos que maneja la empresa | 'Conocer' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G3 · Clasificar los datos | 'Clasificar' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G4 · Describir los datos con un lenguaje común | 'Describir' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G5 · Mantener el diccionario vigente y trazable | Sin vigencia y trazabilidad el diccionario pierde valor con el tiempo. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G6 · Contar con evidencia consultable del gobierno de datos | Apoyar el cumplimiento implica poder mostrar evidencia. |
| Realización | O1 · Metadatos técnicos de S1–S4 importados | G2 · Conocer los datos que maneja la empresa | Con los metadatos técnicos importados se conoce la estructura de los datos de S1–S4. |
| Realización | O2 · Fuentes no estructuradas inventariadas | G2 · Conocer los datos que maneja la empresa | Inventariar lo no estructurado completa el conocimiento de los datos. |
| Realización | O3 · Atributos con clasificación registrada | G3 · Clasificar los datos | Un atributo con categoría o estado registrado evidencia que fue clasificado. |
| Realización | O4 · Atributos con definición y responsable asignados | G4 · Describir los datos con un lenguaje común | Definición y responsable son parte central de la descripción. |
| Realización | O5 · Atributos con política de calidad y regla de validación | G4 · Describir los datos con un lenguaje común | Políticas de calidad y reglas de validación describen cómo debe ser el dato. |
| Realización | O6 · Términos asociados a atributos y conflictos identificados | G4 · Describir los datos con un lenguaje común | Términos asociados a atributos dan el lenguaje común. |
| Realización | O7 · Diccionario integrado consultable por atributo | G4 · Describir los datos con un lenguaje común | El diccionario integrado reúne la descripción técnica y de negocio. |
| Realización | O8 · Historial de importaciones y cambios disponible | G5 · Mantener el diccionario vigente y trazable | El historial muestra que el diccionario se mantiene vigente. |
| Realización | O9 · Metadatos consultables y exportables para revisión | G6 · Contar con evidencia consultable del gobierno de datos | Poder consultar y exportar es la evidencia que se necesita. |
| Realización | P1 · El negocio es dueño del significado de sus datos | G4 · Describir los datos con un lenguaje común | La responsabilidad de negocio hace confiable la descripción de los datos. |
| Realización | P2 · Mostrar lo faltante o dudoso como tal | G3 · Clasificar los datos | Un estado 'en revisión' evita presentar como definitiva una clasificación dudosa. |
| Realización | P2 · Mostrar lo faltante o dudoso como tal | G4 · Describir los datos con un lenguaje común | Lo incompleto debe verse como incompleto en la descripción. |
| Realización | P3 · Gobernar metadatos sin modificar los sistemas operativos | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | Delimita la meta general: se gobiernan metadatos, no se reemplazan procesos operativos. |
| Realización | P4 · Un término, una definición vigente | G4 · Describir los datos con un lenguaje común | Una definición vigente por término es la base del lenguaje común. |
| Realización | P5 · La decisión jurídica es de Jurídica | G3 · Clasificar los datos | La clasificación sólo es confiable si la valida quien tiene competencia jurídica. |
| Realización | R1 · Importar metadatos técnicos desde los motores | O1 · Metadatos técnicos de S1–S4 importados | Importar desde los diccionarios de los motores produce los metadatos técnicos. |
| Realización | R7 · Registrar manualmente fuentes no estructuradas | O2 · Fuentes no estructuradas inventariadas | El registro manual es la única vía para inventariar fuentes sin motor de base de datos. |
| Realización | R2 · Registrar la clasificación de cada atributo | O3 · Atributos con clasificación registrada | Registrar categoría y estado produce atributos clasificados o pendientes. |
| Realización | R3 · Registrar definición y responsable por atributo | O4 · Atributos con definición y responsable asignados | Registrar definición y responsable produce atributos descritos. |
| Realización | R10 · Gestionar roles de edición y aprobación | O4 · Atributos con definición y responsable asignados | Roles de edición y aprobación aseguran que definición y responsable tengan dueño y autoridad. |
| Realización | R4 · Registrar políticas de calidad y expresiones regulares | O5 · Atributos con política de calidad y regla de validación | Registrar políticas y expresiones regulares produce los atributos con regla. |
| Realización | R6 · Gestionar el catálogo de términos y asociarlos a atributos | O6 · Términos asociados a atributos y conflictos identificados | El catálogo y sus asociaciones producen los términos vinculados a atributos. |
| Realización | R5 · Gestionar el diccionario de datos integrado | O7 · Diccionario integrado consultable por atributo | Gestionar el diccionario integrado produce la vista consultable por atributo. |
| Realización | R8 · Registrar importaciones y detectar cambios de estructura | O8 · Historial de importaciones y cambios disponible | Registrar importaciones y cambios produce el historial. |
| Realización | R9 · Consultar y exportar metadatos | O9 · Metadatos consultables y exportables para revisión | Consultar y exportar produce los metadatos disponibles para revisión. |
| Realización | R1 · Importar metadatos técnicos desde los motores | P3 · Gobernar metadatos sin modificar los sistemas operativos | Importa estructura sin escribir en los sistemas de origen. |
| Realización | R2 · Registrar la clasificación de cada atributo | P2 · Mostrar lo faltante o dudoso como tal | El estado 'pendiente' / 'en revisión' hace visible lo dudoso. |
| Realización | R2 · Registrar la clasificación de cada atributo | P5 · La decisión jurídica es de Jurídica | El estado 'en revisión' permite la validación jurídica antes de dar por final una categoría. |
| Realización | R3 · Registrar definición y responsable por atributo | P1 · El negocio es dueño del significado de sus datos | El responsable de negocio queda registrado por atributo. |
| Realización | R10 · Gestionar roles de edición y aprobación | P1 · El negocio es dueño del significado de sus datos | Define quién propone y aprueba sin dar esa autoridad automáticamente a TI. |
| Realización | R10 · Gestionar roles de edición y aprobación | P5 · La decisión jurídica es de Jurídica | Incluye la aprobación jurídica de clasificaciones. |
| Realización | R6 · Gestionar el catálogo de términos y asociarlos a atributos | P4 · Un término, una definición vigente | El catálogo mantiene una definición vigente por término. |
| Influencia | C1 · Solo lectura de estructura; sin leer datos personales | R1 · Importar metadatos técnicos desde los motores | La importación se limita a estructura y no debe leer registros con datos personales. |
| Influencia | C3 · Acceso a metadatos del CRM depende del proveedor | R1 · Importar metadatos técnicos desde los motores | La importación desde el CRM depende de lo que entregue el proveedor. |
| Influencia | C2 · Obligaciones legales por verificar con Jurídica | R2 · Registrar la clasificación de cada atributo | La categoría final depende de la verificación jurídica con fuentes oficiales. |
| Influencia | C4 · Fuera de alcance: autorizaciones, solicitudes de titulares y depuración | R9 · Consultar y exportar metadatos | La exportación apoya los reportes, pero no se asume integración automática con la SIC. |
| Asociación | S8 · Proveedor del CRM | C3 · Acceso a metadatos del CRM depende del proveedor | El proveedor del CRM es quien condiciona el acceso a la estructura de S2. |

</details>

---

## 1.2 V2: mapa de capacidades
 
![V2 - Mapa de capacidades de Hogar Andino](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V2%20-%20Mapa%20de%20Capacidades%20de%20Hogar%20Andino.png)
 
### Qué muestra
 
El mapa de capacidades completo del negocio, con 78 elementos Capability organizados en tres niveles: 13 de Nivel 1, 44 de Nivel 2 y 21 de Nivel 3. Las capacidades se agrupan en cuatro franjas. El color de cada caja indica el impacto de la solución de gobierno de datos, y la leyenda está en la parte superior de la vista.
 
### Cómo se lee
 
La vista usa anidamiento: el Nivel 1 contiene a sus capacidades de Nivel 2, y estas a las de Nivel 3 (relación Composition representada por contención). Solo los bloques de gestión de datos y de cumplimiento se detallan hasta Nivel 3; el resto del negocio llega a Nivel 2. Las cinco flechas de la vista son relaciones Serving que parten de Gestión de Datos e Información hacia las capacidades que consumen sus resultados.
 
### Franjas y capacidades de Nivel 1
 
| Franja | Capacidades de Nivel 1 | Rol estratégico |
|---|---|---|
| Dirección y Cumplimiento | Planeación y Dirección Estratégica; Gestión de Cumplimiento y Riesgos | Soporte; Habilitadora crítica |
| Capacidades Core del Negocio inmobiliario | Gestión del Portafolio Inmobiliario; Comercialización de Inmuebles; Administración de Arrendamientos; Gestión de Relaciones con Clientes | Diferenciadoras (las tres primeras); Soporte |
| Gestión de Datos e Información | Gestión de Datos e Información, con Gobierno de Datos, Gestión de Metadatos, Clasificación de Datos, Gestión de la Calidad de Datos, Gestión de Datos Maestros y Gestión del Ciclo de Vida de los Datos | Habilitadora crítica |
| Capacidades Habilitadoras | Mercadeo y Canales Digitales; Gestión Financiera y Contable; Gestión Jurídica y Contractual; Gestión de Tecnología de la Información; Gestión del Talento Humano; Gestión Administrativa y de Compras | Soporte (las cuatro primeras) y Genérica (las dos últimas) |
 
### Propiedades de cada capacidad
 
Cada elemento Capability lleva 7 propiedades, que se pueden mostrar en Archi con una expresión de etiqueta:
 
| Propiedad | Valores usados |
|---|---|
| Nivel | Nivel 1, Nivel 2, Nivel 3 |
| Tipo de capacidad | Estratégica (22) o Táctica (56) |
| Rol estratégico (empresa) | Habilitadora crítica (33), Soporte (22), Diferenciadora (16), Genérica (7) |
| Impacto de la solución | Directo (12), Parcial (6), Indirecto (36), Fuera de alcance como brecha (9), Sin impacto (15) |
| Madurez actual (según entrevista) | Inexistente (17), Informal (24), No evaluada (37) |
| Estado de validación | Respaldada por la entrevista (64), Parcialmente respaldada (4), Inferida por validar con el experto (10) |
| Apoyo de la solución | Solo en los pasos del proceso (se usa en V3b y V3c) |

El mapa no clasifica las capacidades en subdominios DDD (Core, Supporting, Generic). Esa clasificación se hace en la fase de dominios, porque una capacidad no equivale a un subdominio ni a un contexto delimitado.
 
### Impacto de la solución
 
| Impacto | Significado | Capacidades |
|---|---|---|
| Directo | La solución opera aquí | Gestión de Datos e Información; Gestión de Metadatos; Clasificación de Datos; Gestión de responsables de datos; Gestión de trazabilidad y evidencia de decisiones; Gestión de metadatos de negocio; Gestión de metadatos técnicos; Gestión del diccionario de datos; Gestión del catálogo de términos de negocio; Inventario de atributos de negocio; Clasificación de atributos por categoría legal; Definición de políticas y reglas de calidad y validación |
| Parcial | La solución registra o prepara, pero la decisión o la ejecución es humana | Gobierno de Datos; Gestión de la Calidad de Datos; Resolución de conflictos y decisiones sobre datos; Gestión de cambios de estructura de datos; Validación jurídica de la clasificación; Reporte regulatorio ante la SIC |
| Indirecto | La capacidad consume o produce datos que la solución describe | 36 capacidades, entre ellas las del negocio inmobiliario y los bloques de cumplimiento y TI |
| Fuera de alcance (brecha) | Capacidad que el negocio necesita pero la solución no cubre | Políticas de tratamiento y avisos; autorizaciones de titulares; incidentes con datos personales; encargados del tratamiento; definición de políticas y principios de datos; medición y monitoreo de la calidad; depuración y duplicados; Gestión de Datos Maestros; Gestión del Ciclo de Vida de los Datos |
| Sin impacto | La solución no interviene | 15 capacidades, por ejemplo tesorería, talento humano y compras |
 
### Justificación
 
El dominio principal es Gobierno de Datos orientado a la protección de datos personales. Esta capacidad no diferencia a la inmobiliaria en el mercado: es una habilitadora crítica de cumplimiento, y solo es central dentro de la solución, donde el diccionario y la clasificación son lo que conviene construir con más cuidado. Las capacidades diferenciadoras del negocio son las de portafolio, comercialización y administración de arrendamientos.
 
Las capacidades fuera de alcance se dibujan en gris a propósito: hacen visible lo que la solución no cubre, para no prometer más de lo que entrega. La madurez "No evaluada" de 37 capacidades indica que la entrevista no cubre ese bloque y que debe validarse con el experto del negocio.
 
---
 
## 1.3 V2b: dependencias de gobierno de datos, recursos y cursos de acción
 
![V2b - Dependencias de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V2b%20-%20Dependencias%20de%20Gobierno%20de%20Datos.png)
 
### Qué muestra
 
El detalle del bloque de datos en columnas: 23 capacidades relacionadas por Serving, 7 recursos asignados a las capacidades que habilitan y 3 cursos de acción asociados a las capacidades que los ejecutan. La vista tiene 39 conexiones.
 
### Cómo se lee
 
La relación usada es Serving y se lee "A sirve a B", es decir, B depende de A. El orden de izquierda a derecha es: proveedores de servicio, gobierno, captura, integración y clasificación, y consumidores. Los recursos están en la parte inferior y los cursos de acción en la superior.
 
### Cadenas de dependencia
 
| Cadena | Razón |
|---|---|
| Gestión de metadatos técnicos, Inventario de atributos de negocio, Clasificación de atributos por categoría legal | No se clasifica lo que no se ha inventariado |
| Definición de políticas y principios, Validación jurídica y Resolución de conflictos, Clasificación de atributos | La categoría necesita criterio, aprobación y desempate |
| Gestión de metadatos técnicos, Gestión de metadatos de negocio y Clasificación, Gestión del diccionario de datos, Gestión del catálogo de términos | El diccionario integra todo y el catálogo se apoya en él |
| Gestión del diccionario y Clasificación, Atención de derechos de los titulares, Reporte regulatorio ante la SIC, Gestión de la seguridad de la información | Son los consumidores de la información |
| Gestión de aplicaciones y proveedores y Administración de accesos, Gestión de metadatos técnicos y Gestión de cambios de estructura | Sin acceso de solo lectura no hay importación |
| Gestión de responsables de datos y Definición de políticas y reglas de calidad, Gestión de metadatos de negocio | El metadato de negocio necesita dueño y regla |
| Gestión de trazabilidad y evidencia de decisiones, Reporte regulatorio ante la SIC | La evidencia de quién decidió y con qué criterio respalda el reporte |
 
### Recursos
 
| Recurso | Capacidad que habilita |
|---|---|
| Diccionarios de los motores de S1, S3 (SQL Server) y S4 (MySQL) | Gestión de metadatos técnicos |
| Consulta de solo lectura sobre la estructura del CRM S2 (PostgreSQL), vía proveedor | Gestión de metadatos técnicos |
| Conocimiento jurídico (abogada interna y abogado externo) | Validación jurídica de la clasificación |
| Coordinador de TI | Gestión de aplicaciones y proveedores de software |
| Responsables de dato por área (por designar) | Gestión de responsables de datos |
| Oficial de protección de datos (cargo por decidir) | Atención de derechos de los titulares |
| Marco normativo: Ley 1581 de 2012, Ley 1266 de 2008, Decreto 1074 de 2015 y guías de la SIC | Gestión del cumplimiento normativo |
 
### Cursos de acción
 
Son propuestas del equipo basadas en las metas de ejemplo del Bloque 6 de la entrevista, por validar:
 
| Curso de acción | Se ejecuta mediante |
|---|---|
| Inventariar y clasificar primero los atributos con datos personales | Inventario de atributos de negocio; Clasificación de atributos por categoría legal |
| Documentar la estructura técnica de S1, S3 y S4 y gestionar S2 vía proveedor | Gestión de metadatos técnicos |
| Establecer roles de gobierno (oficial, responsables de dato) y registrar decisiones | Gestión de responsables de datos; Gestión de trazabilidad y evidencia de decisiones |
 
### Cuellos de botella externos
 
La vista deja ver tres dependencias que no controla el equipo: el proveedor de S2, que debe entregar la estructura; la disponibilidad de Jurídica para validar clasificaciones; y la designación pendiente del oficial de protección de datos y de los responsables de dato.
 
---
 
## 1.4 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan
 
![V3a - Cadena de valor del negocio](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3a%20-%20Cadena%20de%20valor%20del%20negocio.png)
 
### Qué muestra
 
La cadena de valor primaria "Intermediación inmobiliaria (de la captación al cierre)" con seis etapas encadenadas por Triggering, tres eventos de negocio que disparan etapas y, bajo cada etapa, las capacidades que la habilitan (Serving). En la franja superior aparece la cadena de soporte "Gobierno de datos personales" y las tres capacidades transversales que sirven a toda la cadena.
 
### Cómo se lee
 
Las etapas van de izquierda a derecha. Las cajas bajo cada etapa son capacidades de la V2 que sirven a esa etapa; una misma capacidad puede aparecer en varias columnas porque sirve a más de una etapa. Cada evento se une con su etapa mediante una Association rotulada "dispara la etapa".
 
### Etapas de la cadena de valor
 
| Etapa | Qué ocurre | Capacidades que la habilitan |
|---|---|---|
| Captar y publicar | Captación del propietario con contrato de corretaje, fotos y publicación en web y portales | Captación de propietarios e inmuebles; Gestión de la información del inmueble; Valoración y fijación de precios de inmuebles; Gestión de contenidos de inmuebles; Gestión de canales web y portales |
| Atender interesados | Recepción por web, portales, teléfono y WhatsApp y registro en el CRM | Gestión de interesados; Atención de visitas y negociación; Gestión del conocimiento del cliente; Gestión de canales web y portales |
| Evaluar y negociar | Estudio y aprobación del candidato (arriendo) u oferta y negociación con revisión jurídica (venta) | Evaluación de candidatos a arrendamiento; Atención de visitas y negociación; Asesoría y revisión legal |
| Formalizar | Firma del contrato de arriendo, o promesa de compraventa y escritura | Gestión de contratos de arrendamiento; Gestión de la venta de inmuebles; Asesoría y revisión legal |
| Administrar la vigencia | Solo arriendo: cobro mensual, pago al propietario, reparaciones, reajuste anual y renovación | Gestión de contratos de arrendamiento; recaudo y cartera; pagos a propietarios; novedades y mantenimiento; contable y de facturación; tesorería; cobro jurídico; peticiones, quejas y reclamos |
| Cerrar | Acta de entrega y devolución de depósitos (arriendo) o liquidación de comisión (venta) | Renovación y cierre de contratos; Entrega de inmuebles y devolución de depósitos; Gestión de comisiones; Gestión contable y de facturación |
 
El arriendo recorre las seis etapas. La venta omite "Administrar la vigencia" y termina en "Cerrar" con la liquidación de la comisión.
 
### Eventos
 
| Evento | Etapa que dispara | Regla o efecto |
|---|---|---|
| Candidato aprobado | Formalizar | Un arriendo no se firma sin estudio aprobado |
| Contrato de arrendamiento firmado | Administrar la vigencia | Nacen los datos de las partes, que hoy se digitan de nuevo en S1 |
| Vencimiento o terminación del contrato | Cerrar | Da paso al acta de entrega y a la devolución de depósitos |
 
### Capacidades transversales y cadena de soporte
 
Tres capacidades sirven a toda la cadena de intermediación: Gestión de Datos e Información, Gestión de la protección de datos personales y Gestión de Tecnología de la Información. La cadena "Gobierno de datos personales (del dato desconocido al dato gobernado)" también se relaciona con la primaria mediante Serving: gobierna los datos que nacen en cada etapa de la intermediación (identificación y contacto del propietario, estudio financiero del candidato, contrato, pagos y mora, acta y saldos).
 
### Justificación
 
Esta vista ubica la solución dentro del negocio: la aplicación no es una etapa de la cadena primaria, sino una cadena de soporte cuyo insumo son los datos que producen esas etapas. Las capacidades de la V2 quedan ancladas a etapas concretas, así se puede responder en qué momento del negocio cada capacidad aporta valor.
 
---
 
## 1.5 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores
 
![V3b - Proceso E2E de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3b%20-%20Proceso%20E2E%20de%20gobierno%20de%20datos.png)
 
### Qué muestra
 
De arriba hacia abajo: la cadena de valor de gobierno de datos con cinco etapas, cuatro eventos que disparan el proceso, el proceso E2E "Gobierno E2E del dato personal (de la fuente al reporte)" con nueve pasos, y los actores y roles asignados a cada paso. Cada etapa de la cadena queda sobre los pasos que la realizan. El color de cada paso indica el apoyo de la solución.
 
### Cómo se lee
 
Los pasos del proceso se encadenan con Triggering de izquierda a derecha. Hay un ciclo de mantenimiento: "Controlar cambios de estructura" vuelve a disparar "Importar metadatos técnicos". Cada línea de la franja inferior es una Assignment de un actor o rol a un paso. La leyenda de colores está en la parte inferior de la vista.
 
### Pasos del proceso y apoyo de la solución
 
| Paso | Qué hace | Apoyo de la solución | Etapa de la cadena |
|---|---|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | TI y proveedores habilitan acceso de solo lectura a S1, S3, S4 y, vía proveedor, S2 | No (lo hace TI o el proveedor) | Conocer los datos |
| P2 Importar metadatos técnicos | Trae tipo de dato y longitud desde los diccionarios de los motores | Sí | Conocer los datos |
| P3 Inventariar atributos de negocio | Consolida los atributos distintos y suma los de fuentes sin motor (hojas, carpetas) | Sí | Conocer los datos |
| P4 Describir atributos (definición, responsable, calidad y validación) | Registra metadatos de negocio por atributo | Sí | Describir los datos |
| P5 Clasificar atributos por categoría legal | Asigna categoría con criterio y justificación | Sí | Clasificar los datos |
| P6 Validar jurídicamente la clasificación | Jurídica revisa y deja constancia; la herramienta registra | Parcial | Clasificar los datos |
| P7 Publicar diccionario de datos y catálogo de términos | Integra lo técnico y lo de negocio y asocia términos a atributos | Sí | Publicar y mantener el diccionario |
| P8 Controlar cambios de estructura | Detecta cambios entre importaciones y deja evidencia | Parcial | Publicar y mantener el diccionario |
| P9 Consultar y reportar (titulares, seguridad, SIC) | Ubica datos de una persona, informa atributos sensibles y prepara el reporte | Parcial | Usar y rendir cuentas |
 
Resumen: cinco pasos con apoyo de la solución (P2, P3, P4, P5 y P7), tres con apoyo parcial (P6, P8 y P9) y uno sin apoyo (P1). El proceso completo está marcado como "Sí (transversal)".
 
### Eventos que disparan el proceso
 
| Evento | Paso que dispara | Descripción |
|---|---|---|
| Nueva fuente de datos incorporada | P1 | Se incorpora un sistema o fuente que maneja datos de personas |
| Cambio de estructura en una base de datos | P8 | Un proveedor o TI modifica tablas o columnas, hoy sin aviso formal |
| Reclamo o solicitud de un titular | P9 | Una persona consulta, corrige o pide suprimir sus datos |
| Requerimiento de la SIC | P9 | La autoridad solicita información; la obligación concreta está por verificar |
 
### Actores y roles por paso
 
| Actor o rol | Tipo | Pasos asignados |
|---|---|---|
| Gerente general | Actor | Proceso E2E completo (aprueba políticas y asigna recursos) |
| Coordinador de TI | Actor | P1, P2, P3, P8 |
| Proveedor del CRM (S2) | Actor externo | P1 |
| Jefa de administración de arrendamientos | Actor | P3 |
| Director comercial | Actor | P3 |
| Responsable de dato de área | Rol por designar | P4 |
| Oficial de protección de datos | Rol por designar | P5, P7, P9 |
| Abogada interna | Actor | P5, P6 |
| Abogado externo | Actor | P6 |
| Servicio al cliente | Actor | P9 |
 
### Justificación
 
Esta vista es el punto de partida de la Fase 2: el proceso E2E es el que se descompone después en servicios por capas. Identificar el apoyo de la solución paso por paso evita sobreprometer: P1 es una tarea de TI y del proveedor, y P6, P8 y P9 dependen de decisiones o ejecuciones humanas, por lo que la herramienta solo registra o prepara.
 
---
 
## 1.6 V3C: proceso E2E y capacidades que realiza
 
![V3c - Proceso E2E y capacidades](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3c%20-%20Proceso%20E2E%20y%20capacidades%20que%20realiza.png)
 
### Qué muestra
 
Los nueve pasos del proceso E2E arriba y, abajo, las 16 capacidades de la V2 que esos pasos realizan, unidas con 17 relaciones Realization. También conserva la secuencia de Triggering y el ciclo de mantenimiento entre P8 y P2. La vista tiene 26 conexiones.
 
### Cómo se lee
 
Una línea de Realization desde un paso hacia una capacidad significa que el paso es la forma concreta en que la organización ejerce esa capacidad. Un paso puede realizar varias capacidades, y se lee de arriba hacia abajo. Los pasos usan la leyenda de apoyo de la solución (naranja con apoyo, naranja claro apoyo parcial, gris sin apoyo) y las capacidades usan la de impacto de la V2 (naranja directo, naranja claro parcial, crema indirecto).
 
### Trazabilidad paso a capacidad
 
| Paso del proceso | Capacidades que realiza |
|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | Gestión de metadatos técnicos; Administración de accesos e identidades |
| P2 Importar metadatos técnicos | Gestión de metadatos técnicos |
| P3 Inventariar atributos de negocio | Inventario de atributos de negocio |
| P4 Describir atributos | Gestión de metadatos de negocio; Gestión de responsables de datos; Definición de políticas y reglas de calidad y validación |
| P5 Clasificar atributos por categoría legal | Clasificación de atributos por categoría legal |
| P6 Validar jurídicamente la clasificación | Validación jurídica de la clasificación; Resolución de conflictos y decisiones sobre datos |
| P7 Publicar diccionario de datos y catálogo de términos | Gestión del diccionario de datos; Gestión del catálogo de términos de negocio |
| P8 Controlar cambios de estructura | Gestión de cambios de estructura de datos; Gestión de trazabilidad y evidencia de decisiones |
| P9 Consultar y reportar (titulares, seguridad, SIC) | Atención de derechos de los titulares; Reporte regulatorio ante la SIC; Gestión de la seguridad de la información |
 
### Qué permite concluir
 
- Los pasos P2, P3, P4, P5 y P7 realizan capacidades con impacto directo, y son el núcleo de la solución.
- P6 realiza dos capacidades de impacto parcial; P8 realiza una de impacto parcial (cambios de estructura) y una directa (trazabilidad y evidencia de decisiones); P9 realiza una de impacto parcial (reporte ante la SIC) y dos indirectas (derechos de los titulares y seguridad de la información). Esto es coherente con el apoyo parcial de estos tres pasos en la V3b.
- P1 realiza una capacidad de impacto directo (metadatos técnicos), pero el paso lo ejecuta TI o el proveedor, y una capacidad de impacto indirecto (accesos e identidades), por eso se marca sin apoyo de la solución.
- Las capacidades fuera de alcance de la V2, como Medición y monitoreo de la calidad o Gestión de Datos Maestros, no tienen un paso que las realice: es la forma de mostrar que son brechas y no parte de la solución.

---

# 2. Descomposición de servicios del proceso E2E

La V4 responde seis preguntas, una por vista:
 
| Vista | Pregunta que responde |
|---|---|
| V4a | De dónde salen los servicios |
| V4b | Cómo se descomponen y cuáles se implementan |
| V4c | Quién los realiza y qué objetos del negocio gestionan |
| V4d | Con qué sistemas externos se interopera, qué se intercambia y en qué dirección |
| V4e | Cuál es el contrato de cada servicio de actividad |
| V4f | Cuál es el contrato de cada servicio de entidad, utilidad e interoperabilidad |

## 2.1 V4a: del proceso E2E a los servicios de actividad

![4A](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4a%20-%20Del%20proceso%20E2E%20a%20los%20servicios.png)

### Qué muestra
 
Los nueve pasos del proceso E2E "Gobierno E2E del dato personal" (P1 a P9), con flujo secuencial entre ellos, y los 14 servicios de actividad (capa 3) que realizan esos pasos mediante relaciones Realization.
 
### Cómo se lee
 
El proceso va de izquierda a derecha, desde la fuente de datos hasta el reporte. Cada línea punteada que baja desde un paso es una relación Realization hacia un servicio de actividad. Un servicio de actividad es la forma en que el negocio ve lo que hace un paso: expone una capacidad con un consumidor y unas reglas propias.
 
Cada servicio queda ligado a una capacidad del mapa de la V2, de modo que la descomposición se puede rastrear desde la estrategia hasta el servicio.
 
### Trazabilidad paso, servicio y capacidad
 
| Paso del proceso | Servicios de actividad | Capacidad de la V2 que soportan |
|---|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | gestión del acceso a metadatos técnicos | Gestión de metadatos técnicos |
| P2 Importar metadatos técnicos | importación de metadatos técnicos | Gestión de metadatos técnicos |
| P3 Inventariar atributos de negocio | inventario de atributos de negocio | Inventario de atributos de negocio |
| P4 Describir atributos (definición, responsable, calidad y validación) | registro de metadatos de negocio; asignación de responsables de datos | Gestión de metadatos de negocio; Gestión de responsables de datos |
| P5 Clasificar atributos por categoría legal | clasificación de atributos | Clasificación de atributos por categoría legal |
| P6 Validar jurídicamente la clasificación | validación jurídica de la clasificación | Validación jurídica de la clasificación |
| P7 Publicar diccionario de datos y catálogo de términos | publicación del diccionario de datos; gestión del catálogo de términos de negocio | Gestión del diccionario de datos; Gestión del catálogo de términos de negocio |
| P8 Controlar cambios de estructura | control de cambios de estructura | Gestión de cambios de estructura de datos |
| P9 Consultar y reportar (titulares, seguridad, SIC) | ubicación de datos personales; información para seguridad de la información; información para el reporte regulatorio; seguimiento de completitud de atributos | Atención de derechos de los titulares; Gestión de la seguridad de la información; Reporte regulatorio ante la SIC; Gobierno de Datos |
 
### Criterio de partición
 
Un paso se parte en varios servicios cuando atiende capacidades distintas, porque cada servicio resultante tiene consumidores y reglas diferentes:
 
- P4 separa metadatos de negocio (definición, calidad, expresión regular) de responsables de datos (asignación y reasignación con histórico).
- P7 separa diccionario (consulta integrada de solo lectura) de catálogo de términos (gestión de significados y conflictos).
- P9 separa cuatro consumidores: el titular que reclama, seguridad de la información, el reporte regulatorio y la gerencia que mide completitud.
Si estos servicios se agruparan en uno solo, un cambio en las reglas de uno obligaría a modificar los demás. La separación reduce el acoplamiento y mantiene cada servicio cohesivo alrededor de una sola capacidad.
 
---

## 2.2 V4b: descomposición en cuatro capas de servicio
 
![4B](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4b%20-%20Descomposici%C3%B3n%20en%20cuatro%20capas%20de%20servicio.png)
 
### Qué muestra
 
Las cuatro capas de servicio, de arriba hacia abajo, más el bloque de servicios excluidos. La capa 1 se compone de la capa 2 y la capa 2 de la capa 3 mediante Composition. Cada servicio de capa 4 queda bajo el servicio de actividad que más lo usa mediante Serving. La vista dibuja solo el uso principal; el uso completo está en la matriz de esta sección y en el modelo como relaciones Serving adicionales.
 
### Las cuatro capas
 
| Capa | Qué es | Cantidad | Se implementa |
|---|---|---|---|
| 1. Servicio E2E | El proceso E2E expuesto como un solo servicio al negocio | 1 | No, agrupa |
| 2. Servicios de proceso | Uno por etapa de la cadena de valor de gobierno de datos | 5 | No, agrupan |
| 3. Servicios de actividad | Uno por paso o capacidad del proceso | 14 | Sí, como orquestación de la capa 4 |
| 4. Servicios de entidad y utilidad | Una entidad del dominio o una utilidad transversal | 13 | Sí. Es el tamaño sobre el que se construye la aplicación |
 
### Composición completa
 
- Servicio de gobierno del dato personal (capa 1)
  - Servicio de conocimiento de los datos (capa 2): gestión del acceso a metadatos técnicos; importación de metadatos técnicos; inventario de atributos de negocio
  - Servicio de descripción de los datos: registro de metadatos de negocio; asignación de responsables de datos
  - Servicio de clasificación de los datos: clasificación de atributos; validación jurídica de la clasificación
  - Servicio de publicación y mantenimiento del diccionario: publicación del diccionario de datos; gestión del catálogo de términos de negocio; control de cambios de estructura
  - Servicio de uso y rendición de cuentas: ubicación de datos personales; información para seguridad de la información; información para el reporte regulatorio; seguimiento de completitud de atributos

### Criterio de tamaño adecuado para un servicio de capa 4
 
Un servicio de capa 4 debe cumplir estas condiciones:
 
1. Gestiona una sola entidad del dominio o una sola utilidad.
2. Tiene entre 3 y 6 operaciones.
3. No depende de otro servicio de su misma capa.
4. Se explica con una frase del negocio.
Reglas de ajuste: si dos entidades cambian siempre juntas se unen en un servicio; si una entidad tiene dos dueños distintos se divide.
 
### Por qué la capa 4 se define por entidades
 
Las entidades son lo más estable del dominio: los pasos del proceso cambian, pero un atributo, una clasificación o un término siguen existiendo. Por eso la aplicación se construye sobre la capa 4 y la capa 3 solo orquesta llamadas a la capa 4. Las tres utilidades (bitácora, notificación y control de acceso) son transversales porque casi todos los servicios las usan. La bitácora es, además, la evidencia de decisiones que pide la gerencia.
 
Servicios de capa 4:
 
| Código | Servicio | Tipo |
|---|---|---|
| 4.1 | atributo de negocio | Entidad |
| 4.2 | metadato técnico | Entidad |
| 4.3 | fuente de datos | Entidad |
| 4.4 | metadato de negocio | Entidad |
| 4.5 | responsable de dato | Entidad |
| 4.6 | clasificación de atributo | Entidad |
| 4.7 | término de negocio | Entidad |
| 4.8 | diccionario de datos | Entidad |
| 4.9 | cambio de estructura | Entidad |
| 4.10 | bitácora y evidencia de decisiones | Utilidad |
| 4.11 | notificación | Utilidad |
| 4.12 | control de acceso por rol | Utilidad |
| 4.13 | informes y exportación | Entidad |
 
### Matriz de uso: capa 3 por capa 4
 
Una "X" indica que el servicio de actividad (fila) usa el servicio de capa 4 (columna).
 
| Capa 3 \ Capa 4 | 4.1 | 4.2 | 4.3 | 4.4 | 4.5 | 4.6 | 4.7 | 4.8 | 4.9 | 4.10 | 4.11 | 4.12 | 4.13 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| gestión del acceso a metadatos técnicos | | | X | | | | | | | X | | X | |
| importación de metadatos técnicos | | X | X | | | | | | X | X | | | |
| inventario de atributos de negocio | X | | X | | | | | | | X | | | |
| registro de metadatos de negocio | X | | | X | | | | | | X | X | | |
| asignación de responsables de datos | X | | | | X | | | | | X | | | |
| clasificación de atributos | X | | | | | X | | | | X | | | |
| validación jurídica de la clasificación | | | | | | X | | | | X | X | | |
| publicación del diccionario de datos | X | X | | X | | X | | X | | | | | |
| gestión del catálogo de términos de negocio | X | | | | | | X | | | X | | | |
| control de cambios de estructura | | X | | | | | | | X | X | X | | |
| ubicación de datos personales | | | X | | | X | | X | | | | | |
| información para seguridad de la información | | | | | X | X | | X | X | | | | |
| información para el reporte regulatorio | | | X | | | X | | X | | | | | X |
| seguimiento de completitud de atributos | X | | | X | X | X | | | | | X | | |
 
### Servicios excluidos
 
Los 16 servicios en gris de la vista son decisiones de alcance, cada una con su justificación:
 
| Código | Servicio excluido | Justificación |
|---|---|---|
| Z1 | Descubrimiento automático de datos personales (lectura de datos) | El negocio prefiere que la herramienta no lea datos de personas para no abrir otro punto de exposición de cédulas e ingresos (Bloque 8). La clasificación es manual. |
| Z2 | Publicación de definiciones y clasificación hacia los sistemas fuente | Nadie lo pide, no hay forma de recibirlo y los proveedores cobrarían por ello (Bloque 8). |
| Z3 | Modificación de estructuras o datos en los sistemas fuente | El negocio no espera que la herramienta cambie las bases de datos. |
| Z4 | Medición y monitoreo de la calidad de los datos | Exige leer datos; solo se pide definir políticas y expresiones regulares. Es una brecha frente a la expectativa de la gerencia. |
| Z5 | Depuración y deduplicación de datos | Fuera de alcance; exige datos personales. El 8 % de propietarios duplicados queda sin atender. |
| Z6 | Gestión de datos maestros | Fuera de alcance. Resolvería la duplicidad, pero es otro proyecto. |
| Z7 | Gestión de autorizaciones de titulares | Fuera de los cinco puntos del alcance; hoy son formatos dispersos. Candidato a otra solución. |
| Z8 | Trámite de reclamos de titulares | La solución solo informa dónde están los datos. El trámite sigue en Jurídica y Servicio al cliente. |
| Z9 | Gestión de incidentes con datos personales | Fuera de alcance; no hay procedimiento definido. |
| Z10 | Gestión de encargados del tratamiento (proveedores) | Fuera de alcance; las cláusulas de datos con proveedores siguen pendientes con la gerente. |
| Z11 | Retención y supresión de datos | Fuera de alcance; consumirá el diccionario cuando exista. |
| Z12 | Transmisión del reporte a la SIC | Formato, canal y plazos por verificar, y la obligación misma es incierta. Se exporta el informe y Jurídica lo presenta. |
| Z13 | Linaje de datos | No fue solicitado y las hojas y carpetas no tienen catálogo técnico que lo permita. |
| Z14 | Aprobación de políticas de datos | Decide la gerente fuera de la herramienta; el diccionario solo referencia las vigentes. |
| Z15 | Directorio e identidad corporativa (SSO) | La empresa no tiene uno; los roles se manejan localmente en el servicio de control de acceso. |
| Z16 | Integración con portales, aseguradora, banco, notarías y centrales de riesgo | Reciben datos del negocio pero no intercambian información con la herramienta. Extensión futura: registrarlos como destinatarios del atributo. |
 
---

## 2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos
 
![4C](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4c%20-%20Servicios%20de%20entidad%20y%20utilidad.png)
 
### Qué muestra
 
Para cada servicio de capa 4: los roles y actores asignados (Assignment) a la función de negocio que lo realiza (Realization) y los objetos pasivos que gestiona (Access). En la parte inferior de la vista está el modelo de objetos pasivos.
 
### Cómo se lee
 
La cadena de elementos para cada servicio es:
 
Rol o actor, Assignment, Función de negocio, Realization, Servicio de negocio, Access, Objeto pasivo.
 
Se usa una función por servicio para dejar claro quién responde por cada entidad.
 
### Asignaciones
 
| Servicio | Función que lo realiza | Roles y actores asignados | Objetos pasivos |
|---|---|---|---|
| atributo de negocio | Administración de atributos de negocio | Administrador del diccionario de datos | Atributo de negocio |
| metadato técnico | Administración de metadatos técnicos | Administrador del diccionario de datos; Coordinador de TI | Metadato técnico |
| fuente de datos | Administración de fuentes de datos y accesos | Administrador del diccionario de datos; Coordinador de TI | Fuente de datos; Autorización de acceso a metadatos |
| metadato de negocio | Administración de metadatos de negocio | Responsable de dato de área | Metadato de negocio |
| responsable de dato | Administración de responsables de datos | Administrador del diccionario de datos; Gerente general | Responsabilidad sobre el dato |
| clasificación de atributo | Administración de la clasificación de datos | Oficial de protección de datos; Abogada interna | Clasificación del atributo |
| término de negocio | Administración del catálogo de términos | Responsable de dato de área; Administrador del diccionario de datos | Término de negocio |
| diccionario de datos | Mantenimiento del diccionario integrado | Administrador del diccionario de datos | Diccionario de datos |
| cambio de estructura | Detección y registro de cambios de estructura | Coordinador de TI; Administrador del diccionario de datos | Cambio de estructura |
| bitácora y evidencia de decisiones | Conservación de evidencia de decisiones | Oficial de protección de datos | Evidencia de decisión |
| notificación | Gestión de avisos | Administrador del diccionario de datos | Aviso |
| control de acceso por rol | Administración de permisos | Administrador del diccionario de datos | Permiso de acceso |
| informes y exportación | Elaboración de informes | Oficial de protección de datos; Abogada interna | Informe regulatorio |
 
### Modelo de objetos pasivos
 
- El Atributo de negocio agrega su Metadato técnico, su Metadato de negocio, su Clasificación y su Responsabilidad.
- La Fuente de datos agrega los metadatos técnicos que se importan de ella.
- El Término de negocio se asocia a los atributos que describe.
- El Diccionario de datos agrega atributos y términos.

### Roles por designar
 
Tres de los roles no existen aún en la empresa y se modelaron como roles por designar, sin asignar personas:
 
- Oficial de protección de datos.
- Responsable de dato de área.
- Administrador del diccionario de datos.
La entrevista habla de "quien administre el diccionario" sin definirlo. Quién ocupe ese rol define los permisos del servicio de control de acceso por rol, y eso importa porque el diccionario revela dónde está la información sensible.
 
---

## 2.4 V4D: capa anticorrupción e interoperabilidad
 
![v4d](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4d%20-%20Capa%20anticorrupci%C3%B3n.png)

 
### Qué muestra
 
La parte superior (ENTRADA) muestra los servicios externos que alimentan la solución. La parte inferior (SALIDA) muestra los servicios de la solución que consumen el oficial, seguridad y Jurídica. Los servicios en naranja son los adaptadores de la capa anticorrupción. Los servicios en lila son los servicios externos.
 
La dirección se describe desde la solución: entrada es información que llega a la solución; salida es información que la solución entrega.
 
### Cómo se lee
 
En la entrada, el recorrido es: actor externo, servicio externo, adaptador, servicio de la solución. En la salida, el recorrido es el inverso: servicio de la solución, adaptador, consumidor.
 
### Qué es la capa anticorrupción
 
Es un patrón de DDD (Anti-Corruption Layer). Los sistemas legados, el CRM del proveedor y la SIC tienen sus propios modelos y formatos. El adaptador traduce esos modelos al modelo interno, de modo que un cambio de motor, de proveedor o del formato del reporte afecta solo al adaptador y no al dominio.
 
### Inventario de interoperabilidades
 
| # | Servicio externo | Tipo | Información | Dirección | Adaptador | Si no está disponible o no es válida |
|---|---|---|---|---|---|---|
| 1 | S1 Administración de arrendamientos (SQL Server) | Sistema legado | Estructura técnica: tablas, columnas, tipo, longitud, obligatoriedad. Autoriza la jefa de administración; ejecuta TI | Entrada | A1 | Se reintenta; se usa la última versión conocida y se anota su fecha |
| 2 | S3 Contable (SQL Server) | Sistema legado | Misma estructura. Autoriza el contador; ejecuta TI | Entrada | A1 | Igual |
| 3 | S4 Sitio web (MySQL) | Sistema legado | Misma estructura. Autoriza el analista de mercadeo con la gerente; ejecuta TI | Entrada | A1 | Igual |
| 4 | S2 CRM comercial (PostgreSQL) | Sistema de proveedor | Misma estructura, entregada por el proveedor. Autoriza el director comercial con la gerente | Entrada | A2 | El negocio acepta demoras de días; la fuente se muestra desactualizada |
| 5 | Proveedores de S1 a S4 | Proveedor | Aviso de cambios de estructura | Entrada | A3 | No hay aviso garantizado; la detección por diferencias entre importaciones lo compensa |
| 6 | Hojas, carpetas, correo y WhatsApp | Fuente no estructurada | Inventario manual: ubicación, tipo de dato personal, responsable | Entrada (manual) | A4 | Queda como "área sin cubrir" |
| 7 | Áreas de negocio y responsables de dato | Proceso interno | Definiciones, políticas de calidad, expresiones regulares y términos | Entrada (por pantalla) | Sin adaptador | Atributo incompleto, visible al oficial |
| 8 | Jurídica (abogada interna y abogado externo) | Proceso interno | Validación de la clasificación y su justificación | Entrada (por pantalla) | Sin adaptador | Clasificación "en revisión" con la opinión de cada parte |
| 9 | Oficial de protección de datos | Proceso interno | Atributos personales, categoría, ubicación, responsable, pendientes y cambios recientes | Salida | A5 | Se indica qué falta |
| 10 | Seguridad de la información (hoy, el coordinador de TI) | Proceso interno | Atributos sensibles y privados, sistemas de mayor riesgo, cambios que los afecten | Salida | A6 | Se indica qué falta |
| 11 | Superintendencia de Industria y Comercio (vía Jurídica) | Entidad regulatoria | Informe: bases, finalidad, responsable y encargado, tipos de datos, clasificación, medidas de seguridad, titulares aproximados. Formato por verificar | Salida (la presenta Jurídica a mano) | A7 | Información no validada: no se presenta como definitiva |
| 12 | Correo electrónico | Canal | Avisos por rol, sin datos de personas | Salida | A8 | El aviso queda pendiente en la aplicación |
| 13 | Portales, correo masivo, aseguradora, banco, notarías, centrales de riesgo | Terceros receptores de datos | Reciben datos del negocio, no de la herramienta | Sin intercambio | No aplica | Excluido (Z16); extensión futura: registrarlos como destinatarios del atributo |
| 14 | Dispositivos | No aplica | Ninguno identificado en la entrevista (la huella de la cédula es un dato, no un dispositivo) | No aplica | No aplica | No aplica |
 
### Adaptadores
 
| Adaptador | Dirección | Sirve a | Qué traduce |
|---|---|---|---|
| A1 adaptación de metadatos técnicos de motores relacionales | Entrada | importación de metadatos técnicos | Traduce el catálogo de SQL Server y MySQL (S1, S3, S4) al modelo interno de metadato técnico y normaliza tipos entre motores |
| A2 adaptación de metadatos técnicos del CRM (S2) | Entrada | importación de metadatos técnicos | Traduce lo que entregue el proveedor del CRM (formato por acordar) al modelo interno; tolera demoras de días |
| A3 recepción de avisos de cambio de los proveedores | Entrada | control de cambios de estructura | Recibe y registra los avisos de cambio de estructura; no se confía en que lleguen |
| A4 carga del inventario de fuentes no estructuradas | Entrada | inventario de atributos de negocio | Recibe el inventario manual de hojas, carpetas, correo y WhatsApp, que no tienen catálogo técnico |
| A5 entrega de información al oficial de protección de datos | Salida | ubicación de datos personales | Presenta atributos personales, categoría, ubicación, responsable y faltantes en la vista que usa el oficial |
| A6 entrega de información a seguridad de la información | Salida | información para seguridad de la información | Presenta atributos sensibles y privados, sistemas de riesgo y cambios de riesgo en la vista de seguridad |
| A7 generación del informe para la SIC | Salida | información para el reporte regulatorio | Da forma de informe a la información regulatoria; el formato exigido está por verificar |
| A8 notificación por correo electrónico | Salida | notificación | Convierte un aviso interno en un correo sin datos de personas |
 
### Restricciones de diseño
 
- Todos los intercambios de entrada son de solo estructura: la herramienta no lee datos de personas, como pidieron la gerente y la abogada.
- Las áreas de negocio y Jurídica interactúan por pantalla con la propia aplicación, por eso no necesitan adaptador.
- La SIC no recibe nada directamente de la solución: se exporta el informe y Jurídica lo presenta de forma manual.
- Ante una fuente caída se trabaja con la última versión conocida y se muestra su fecha, nunca se bloquea el diccionario.

---

## 2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)
 
![V4E](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4e%20-%20Contract%20First%20contratos%20de%20los%20servicios%20capa%203.png)
 
### Qué muestra
 
Cada servicio de capa 3, su contrato (elemento Contract de ArchiMate, relación de especificación) y los objetos pasivos que el contrato agrega (Aggregation).
 
### Qué significa Contract First
 
El contrato se diseña antes que la aplicación. Fija lo que el consumidor puede pedir y lo que el servicio promete. Cada contrato define cinco campos, que están guardados como propiedades del elemento Contract en Archi:
 
| Campo | Contenido |
|---|---|
| Operaciones | Firmas de las operaciones que expone el servicio |
| Entrada | Datos que debe recibir |
| Salida | Resultado que entrega |
| Reglas de negocio | Condiciones que el servicio garantiza o exige |
| Excepciones | Qué pasa cuando falta información o algo falla |
 
Las capas 1 y 2 no tienen contrato propio porque solo agrupan.
 
### Regla común de excepciones
 
Los contratos de capa 3 son los que ven los usuarios del negocio, por eso sus excepciones siguen la regla de la gerente: cuando la información falta o es dudosa, el sistema indica qué falta y no presenta un dato dudoso como correcto.
 
### Ejemplo completo: 3.6 Servicio de clasificación de atributos
 
| Campo | Contenido |
|---|---|
| Operaciones | proponerClasificacion(atributo, categoría, criterio, justificación); marcarEnRevision(atributo, opinión); consultarPendientes() |
| Entrada | atributo, categoría, criterio, justificación, fuente normativa |
| Salida | clasificación en estado propuesta o en revisión |
| Reglas de negocio | Categorías según el marco normativo (por verificar). Si hay discusión queda "en revisión" con la opinión de cada parte |
| Excepciones | Sin justificación no se guarda |
 
### Resumen de los 14 contratos de capa 3
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| 3.1 | gestión del acceso a metadatos técnicos | solicitarAcceso(fuente); registrarAutorizacion(fuente, autorizador); registrarCuentaSoloLectura(fuente); revocarAcceso(fuente) | Solo lectura, cuenta propia. Sin autorización no se habilita la importación |
| 3.2 | importación de metadatos técnicos | importarEstructura(fuente); reintentarImportacion(fuente); consultarEstadoImportacion(fuente) | Solo estructura. Fuente no disponible: se reintenta y se usa la última versión conocida |
| 3.3 | inventario de atributos de negocio | inventariarAtributos(fuente); registrarAtributoManual(datos); vincularColumna(atributo, columna) | Columnas equivalentes se consolidan en un atributo. Fuente sin inventario queda "sin cubrir" |
| 3.4 | registro de metadatos de negocio | registrarMetadatosNegocio(atributo, definición, calidad, regex); solicitarCompletar(atributo) | La regex debe ser válida y no se ejecuta contra datos. Dato faltante: atributo incompleto |
| 3.5 | asignación de responsables de datos | asignarResponsable(atributo, responsable); reasignarResponsable(atributo, responsable); listarSinResponsable() | Todo atributo con datos personales debe tener responsable. La reasignación conserva histórico |
| 3.6 | clasificación de atributos | proponerClasificacion; marcarEnRevision; consultarPendientes | Sin justificación no se guarda |
| 3.7 | validación jurídica de la clasificación | validar(clasificación, justificación); objetar(clasificación, motivo); consultarPendientes() | La valida solo Jurídica o el oficial. Sin validar no se presenta como definitiva |
| 3.8 | publicación del diccionario de datos | publicarVersion(); consultarVersionPublicada(); compararVersiones(a, b) | Publica todo, pero marca atributos incompletos y la antigüedad de la información técnica |
| 3.9 | gestión del catálogo de términos de negocio | proponerTermino(término, significado); aprobarTermino(término); asociarAtributos(término, atributos); resolverConflicto(término) | Dos significados se registran ambos y se marca el conflicto. Término sin atributos: advertencia |
| 3.10 | control de cambios de estructura | detectarCambios(fuente); notificarCambio(cambio); registrarImpacto(cambio) | Un cambio sobre un atributo sensible se marca de riesgo y no altera la clasificación por sí solo |
| 3.11 | ubicación de datos personales | listarAtributosPersonales(filtro); ubicarAtributo(atributo); sistemasConDatosDeTipoDeTitular(tipo) | Responde por atributo y tipo de titular, no por persona |
| 3.12 | información para seguridad de la información | listarAtributosSensibles(); listarSistemasDeRiesgo(); listarCambiosDeRiesgo(); listarSinResponsable() | Solo atributos sensibles y privados, sin datos de personas |
| 3.13 | información para el reporte regulatorio | prepararInforme(parámetros); validarCompletitud(informe); exportarInforme(informe, formato) | No se transmite: lo presenta Jurídica. Información no validada no se presenta como definitiva |
| 3.14 | seguimiento de completitud de atributos | calcularCobertura(); listarIncompletos(); listarSinClasificar() | El cálculo es sobre atributos, no sobre datos. Sin atributos inventariados: cobertura no calculable |
 
---

## 2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad
 
![V4F](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4f%20-%20Contract%20First%20contratos%20entidad%2C%20utilidad%20e%20interoperabilidad.png)
 
### Qué muestra
 
Los contratos de los 13 servicios de capa 4 y de los 8 adaptadores de la capa anticorrupción, con los objetos pasivos que agregan. Los servicios de entidad y utilidad se muestran en amarillo claro y los adaptadores en naranja.
 
### Por qué son el nivel de construcción
 
Estos contratos son los que sirven de base a la capa de aplicaciones: cada uno corresponde a una entidad, una utilidad o un adaptador. Son pequeños e independientes del proceso, por eso se reutilizan desde varios servicios de actividad. Los de los adaptadores dejan por escrito qué formato se espera de cada sistema externo y qué ocurre si no llega. Las operaciones están escritas como firmas del negocio y se refinan al pasar a la capa de aplicaciones.
 
### Ejemplo completo de entidad: 4.6 Servicio de clasificación de atributo
 
| Campo | Contenido |
|---|---|
| Operaciones | proponer(atributo, categoría, criterio, justificación); registrarValidacion(id, decisión); marcarEnRevision(id, opinión); consultar(atributo); listarPendientes() |
| Entrada | atributo, categoría (pública, semiprivada, privada, sensible), criterio, justificación, fuente normativa, autor |
| Salida | clasificación con estado (propuesta, en revisión, validada), versión y fecha |
| Reglas de negocio | La valida solo Jurídica u oficial. Reclasificar crea versión |
| Excepciones | Sin justificación no se guarda; sin validar no es definitiva |
 
### Ejemplo completo de adaptador: A1 Servicio de adaptación de metadatos técnicos de motores relacionales
 
| Campo | Contenido |
|---|---|
| Operaciones | leerCatalogo(motor, conexión); traducirAModeloInterno(catálogo) |
| Entrada | Catálogo del sistema del motor: tablas, columnas, tipo, longitud, obligatoriedad, relaciones |
| Salida | Metadatos técnicos en el modelo interno, con tipos normalizados |
| Reglas de negocio | Solo el catálogo del sistema, nunca tablas de negocio. Cuenta propia de solo lectura |
| Excepciones | Fallo de conexión: se reintenta y la fuente queda "desactualizada" |
 
### Resumen de los contratos de capa 4
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| 4.1 | atributo de negocio | crearAtributo(datos); consultarAtributo(id); modificarAtributo(id, datos); listarAtributos(filtro); obtenerVersiones(id) | Un atributo puede mapearse a varias columnas. Cada cambio crea versión. Es "incompleto" si falta definición, responsable o clasificación |
| 4.2 | metadato técnico | registrarEstructura(fuente, versión, columnas); consultarMetadatoTecnico(atributo); listarVersiones(fuente) | Solo estructura. Se conserva la versión anterior y se muestra la fecha |
| 4.3 | fuente de datos | registrarFuente(datos); consultarFuente(id); registrarAutorizacion(fuente, autorizador); listarFuentes(filtro) | Toda fuente tiene autorizador y constancia de acceso. La no inventariada es "área sin cubrir" |
| 4.4 | metadato de negocio | registrarMetadatoNegocio(atributo, datos); consultar(atributo); modificar(atributo, datos); validarExpresion(regex) | Definición obligatoria. La regex se valida sintácticamente y no se ejecuta contra datos |
| 4.5 | responsable de dato | asignar(atributo, responsable); reasignar(atributo, responsable); consultar(atributo); listarSinResponsable() | Todo atributo con datos personales requiere responsable. Sin responsable: alerta al oficial |
| 4.6 | clasificación de atributo | proponer; registrarValidacion; marcarEnRevision; consultar; listarPendientes | Ver ejemplo completo arriba |
| 4.7 | término de negocio | crearTermino(datos); modificarTermino(id, datos); asociarAtributo(término, atributo); desasociarAtributo(término, atributo); marcarConflicto(término); consultar(término) | Dos significados se registran ambos y se marca el conflicto |
| 4.8 | diccionario de datos | consultarDiccionario(filtros); obtenerFichaAtributo(id); listarIncompletos(); buscarPorTermino(término) | Solo lectura. Siempre indica qué falta y qué tan antigua es la información técnica |
| 4.9 | cambio de estructura | registrarDiferencias(fuente, versiónA, versiónB); consultarCambios(fuente, rango); marcarRevisado(cambio) | Un cambio sobre un atributo sensible se marca de riesgo. No modifica clasificaciones |
| 4.10 | bitácora y evidencia de decisiones | registrarEvento(actor, acción, objeto, antes, después); consultarEventos(filtros); exportarEvidencia(filtros) | Evento inmutable. Si no se puede registrar, la operación de origen no se confirma |
| 4.11 | notificación | programarAviso(tipo, rol, referencia); listarAvisos(rol); marcarAtendido(aviso) | Los avisos van por rol y nunca incluyen datos de personas |
| 4.12 | control de acceso por rol | asignarRol(usuario, rol); verificarPermiso(usuario, operación); listarPermisos(rol) | Roles: administrador, responsable de dato, oficial, jurídica, TI, consulta. Sin permiso: se deniega y se registra en la bitácora |
| 4.13 | informes y exportación | generarInforme(tipo, parámetros); exportar(informe, formato) | Marca qué falta o no está validado. No contiene datos de personas |
 
### Resumen de los contratos de adaptadores
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| A1 | metadatos técnicos de motores relacionales | leerCatalogo(motor, conexión); traducirAModeloInterno(catálogo) | Ver ejemplo completo arriba |
| A2 | metadatos técnicos del CRM (S2) | recibirEntregaEstructura(entrega); traducirAModeloInterno(entrega) | La empresa no tiene credenciales propias; se acepta demora de días. Sin entrega: se conserva la última versión con aviso |
| A3 | avisos de cambio de los proveedores | recibirAviso(aviso); registrarAviso(aviso, fuente) | No se confía en que el aviso llegue. Aviso sin fuente identificable: queda pendiente de clasificar |
| A4 | inventario de fuentes no estructuradas | validarPlantilla(archivo); cargarInventario(archivo) | Carga manual guiada; no se cargan archivos con datos de personas. Plantilla inválida: se rechaza indicando las filas |
| A5 | información al oficial de protección de datos | consultarAtributosPersonales(filtro); consultarPendientes(); consultarCambiosRecientes(rango) | Solo lectura y sin datos de personas. Muestra qué falta |
| A6 | información a seguridad de la información | obtenerAtributosSensibles(); obtenerSistemasDeRiesgo(); obtenerCambiosDeRiesgo() | Solo atributos sensibles y privados |
| A7 | informe para la SIC | generarInformeRegulatorio(parámetros); exportar(informe, formato) | Formato por verificar. La presenta Jurídica de forma manual |
| A8 | notificación por correo electrónico | enviarAviso(destinatario, plantilla, referencia) | El cuerpo no incluye datos de personas. Servidor no disponible: el aviso queda pendiente |
 
Total: 14 contratos de actividad, 13 de entidad y utilidad y 8 de adaptadores, es decir, 35 contratos. Son un primer borrador de operaciones y reglas que se refina en la capa de aplicaciones.
 
---ón, y objetos del negocio](#11-v1-motivación-de-la-solución-de-la-necesidad-a-la-meta)

  - [1.2 V2: mapa de capacidades](#12-v2-mapa-de-capacidades)

  - [1.3 V2B: dependencias de gobierno de datos, recursos y cursos de acción](#13-v2b-dependencias-de-gobierno-de-datos-recursos-y-cursos-de-acción)

  - [1.4 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan](#14-v3a-cadena-de-valor-del-negocio-eventos-y-capacidades-que-la-habilitan)
  
  - [1.5 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores](#15-v3b-proceso-e2e-de-gobierno-de-datos-cadena-de-valor-eventos-y-actores)
  
  - [1.6 V3C: proceso E2E y capacidades que realiza](#16-v3c-proceso-e2e-y-capacidades-que-realiza)
    
- [2. Descomposición de servicios del proceso E2E](#2-descomposición-de-servicios-del-proceso-e2e)
  - [2.1 V4a: del proceso E2E a los servicios de actividad](#21-v4a-del-proceso-e2e-a-los-servicios-de-actividad)
  
  - [2.2 V4b: descomposición en cuatro capas de servicio](#22-v4b-descomposición-en-cuatro-capas-de-servicio)
   
  - [2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos](#23-v4c-servicios-de-entidad-y-utilidad-roles-funciones-y-objetos-pasivos)

  - [2.4 V4D: capa anticorrupción e interoperabilidad](#24-v4d-capa-anticorrupción-e-interoperabilidad)
   
  - [2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)](#25-v4e-contract-first-contratos-de-los-servicios-de-actividad-capa-3)

  - [2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad](#26-v4f-contract-first-contratos-de-entidad-utilidad-e-interoperabilidad)

# 1. Entendimiento del negocio y mapa de capacidades 

La Fase 1 responde seis preguntas, que se reparten entre las vistas así:
 
| Vista | Pregunta que responde |
|---|---|
| V1 | Por qué se necesita la aplicación: quién la necesita, qué problemas la justifican, qué metas persigue y qué requisitos, principios y restricciones se derivan |
| V2 | Qué es capaz de hacer la organización y en cuáles capacidades impacta la solución |
| V2b | Cómo dependen entre sí las capacidades de datos y qué recursos y cursos de acción las sostienen |
| V3a | Cuál es la cadena de valor del negocio, qué eventos la disparan y qué capacidades habilitan cada etapa |
| V3b | Cuál es el proceso E2E donde opera la aplicación, quién interviene y qué pasos apoya la solución |
| V3c | Qué capacidades realiza cada paso del proceso E2E |
 
Principio de modelado: una capacidad describe lo que la organización es capaz de hacer, no un proceso ni una actividad operativa. Por eso los nombres de las capacidades son sustantivos de habilidad ("Gestión de metadatos técnicos") y los pasos del proceso son verbos ("Importar metadatos técnicos").
 
Elementos de ArchiMate que se usan:
 
| Elemento | Capa | Uso en este modelo |
|---|---|---|
| Capability | Estrategia | Capacidades en tres niveles (Nivel 1, 2 y 3) |
| Value Stream | Estrategia | Etapas de la cadena de valor del negocio y de la cadena de gobierno de datos |
| Resource | Estrategia | Recursos que habilitan las capacidades de datos |
| Course of Action | Estrategia | Líneas de acción propuestas a partir de las metas de la entrevista |
| Stakeholder, Driver, Assessment, Goal, Outcome, Principle, Requirement y Constraint | Motivación | Quién necesita la aplicación y por qué: de la necesidad a la meta, los requisitos y las restricciones (V1) |
| Business Process | Negocio | Pasos del proceso E2E |
| Business Event | Negocio | Hechos que disparan una etapa o un paso |
| Business Actor y Business Role | Negocio | Quién ejecuta o responde por cada paso |
| Grouping | Otros | Franjas de la V2 |
 
Relaciones que se usan:
 
| Relación | Significado en este modelo |
|---|---|
| Composition | Una capacidad de Nivel 1 se compone de las de Nivel 2, y estas de las de Nivel 3 |
| Serving | La capacidad origen sirve a la capacidad o a la etapa destino; "A sirve a B" también se lee "B depende de A" |
| Realization | Un paso del proceso realiza una capacidad. En la V1, un resultado, un principio o un requisito realiza una meta, un resultado o un principio |
| Assignment | Un actor, rol o recurso se asigna a un paso o a una capacidad |
| Triggering | Secuencia entre etapas o pasos, o un evento que dispara una etapa o un paso |
| Association | Un curso de acción se ejecuta mediante una capacidad, o un evento se asocia con la etapa que dispara. En la V1, un interesado se asocia con un impulsor y un impulsor con una evaluación |
| Influence | Solo en la V1: una evaluación motiva una meta («motiva +») y una restricción limita un requisito («restringe») |
| Aggregation | Solo en la V1: una meta general se compone de sub-metas (se dibuja por anidamiento) |
 
---
 
## 1.1 V1: motivación de la solución, de la necesidad a la meta

![V1 - Motivación de la solución de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/main/motivacion/V1%20%C2%B7%20Motivaci%C3%B3n.png?raw=true)

### Qué muestra

Una sola vista de la capa de Motivación de ArchiMate con los 56 elementos del modelo de motivación y 75 relaciones dibujadas. Responde por qué se necesita la aplicación de gobierno de datos: quién la necesita (interesados), qué fuerzas la originan (impulsores), qué problemas actuales la justifican (evaluaciones), qué se quiere lograr (metas y resultados) y qué requisitos, principios y restricciones se derivan. No basta con listar necesidades: la vista muestra cómo cada necesidad conduce a un objetivo de la solución.

### Cómo se lee

Es una sola vista organizada en **bandas horizontales** que se leen de arriba hacia abajo, de la necesidad a la solución:

| Banda | Elementos | Lectura |
|---|---|---|
| Interesados internos y externos | S1–S8 | quién tiene la necesidad |
| Impulsores | D1–D5 | qué fuerza la origina |
| Evaluaciones (problemas actuales) | A1–A9 | qué problema concreto hace evidente cada impulsor |
| Metas | G1 con G2–G6 anidadas | qué se quiere lograr; cada evaluación **motiva** una meta |
| Resultados esperados y principios | O1–O9, P1–P5 | cómo se sabrá que se logró y bajo qué criterios; ambos **realizan** las metas |
| Requisitos de la aplicación | R1–R10 | qué debe hacer la aplicación; los requisitos **realizan** resultados y principios |
| Restricciones | C1–C4 | qué limita a los requisitos |

Las sub-metas G2–G6 están **anidadas dentro de G1**: el anidamiento representa la relación de agregación (G1 se compone de ellas), por eso no se dibujan esas cinco líneas. El proveedor del CRM aparece **dos veces**, como el mismo elemento del modelo: arriba, junto al impulsor de fragmentación, y abajo, junto a la restricción C3 que condiciona. Así se evita una línea que cruce toda la vista.

> **Códigos.** Los códigos de esta vista (S, D, A, G, O, P, R, C) son propios de la V1. En el resto del documento, S1–S4 son los sistemas fuente (en el nombre del resultado O1 se mantienen así) y P1–P9 son los pasos del proceso E2E.

### Relaciones usadas

| Relación | Cómo se ve en Archi | Uso en la vista | Lectura |
|---|---|---|---|
| Asociación | Línea continua sin flecha | Interesado–impulsor e impulsor–evaluación | «le importa» / «hace evidente» |
| Influencia positiva | Línea discontinua con flecha abierta y la etiqueta «motiva +» | Evaluación → meta | el problema empuja a perseguir la meta |
| Influencia | Línea discontinua con flecha abierta y la etiqueta «restringe» | Restricción → requisito | la restricción limita cómo puede cumplirse el requisito |
| Realización | Línea discontinua con punta de triángulo vacío | Resultado → meta, principio → meta, requisito → resultado, requisito → principio | «contribuye a lograr» |
| Agregación (anidada) | Cajas anidadas, sin línea | G1 → G2…G6 | la meta general se compone de las sub-metas |

El «+» de «motiva +» es el signo de la influencia: la evaluación favorece la meta. «restringe» no lleva signo porque limita, no empuja a favor ni en contra.

### Cadena de justificación: de la necesidad a la meta

Cada fila sigue un hilo completo impulsor → evaluación → meta. Es la respuesta a «cómo cada necesidad conduce a un objetivo».

| Impulsor | Evaluación (problema actual) | Meta que motiva |
|---|---|---|
| D4 · Calidad y coherencia de la información | A1 · No existe un diccionario de datos integrado | G2 · Conocer los datos que maneja la empresa |
| D5 · Fragmentación de sistemas y fuentes | A1 · No existe un diccionario de datos integrado | G2 · Conocer los datos que maneja la empresa |
| D4 · Calidad y coherencia de la información | A1 · No existe un diccionario de datos integrado | G4 · Describir los datos con un lenguaje común |
| D5 · Fragmentación de sistemas y fuentes | A1 · No existe un diccionario de datos integrado | G4 · Describir los datos con un lenguaje común |
| D4 · Calidad y coherencia de la información | A2 · Términos de negocio ambiguos y sin catálogo | G4 · Describir los datos con un lenguaje común |
| D1 · Cumplimiento de la Ley 1581 de 2012 | A3 · Atributos sin responsable formal | G4 · Describir los datos con un lenguaje común |
| D1 · Cumplimiento de la Ley 1581 de 2012 | A4 · Clasificación de datos intuitiva y sin documentar | G3 · Clasificar los datos |
| D3 · Riesgo de exposición de datos personales | A4 · Clasificación de datos intuitiva y sin documentar | G3 · Clasificar los datos |
| D4 · Calidad y coherencia de la información | A5 · Reglas de calidad dispersas y desiguales | G4 · Describir los datos con un lenguaje común |
| D1 · Cumplimiento de la Ley 1581 de 2012 | A6 · Datos personales en canales informales sin inventario | G2 · Conocer los datos que maneja la empresa |
| D3 · Riesgo de exposición de datos personales | A6 · Datos personales en canales informales sin inventario | G2 · Conocer los datos que maneja la empresa |
| D2 · Rendición de cuentas ante la SIC | A7 · Cambios de estructura y de finalidad sin registro | G5 · Mantener el diccionario vigente y trazable |
| D5 · Fragmentación de sistemas y fuentes | A7 · Cambios de estructura y de finalidad sin registro | G5 · Mantener el diccionario vigente y trazable |
| D2 · Rendición de cuentas ante la SIC | A8 · La cobertura de metadatos no se mide | G6 · Contar con evidencia consultable del gobierno de datos |
| D1 · Cumplimiento de la Ley 1581 de 2012 | A9 · Documentación de cumplimiento incompleta | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos |
| D2 · Rendición de cuentas ante la SIC | A9 · Documentación de cumplimiento incompleta | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos |

Un hilo completo, de arriba abajo: Jurídica (interesado) se asocia con *Cumplimiento de la Ley 1581* (impulsor), que se asocia con *Clasificación de datos intuitiva y sin documentar* (evaluación), que motiva *Clasificar los datos* (meta). A esa meta la realiza el resultado *Atributos con clasificación registrada*; a ese resultado lo realiza el requisito *Registrar la clasificación de cada atributo*, y la restricción *Obligaciones legales por verificar con Jurídica* limita a ese requisito.

### Interesados y sus necesidades

| ID | Interesado | Necesidad / interés | Naturaleza |
|---|---|---|---|
| S1 | Gerencia general | Necesidad: reducir el riesgo legal y reputacional de la empresa y contar con información confiable para decidir. Espera ver avances medibles (cobertura de metadatos). | Supuesto del escenario |
| S2 | Jurídica / protección de datos | Necesidad: saber qué datos personales existen, cómo están clasificados y quién responde por ellos, para validar la clasificación y atender consultas. El rol de 'oficial de protección de datos' queda abierto: no se asume que la ley exija un cargo con esa denominación. | Supuesto del escenario |
| S3 | Responsables de datos por área | Personas expertas de las áreas de negocio (comercial, administración, contabilidad, etc.). Necesidad: un lugar único donde definir y consultar el significado y la calidad esperada de sus atributos y acordar términos con otras áreas. | Supuesto del escenario |
| S4 | Equipo de TI | Necesidad: documentar la estructura técnica y vincularla con el significado de negocio; saber qué impacto tiene un cambio de estructura; conservar el control del acceso a los motores. | Supuesto del escenario |
| S5 | Titulares de los datos | Clientes, propietarios, arrendatarios y personas de contacto. Necesidad: que sus datos se traten conforme a la ley y a la finalidad autorizada. Interesado externo que no usa la aplicación. | Supuesto del escenario |
| S6 | Superintendencia de Industria y Comercio (SIC) | Autoridad de protección de datos. Necesidad: que la organización pueda demostrar cómo administra los datos personales. El formato y la obligación de reporte están por verificar; la entrevista no muestra una API o reporte automático. | Supuesto del escenario |
| S7 | Seguridad de la información | Necesidad: saber dónde están los datos privados y sensibles para priorizar controles. Aparece en las interoperabilidades del enunciado, pero el escenario no define si es un área propia o parte de TI (supuesto arquitectónico). | Propuesta del equipo (por validar) |
| S8 | Proveedor del CRM | Proveedor externo del CRM en la nube (S2). Interés: controlar qué estructura de su plataforma expone. La entrega de metadatos del CRM depende de él. | Supuesto del escenario |

### Impulsores

| ID | Impulsor | Descripción | Fuente |
|---|---|---|---|
| D1 | Cumplimiento de la Ley 1581 de 2012 | Obligación de protección de datos personales aplicable a la empresa. El alcance exacto de las obligaciones debe verificarse con Jurídica y en fuentes oficiales vigentes; la aplicación apoya, no garantiza el cumplimiento. | Enunciado; Bloque 7; H-09 |
| D2 | Rendición de cuentas ante la SIC | Necesidad de poder demostrar, con información clara, cómo se administran los datos personales. El formato y la obligación de reporte están por verificar. | Bloques 7 y 8; H-12 |
| D3 | Riesgo de exposición de datos personales | Hay datos personales en hojas de cálculo, carpetas, correo y WhatsApp, y atributos delicados (ingresos, mora, datos de menores, imágenes de documentos). Riesgo de incidentes, sanciones y daño reputacional. | Bloques 4 y 7; H-08 |
| D4 | Calidad y coherencia de la información | La operación (arriendos, ventas, contabilidad) depende de datos consistentes. Hoy hay nombres de campo ambiguos, reglas de validación distintas y digitación repetida entre CRM y arriendos. | Bloques 1, 2 y 5; H-04 |
| D5 | Fragmentación de sistemas y fuentes | S1–S4 (motores distintos y proveedores distintos) más S5 y canales informales, sin diccionario técnico central. | Bloques 1 y 8; H-03 |

### Problemas actuales del gobierno de datos (evaluaciones)

| ID | Evaluación | Descripción | Fuente |
|---|---|---|---|
| A1 | No existe un diccionario de datos integrado | Los metadatos técnicos (en cada motor) y los de negocio (conocimiento tácito) están separados; no hay una vista única por atributo. | Bloque 2; H-04 |
| A2 | Términos de negocio ambiguos y sin catálogo | 'Cliente', 'activo', 'estado', 'canon' y 'propietario' significan cosas distintas según el área; los conflictos se resuelven caso por caso. | Bloques 2 y 5; H-05 |
| A3 | Atributos sin responsable formal | Las definiciones dependen de conocimiento tácito; TI conoce la estructura pero no siempre el significado de negocio; no hay mecanismo estable para aprobar definiciones. | Bloque 3; H-06 |
| A4 | Clasificación de datos intuitiva y sin documentar | Casos dudosos: direcciones, identificaciones, ingresos, extractos, mora, referencias personales, datos de menores, imágenes de documentos y observaciones libres. Las clasificaciones tentativas no son dictamen jurídico. | Bloque 4; H-09 |
| A5 | Reglas de calidad dispersas y desiguales | Validaciones distintas en S1, S2 y S4 y sin control equivalente en S5; los errores se detectan después de ocurrir. | Bloques 2 y 4; H-07 |
| A6 | Datos personales en canales informales sin inventario | Hojas de cálculo, carpetas, correo y WhatsApp no tienen diccionario técnico que importar; requieren inventario manual. | Bloques 5 y 8; H-08 |
| A7 | Cambios de estructura y de finalidad sin registro | Se agregan o cambian campos (p. ej., '¿Acepta publicidad?' existe en la web y no en el CRM) o cambia el uso de un dato sin avisar ni revisar su clasificación. | Bloques 2, 4 y 5; H-10, H-15 |
| A8 | La cobertura de metadatos no se mide | No hay línea base de cuántos atributos tienen definición, responsable, clasificación o regla de calidad. | Bloque 6; H-11, H-17 |
| A9 | Documentación de cumplimiento incompleta | Formatos de autorización dispersos, política de tratamiento en desuso, sin procedimiento de solicitudes ni política de conservación. Se resuelve sobre todo con procesos organizacionales, fuera del núcleo de la aplicación. | Bloque 7; H-14 |

### Metas y resultados esperados

Las **metas** dicen qué se quiere lograr (cualitativas); los **resultados** dicen cómo se sabrá que se logró (medibles). Los indicadores son *candidatos* tomados de la entrevista (H-11); no son metas obligatorias del enunciado ni compromisos aprobados, y no llevan cifras porque las del escenario son ficticias (H-17).

| ID | Meta | Resultados que la realizan |
|---|---|---|
| G1 | Gobernar los datos y apoyar el cumplimiento de protección de datos — Meta general. La aplicación contribuye al cumplimiento con información clara sobre qué datos existen, cómo están clasificados y quién responde por ellos; no sustituye los procesos legales, de seguridad ni de operación. | Agrega G2–G6 |
| G2 | Conocer los datos que maneja la empresa — Inventario de atributos y fuentes, estructuradas y no estructuradas ('conocer' en el enunciado). | O1 · Metadatos técnicos de S1–S4 importados<br>O2 · Fuentes no estructuradas inventariadas |
| G3 | Clasificar los datos — Asignar a cada atributo una categoría (público, semiprivado, privado, sensible) con revisión jurídica. | O3 · Atributos con clasificación registrada |
| G4 | Describir los datos con un lenguaje común — Definición, responsable, políticas de calidad, expresiones regulares y términos de negocio asociados a cada atributo. | O4 · Atributos con definición y responsable asignados<br>O5 · Atributos con política de calidad y regla de validación<br>O6 · Términos asociados a atributos y conflictos identificados<br>O7 · Diccionario integrado consultable por atributo |
| G5 | Mantener el diccionario vigente y trazable — Que los cambios de estructura, las importaciones y las decisiones queden registrados. Meta derivada del escenario, no del enunciado. | O8 · Historial de importaciones y cambios disponible |
| G6 | Contar con evidencia consultable del gobierno de datos — Que Jurídica, Seguridad y la dirección puedan consultar y exportar la información para revisión y para preparar lo que se requiera ante la SIC. | O9 · Metadatos consultables y exportables para revisión |

| ID | Resultado | Indicador / observación |
|---|---|---|
| O1 | Metadatos técnicos de S1–S4 importados | Indicador candidato: columnas importadas / columnas existentes en cada motor. La meta numérica queda por definir con una línea base real (las cifras del escenario son ficticias). |
| O2 | Fuentes no estructuradas inventariadas | Hojas, carpetas, correo y WhatsApp registrados manualmente (contenido, responsable, tipos de datos). Indicador candidato: fuentes inventariadas / fuentes identificadas. |
| O3 | Atributos con clasificación registrada | Cada atributo con categoría o con estado 'pendiente' / 'en revisión'. Denominador: atributos de negocio inventariados. |
| O4 | Atributos con definición y responsable asignados | Indicador candidato: atributos con definición y responsable / atributos de negocio inventariados. |
| O5 | Atributos con política de calidad y regla de validación | Sólo donde aplique. Denominador: atributos que requieren regla de validación, no todos los atributos. La expresión regular valida formato, no licitud ni veracidad. |
| O6 | Términos asociados a atributos y conflictos identificados | Términos con atributos asociados y conflictos de significado visibles. Resolverlos sigue siendo decisión de la organización. |
| O7 | Diccionario integrado consultable por atributo | Cada atributo con sus metadatos técnicos y de negocio juntos y comparables. |
| O8 | Historial de importaciones y cambios disponible | Fecha y estado de importación, diferencias de estructura detectadas y cambios de clasificación o definición. |
| O9 | Metadatos consultables y exportables para revisión | Consultas o exportaciones para Jurídica, Seguridad y preparación de información ante la SIC. No se asume una integración regulatoria automática. |

### Principios, requisitos y restricciones

#### Principios

| ID | Principio | Qué significa | Realiza |
|---|---|---|---|
| P1 | El negocio es dueño del significado de sus datos | El responsable de negocio define y aprueba; TI administra lo técnico. No se da autoridad automática a TI sobre las definiciones. | G4 |
| P2 | Mostrar lo faltante o dudoso como tal | Un atributo sin definición, responsable o clasificación se muestra como incompleto o 'en revisión', no como correcto. | G3, G4 |
| P3 | Gobernar metadatos sin modificar los sistemas operativos | La aplicación documenta y gobierna; no corrige datos, no depura duplicados ni reemplaza S1–S5. | G1 |
| P4 | Un término, una definición vigente | Cada término del catálogo tiene una definición vigente; los conflictos de significado se hacen explícitos (lenguaje ubicuo para DDD). | G4 |
| P5 | La decisión jurídica es de Jurídica | La aplicación registra y propone; la categoría final de un atributo la valida Jurídica o la asesoría competente. | G3 |

#### Requisitos

| ID | Requisito | Detalle | Origen | Realiza |
|---|---|---|---|---|
| R1 | Importar metadatos técnicos desde los motores | Tipo de dato y longitud (y nombre de tabla y columna) leídos de los diccionarios de S1–S4. | Requisito del enunciado | O1, P3 |
| R2 | Registrar la clasificación de cada atributo | Categoría (público, semiprivado, privado, sensible) y estado (clasificado, pendiente, en revisión). | Requisito del enunciado | O3, P2, P5 |
| R3 | Registrar definición y responsable por atributo | Metadatos de negocio por atributo: definición y responsable de negocio. | Requisito del enunciado | O4, P1 |
| R4 | Registrar políticas de calidad y expresiones regulares | Política de calidad y expresión regular de validación por atributo cuando aplique. | Requisito del enunciado | O5 |
| R5 | Gestionar el diccionario de datos integrado | Vista unificada de metadatos técnicos y de negocio por atributo. | Requisito del enunciado | O7 |
| R6 | Gestionar el catálogo de términos y asociarlos a atributos | Alta y mantenimiento de términos de negocio, cada uno asociado a los atributos que lo describen. | Requisito del enunciado | O6, P4 |
| R7 | Registrar manualmente fuentes no estructuradas | Inventario manual de hojas, carpetas, correo y canales de mensajería, sin escaneo automático. | Propuesta del equipo (por validar) | O2 |
| R8 | Registrar importaciones y detectar cambios de estructura | Fecha y estado de importación, reimportación y comparación de estructura; historial de cambios de clasificación y definición. | Propuesta del equipo (por validar) | O8 |
| R9 | Consultar y exportar metadatos | Para Jurídica, Seguridad de la información y preparación de información ante la SIC (consulta o exportación, no integración automática). | Propuesta del equipo (por validar) | O9 |
| R10 | Gestionar roles de edición y aprobación | Quién propone, revisa y aprueba definiciones y clasificaciones. Las reglas de autoridad quedan por definir con la organización. | Propuesta del equipo (por validar) | O4, P1, P5 |

R1–R6 corresponden uno a uno al alcance funcional del enunciado; R7–R10 son propuestas del equipo derivadas del escenario y deben validarse.

#### Restricciones

| ID | Restricción | Detalle | Afecta a |
|---|---|---|---|
| C1 | Solo lectura de estructura; sin leer datos personales | La herramienta lee la estructura (metadatos) y no los registros con datos personales. Restricción candidata del escenario que debe reflejarse en permisos e interoperabilidad. | R1 |
| C2 | Obligaciones legales por verificar con Jurídica | Las categorías finales y las reglas sobre autorización, menores, datos financieros, finalidad o conservación se contrastan con fuentes oficiales; los ejemplos de la entrevista no son dictamen. | R2 |
| C3 | Acceso a metadatos del CRM depende del proveedor | La estructura del CRM (S2) se obtiene mediante el proveedor, con tiempos y permisos que la empresa no controla. | R1 |
| C4 | Fuera de alcance: autorizaciones, solicitudes de titulares y depuración | Tampoco incluye reportes regulatorios automáticos ni gestión de accesos o de copias de respaldo; son procesos organizacionales con los que sólo se interopera. | R9 |

### Justificación

La vista responde por qué se necesita la aplicación y deja explícito su alcance. Las metas G2, G3 y G4 y los requisitos R1–R6 corresponden uno a uno al alcance funcional del enunciado; G5, G6 y R7–R10 son propuestas del equipo derivadas del escenario y deben validarse. Las restricciones y las metas que la aplicación no cubre son coherentes con las capacidades marcadas como fuera de alcance en la V2 y con los servicios excluidos de la V4b: la aplicación documenta y gobierna metadatos, no corrige datos ni reemplaza los procesos legales, de seguridad o de operación.

### Supuestos arquitectónicos e impacto

| # | Supuesto | Impacto si cambia |
|---|---|---|
| 1 | Se modela el caso ficticio **Hogar Andino** tal como lo propuso la entrevista; cifras, cargos y sistemas no son hechos reales. | Si el profesor fija otro escenario, cambian S1–S8 y los impulsores D3–D5; las metas G2–G4 y R1–R6 no, porque vienen del enunciado. |
| 2 | El rol de oficial de protección de datos queda abierto: se modela «Jurídica / protección de datos» como interesado. | Si se define un cargo formal, se separa de S2 y se ajusta R10 (roles de aprobación). |
| 3 | «Seguridad de la información» se trata como interesado propio aunque el escenario no define el área (podría ser parte de TI). | Si es parte de TI, S7 se fusiona con S4 y D3 pierde un interesado directo. |
| 4 | La aplicación sólo lee estructura (metadatos), no datos personales (C1, candidata). | Si se necesita perfilar datos reales, cambian R1, el riesgo D3 sobre la propia herramienta y los permisos. |
| 5 | No hay integración automática con la SIC: sólo consulta o exportación (R9, C4). | Si el formato de reporte es obligatorio y estructurado, se agrega un requisito y un actor técnico. |
| 6 | G5 (vigencia y trazabilidad) y G6 (evidencia) son metas **derivadas del escenario**, no del enunciado. | Si el equipo las excluye, se eliminan O8, O9, R8, R9 y A7/A8 pierden destino. |
| 7 | Los indicadores de O1–O6 son candidatos sin meta numérica. | Se necesita una línea base real antes de fijar metas (H-17). |

### Inconsistencias y puntos a cuestionar

1. **El Bloque 6 del guion repite el Bloque 7.** En el documento de la Fase 0 las preguntas del Bloque 6 («Indicadores y resultados») son las de normatividad y su objetivo dice «obligaciones y restricciones», pero los hallazgos del Bloque 6 hablan de indicadores. Conviene corregir el guion para que coincida con lo realmente preguntado.
2. **«Cumplir la ley» no es una meta alcanzable por software.** La entrevista lo reconoce (registrar metadatos no garantiza cumplimiento). Por eso el impulsor es «Cumplimiento de la Ley 1581» y la meta es «**apoyar** el cumplimiento» (G1). Se descartó también «cero duplicados» como resultado, porque la aplicación no corrige datos operativos (H-14).
3. **Las categorías de datos requieren verificación jurídica.** El enunciado atribuye la clasificación público/semiprivado/privado/sensible a la Ley 1581. Hasta donde sé, el dato sensible está definido en la Ley 1581 y la distinción público/semiprivado/privado proviene sobre todo de la Ley 1266 de 2008, además de normas reglamentarias; hay que confirmarlo con fuentes oficiales vigentes antes de citarlo en el informe (restricción C2, principio P5).
4. **A9 (documentación de cumplimiento incompleta) se resuelve sobre todo fuera de la aplicación.** Se dejó en el modelo porque justifica G1, pero sólo se cubre la parte de metadatos; autorizaciones, solicitudes de titulares y conservación son procesos organizacionales (C4).
5. **Interesados externos sin voz directa.** Titulares y SIC no usan la aplicación: su necesidad se infiere de la ley y de la entrevista, no se validó con ellos.
6. **Decisión pendiente de fondo:** quién puede proponer, revisar y aprobar definiciones y clasificaciones (R10). La entrevista no lo resuelve y afecta el diseño de roles.

<details>
<summary><b>Anexo: las 80 relaciones de la V1 y su justificación</b></summary>

| Tipo | Origen | Destino | Justificación |
|---|---|---|---|
| Asociación | S1 · Gerencia general | D1 · Cumplimiento de la Ley 1581 de 2012 | La gerencia responde ante la ley por el tratamiento de datos de la empresa. |
| Asociación | S1 · Gerencia general | D3 · Riesgo de exposición de datos personales | La gerencia asume el riesgo legal y reputacional de una exposición de datos. |
| Asociación | S1 · Gerencia general | D4 · Calidad y coherencia de la información | Necesita información coherente para operar y decidir. |
| Asociación | S2 · Jurídica / protección de datos | D1 · Cumplimiento de la Ley 1581 de 2012 | Jurídica vela por el cumplimiento de la Ley 1581 y orienta a las áreas. |
| Asociación | S2 · Jurídica / protección de datos | D2 · Rendición de cuentas ante la SIC | Jurídica prepara y valida la información que eventualmente se presente a la SIC. |
| Asociación | S3 · Responsables de datos por área | D4 · Calidad y coherencia de la información | Cada área sufre inconsistencias, reprocesos y términos ambiguos en sus propios datos. |
| Asociación | S3 · Responsables de datos por área | D5 · Fragmentación de sistemas y fuentes | Las áreas digitan y consultan datos en varios sistemas y canales. |
| Asociación | S4 · Equipo de TI | D5 · Fragmentación de sistemas y fuentes | TI administra los sistemas fragmentados y recibe el impacto de sus cambios. |
| Asociación | S5 · Titulares de los datos | D1 · Cumplimiento de la Ley 1581 de 2012 | La ley protege los derechos de los titulares sobre sus datos. |
| Asociación | S5 · Titulares de los datos | D3 · Riesgo de exposición de datos personales | Los titulares son quienes sufren la exposición de sus datos. |
| Asociación | S6 · Superintendencia de Industria y Comercio (SIC) | D1 · Cumplimiento de la Ley 1581 de 2012 | La SIC vigila el cumplimiento de la ley de protección de datos. |
| Asociación | S6 · Superintendencia de Industria y Comercio (SIC) | D2 · Rendición de cuentas ante la SIC | La SIC es la autoridad ante la cual la empresa rinde cuentas. |
| Asociación | S7 · Seguridad de la información | D3 · Riesgo de exposición de datos personales | Seguridad necesita saber dónde están los datos de mayor riesgo para protegerlos. |
| Asociación | S8 · Proveedor del CRM | D5 · Fragmentación de sistemas y fuentes | El CRM es una plataforma externa; su estructura sólo se obtiene a través del proveedor. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A3 · Atributos sin responsable formal | Cumplir exige saber quién responde por cada dato; hoy no hay responsable formal. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A4 · Clasificación de datos intuitiva y sin documentar | Aplicar la ley exige clasificar los datos; hoy la clasificación es intuitiva. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A6 · Datos personales en canales informales sin inventario | Los datos personales en canales informales escapan al control que exige la ley. |
| Asociación | D1 · Cumplimiento de la Ley 1581 de 2012 | A9 · Documentación de cumplimiento incompleta | La obligación legal se evidencia con documentación que hoy está incompleta. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A7 · Cambios de estructura y de finalidad sin registro | Rendir cuentas requiere trazabilidad de cambios; hoy no se registran. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A8 · La cobertura de metadatos no se mide | No se puede demostrar avance sin medir la cobertura de metadatos. |
| Asociación | D2 · Rendición de cuentas ante la SIC | A9 · Documentación de cumplimiento incompleta | Sin políticas y procedimientos documentados no hay evidencia que presentar. |
| Asociación | D3 · Riesgo de exposición de datos personales | A4 · Clasificación de datos intuitiva y sin documentar | Sin clasificar no se sabe qué datos privados o sensibles necesitan más protección. |
| Asociación | D3 · Riesgo de exposición de datos personales | A6 · Datos personales en canales informales sin inventario | Los canales informales son la mayor superficie de exposición. |
| Asociación | D4 · Calidad y coherencia de la información | A1 · No existe un diccionario de datos integrado | La información no es coherente cuando metadatos técnicos y de negocio están separados. |
| Asociación | D4 · Calidad y coherencia de la información | A2 · Términos de negocio ambiguos y sin catálogo | Términos ambiguos producen interpretaciones distintas del mismo dato. |
| Asociación | D4 · Calidad y coherencia de la información | A5 · Reglas de calidad dispersas y desiguales | Reglas de validación dispersas generan datos inconsistentes entre sistemas. |
| Asociación | D5 · Fragmentación de sistemas y fuentes | A1 · No existe un diccionario de datos integrado | Cada sistema tiene su propio diccionario técnico, sin integración entre ellos. |
| Asociación | D5 · Fragmentación de sistemas y fuentes | A7 · Cambios de estructura y de finalidad sin registro | La fragmentación hace que los cambios de estructura no se comuniquen. |
| Influencia | A1 · No existe un diccionario de datos integrado | G2 · Conocer los datos que maneja la empresa | Sin diccionario no se sabe con certeza qué datos existen en cada sistema. |
| Influencia | A1 · No existe un diccionario de datos integrado | G4 · Describir los datos con un lenguaje común | Describir exige unir lo técnico y lo de negocio en un solo lugar. |
| Influencia | A2 · Términos de negocio ambiguos y sin catálogo | G4 · Describir los datos con un lenguaje común | Un lenguaje común exige un catálogo de términos asociado a atributos. |
| Influencia | A3 · Atributos sin responsable formal | G4 · Describir los datos con un lenguaje común | Describir incluye asignar y mantener un responsable por atributo. |
| Influencia | A4 · Clasificación de datos intuitiva y sin documentar | G3 · Clasificar los datos | La clasificación intuitiva y sin registro motiva clasificar de forma sistemática. |
| Influencia | A5 · Reglas de calidad dispersas y desiguales | G4 · Describir los datos con un lenguaje común | Las políticas de calidad y expresiones regulares forman parte de la descripción del atributo. |
| Influencia | A6 · Datos personales en canales informales sin inventario | G2 · Conocer los datos que maneja la empresa | Hay que inventariar las fuentes no estructuradas para conocer todos los datos. |
| Influencia | A7 · Cambios de estructura y de finalidad sin registro | G5 · Mantener el diccionario vigente y trazable | Los cambios sin registro motivan mantener el diccionario vigente y trazable. |
| Influencia | A8 · La cobertura de metadatos no se mide | G6 · Contar con evidencia consultable del gobierno de datos | Sin cobertura medida no hay evidencia consultable del gobierno de datos. |
| Influencia | A9 · Documentación de cumplimiento incompleta | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | La documentación incompleta justifica la meta general; la aplicación sólo cubre la parte de metadatos. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G2 · Conocer los datos que maneja la empresa | 'Conocer' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G3 · Clasificar los datos | 'Clasificar' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G4 · Describir los datos con un lenguaje común | 'Describir' es una de las tres acciones del enunciado. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G5 · Mantener el diccionario vigente y trazable | Sin vigencia y trazabilidad el diccionario pierde valor con el tiempo. |
| Agregación | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | G6 · Contar con evidencia consultable del gobierno de datos | Apoyar el cumplimiento implica poder mostrar evidencia. |
| Realización | O1 · Metadatos técnicos de S1–S4 importados | G2 · Conocer los datos que maneja la empresa | Con los metadatos técnicos importados se conoce la estructura de los datos de S1–S4. |
| Realización | O2 · Fuentes no estructuradas inventariadas | G2 · Conocer los datos que maneja la empresa | Inventariar lo no estructurado completa el conocimiento de los datos. |
| Realización | O3 · Atributos con clasificación registrada | G3 · Clasificar los datos | Un atributo con categoría o estado registrado evidencia que fue clasificado. |
| Realización | O4 · Atributos con definición y responsable asignados | G4 · Describir los datos con un lenguaje común | Definición y responsable son parte central de la descripción. |
| Realización | O5 · Atributos con política de calidad y regla de validación | G4 · Describir los datos con un lenguaje común | Políticas de calidad y reglas de validación describen cómo debe ser el dato. |
| Realización | O6 · Términos asociados a atributos y conflictos identificados | G4 · Describir los datos con un lenguaje común | Términos asociados a atributos dan el lenguaje común. |
| Realización | O7 · Diccionario integrado consultable por atributo | G4 · Describir los datos con un lenguaje común | El diccionario integrado reúne la descripción técnica y de negocio. |
| Realización | O8 · Historial de importaciones y cambios disponible | G5 · Mantener el diccionario vigente y trazable | El historial muestra que el diccionario se mantiene vigente. |
| Realización | O9 · Metadatos consultables y exportables para revisión | G6 · Contar con evidencia consultable del gobierno de datos | Poder consultar y exportar es la evidencia que se necesita. |
| Realización | P1 · El negocio es dueño del significado de sus datos | G4 · Describir los datos con un lenguaje común | La responsabilidad de negocio hace confiable la descripción de los datos. |
| Realización | P2 · Mostrar lo faltante o dudoso como tal | G3 · Clasificar los datos | Un estado 'en revisión' evita presentar como definitiva una clasificación dudosa. |
| Realización | P2 · Mostrar lo faltante o dudoso como tal | G4 · Describir los datos con un lenguaje común | Lo incompleto debe verse como incompleto en la descripción. |
| Realización | P3 · Gobernar metadatos sin modificar los sistemas operativos | G1 · Gobernar los datos y apoyar el cumplimiento de protección de datos | Delimita la meta general: se gobiernan metadatos, no se reemplazan procesos operativos. |
| Realización | P4 · Un término, una definición vigente | G4 · Describir los datos con un lenguaje común | Una definición vigente por término es la base del lenguaje común. |
| Realización | P5 · La decisión jurídica es de Jurídica | G3 · Clasificar los datos | La clasificación sólo es confiable si la valida quien tiene competencia jurídica. |
| Realización | R1 · Importar metadatos técnicos desde los motores | O1 · Metadatos técnicos de S1–S4 importados | Importar desde los diccionarios de los motores produce los metadatos técnicos. |
| Realización | R7 · Registrar manualmente fuentes no estructuradas | O2 · Fuentes no estructuradas inventariadas | El registro manual es la única vía para inventariar fuentes sin motor de base de datos. |
| Realización | R2 · Registrar la clasificación de cada atributo | O3 · Atributos con clasificación registrada | Registrar categoría y estado produce atributos clasificados o pendientes. |
| Realización | R3 · Registrar definición y responsable por atributo | O4 · Atributos con definición y responsable asignados | Registrar definición y responsable produce atributos descritos. |
| Realización | R10 · Gestionar roles de edición y aprobación | O4 · Atributos con definición y responsable asignados | Roles de edición y aprobación aseguran que definición y responsable tengan dueño y autoridad. |
| Realización | R4 · Registrar políticas de calidad y expresiones regulares | O5 · Atributos con política de calidad y regla de validación | Registrar políticas y expresiones regulares produce los atributos con regla. |
| Realización | R6 · Gestionar el catálogo de términos y asociarlos a atributos | O6 · Términos asociados a atributos y conflictos identificados | El catálogo y sus asociaciones producen los términos vinculados a atributos. |
| Realización | R5 · Gestionar el diccionario de datos integrado | O7 · Diccionario integrado consultable por atributo | Gestionar el diccionario integrado produce la vista consultable por atributo. |
| Realización | R8 · Registrar importaciones y detectar cambios de estructura | O8 · Historial de importaciones y cambios disponible | Registrar importaciones y cambios produce el historial. |
| Realización | R9 · Consultar y exportar metadatos | O9 · Metadatos consultables y exportables para revisión | Consultar y exportar produce los metadatos disponibles para revisión. |
| Realización | R1 · Importar metadatos técnicos desde los motores | P3 · Gobernar metadatos sin modificar los sistemas operativos | Importa estructura sin escribir en los sistemas de origen. |
| Realización | R2 · Registrar la clasificación de cada atributo | P2 · Mostrar lo faltante o dudoso como tal | El estado 'pendiente' / 'en revisión' hace visible lo dudoso. |
| Realización | R2 · Registrar la clasificación de cada atributo | P5 · La decisión jurídica es de Jurídica | El estado 'en revisión' permite la validación jurídica antes de dar por final una categoría. |
| Realización | R3 · Registrar definición y responsable por atributo | P1 · El negocio es dueño del significado de sus datos | El responsable de negocio queda registrado por atributo. |
| Realización | R10 · Gestionar roles de edición y aprobación | P1 · El negocio es dueño del significado de sus datos | Define quién propone y aprueba sin dar esa autoridad automáticamente a TI. |
| Realización | R10 · Gestionar roles de edición y aprobación | P5 · La decisión jurídica es de Jurídica | Incluye la aprobación jurídica de clasificaciones. |
| Realización | R6 · Gestionar el catálogo de términos y asociarlos a atributos | P4 · Un término, una definición vigente | El catálogo mantiene una definición vigente por término. |
| Influencia | C1 · Solo lectura de estructura; sin leer datos personales | R1 · Importar metadatos técnicos desde los motores | La importación se limita a estructura y no debe leer registros con datos personales. |
| Influencia | C3 · Acceso a metadatos del CRM depende del proveedor | R1 · Importar metadatos técnicos desde los motores | La importación desde el CRM depende de lo que entregue el proveedor. |
| Influencia | C2 · Obligaciones legales por verificar con Jurídica | R2 · Registrar la clasificación de cada atributo | La categoría final depende de la verificación jurídica con fuentes oficiales. |
| Influencia | C4 · Fuera de alcance: autorizaciones, solicitudes de titulares y depuración | R9 · Consultar y exportar metadatos | La exportación apoya los reportes, pero no se asume integración automática con la SIC. |
| Asociación | S8 · Proveedor del CRM | C3 · Acceso a metadatos del CRM depende del proveedor | El proveedor del CRM es quien condiciona el acceso a la estructura de S2. |

</details>

---

## 1.2 V2: mapa de capacidades
 
![V2 - Mapa de capacidades de Hogar Andino](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V2%20-%20Mapa%20de%20Capacidades%20de%20Hogar%20Andino.png)
 
### Qué muestra
 
El mapa de capacidades completo del negocio, con 78 elementos Capability organizados en tres niveles: 13 de Nivel 1, 44 de Nivel 2 y 21 de Nivel 3. Las capacidades se agrupan en cuatro franjas. El color de cada caja indica el impacto de la solución de gobierno de datos, y la leyenda está en la parte superior de la vista.
 
### Cómo se lee
 
La vista usa anidamiento: el Nivel 1 contiene a sus capacidades de Nivel 2, y estas a las de Nivel 3 (relación Composition representada por contención). Solo los bloques de gestión de datos y de cumplimiento se detallan hasta Nivel 3; el resto del negocio llega a Nivel 2. Las cinco flechas de la vista son relaciones Serving que parten de Gestión de Datos e Información hacia las capacidades que consumen sus resultados.
 
### Franjas y capacidades de Nivel 1
 
| Franja | Capacidades de Nivel 1 | Rol estratégico |
|---|---|---|
| Dirección y Cumplimiento | Planeación y Dirección Estratégica; Gestión de Cumplimiento y Riesgos | Soporte; Habilitadora crítica |
| Capacidades Core del Negocio inmobiliario | Gestión del Portafolio Inmobiliario; Comercialización de Inmuebles; Administración de Arrendamientos; Gestión de Relaciones con Clientes | Diferenciadoras (las tres primeras); Soporte |
| Gestión de Datos e Información | Gestión de Datos e Información, con Gobierno de Datos, Gestión de Metadatos, Clasificación de Datos, Gestión de la Calidad de Datos, Gestión de Datos Maestros y Gestión del Ciclo de Vida de los Datos | Habilitadora crítica |
| Capacidades Habilitadoras | Mercadeo y Canales Digitales; Gestión Financiera y Contable; Gestión Jurídica y Contractual; Gestión de Tecnología de la Información; Gestión del Talento Humano; Gestión Administrativa y de Compras | Soporte (las cuatro primeras) y Genérica (las dos últimas) |
 
### Propiedades de cada capacidad
 
Cada elemento Capability lleva ocho propiedades, que se pueden mostrar en Archi con una expresión de etiqueta:
 
| Propiedad | Valores usados |
|---|---|
| Nivel | Nivel 1, Nivel 2, Nivel 3 |
| Tipo de capacidad | Estratégica (22) o Táctica (56) |
| Rol estratégico (empresa) | Habilitadora crítica (33), Soporte (22), Diferenciadora (16), Genérica (7) |
| Subdominio DDD (solución Tema 2) | Dominio principal del Tema 2 (1), Core (6), Supporting (11), Generic (1), N/A fuera de la solución (59) |
| Impacto de la solución | Directo (12), Parcial (6), Indirecto (36), Fuera de alcance como brecha (9), Sin impacto (15) |
| Madurez actual (según entrevista) | Inexistente (17), Informal (24), No evaluada (37) |
| Estado de validación | Respaldada por la entrevista (64), Parcialmente respaldada (4), Inferida por validar con el experto (10) |
| Apoyo de la solución | Solo en los pasos del proceso (se usa en V3b y V3c) |
 
### Impacto de la solución
 
| Impacto | Significado | Capacidades |
|---|---|---|
| Directo | La solución opera aquí | Gestión de Datos e Información; Gestión de Metadatos; Clasificación de Datos; Gestión de responsables de datos; Gestión de trazabilidad y evidencia de decisiones; Gestión de metadatos de negocio; Gestión de metadatos técnicos; Gestión del diccionario de datos; Gestión del catálogo de términos de negocio; Inventario de atributos de negocio; Clasificación de atributos por categoría legal; Definición de políticas y reglas de calidad y validación |
| Parcial | La solución registra o prepara, pero la decisión o la ejecución es humana | Gobierno de Datos; Gestión de la Calidad de Datos; Resolución de conflictos y decisiones sobre datos; Gestión de cambios de estructura de datos; Validación jurídica de la clasificación; Reporte regulatorio ante la SIC |
| Indirecto | La capacidad consume o produce datos que la solución describe | 36 capacidades, entre ellas las del negocio inmobiliario y los bloques de cumplimiento y TI |
| Fuera de alcance (brecha) | Capacidad que el negocio necesita pero la solución no cubre | Políticas de tratamiento y avisos; autorizaciones de titulares; incidentes con datos personales; encargados del tratamiento; definición de políticas y principios de datos; medición y monitoreo de la calidad; depuración y duplicados; Gestión de Datos Maestros; Gestión del Ciclo de Vida de los Datos |
| Sin impacto | La solución no interviene | 15 capacidades, por ejemplo tesorería, talento humano y compras |
 
### Justificación
 
El dominio principal es Gobierno de Datos orientado a la protección de datos personales. Esta capacidad no diferencia a la inmobiliaria en el mercado: es una habilitadora crítica de cumplimiento, y solo es central dentro de la solución, donde el diccionario y la clasificación son lo que conviene construir con más cuidado. Las capacidades diferenciadoras del negocio son las de portafolio, comercialización y administración de arrendamientos.
 
Las capacidades fuera de alcance se dibujan en gris a propósito: hacen visible lo que la solución no cubre, para no prometer más de lo que entrega. La madurez "No evaluada" de 37 capacidades indica que la entrevista no cubre ese bloque y que debe validarse con el experto del negocio.
 
---
 
## 1.3 V2b: dependencias de gobierno de datos, recursos y cursos de acción
 
![V2b - Dependencias de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V2b%20-%20Dependencias%20de%20Gobierno%20de%20Datos.png)
 
### Qué muestra
 
El detalle del bloque de datos en columnas: 23 capacidades relacionadas por Serving, 7 recursos asignados a las capacidades que habilitan y 3 cursos de acción asociados a las capacidades que los ejecutan. La vista tiene 39 conexiones.
 
### Cómo se lee
 
La relación usada es Serving y se lee "A sirve a B", es decir, B depende de A. El orden de izquierda a derecha es: proveedores de servicio, gobierno, captura, integración y clasificación, y consumidores. Los recursos están en la parte inferior y los cursos de acción en la superior.
 
### Cadenas de dependencia
 
| Cadena | Razón |
|---|---|
| Gestión de metadatos técnicos, Inventario de atributos de negocio, Clasificación de atributos por categoría legal | No se clasifica lo que no se ha inventariado |
| Definición de políticas y principios, Validación jurídica y Resolución de conflictos, Clasificación de atributos | La categoría necesita criterio, aprobación y desempate |
| Gestión de metadatos técnicos, Gestión de metadatos de negocio y Clasificación, Gestión del diccionario de datos, Gestión del catálogo de términos | El diccionario integra todo y el catálogo se apoya en él |
| Gestión del diccionario y Clasificación, Atención de derechos de los titulares, Reporte regulatorio ante la SIC, Gestión de la seguridad de la información | Son los consumidores de la información |
| Gestión de aplicaciones y proveedores y Administración de accesos, Gestión de metadatos técnicos y Gestión de cambios de estructura | Sin acceso de solo lectura no hay importación |
| Gestión de responsables de datos y Definición de políticas y reglas de calidad, Gestión de metadatos de negocio | El metadato de negocio necesita dueño y regla |
| Gestión de trazabilidad y evidencia de decisiones, Reporte regulatorio ante la SIC | La evidencia de quién decidió y con qué criterio respalda el reporte |
 
### Recursos
 
| Recurso | Capacidad que habilita |
|---|---|
| Diccionarios de los motores de S1, S3 (SQL Server) y S4 (MySQL) | Gestión de metadatos técnicos |
| Consulta de solo lectura sobre la estructura del CRM S2 (PostgreSQL), vía proveedor | Gestión de metadatos técnicos |
| Conocimiento jurídico (abogada interna y abogado externo) | Validación jurídica de la clasificación |
| Coordinador de TI | Gestión de aplicaciones y proveedores de software |
| Responsables de dato por área (por designar) | Gestión de responsables de datos |
| Oficial de protección de datos (cargo por decidir) | Atención de derechos de los titulares |
| Marco normativo: Ley 1581 de 2012, Ley 1266 de 2008, Decreto 1074 de 2015 y guías de la SIC | Gestión del cumplimiento normativo |
 
### Cursos de acción
 
Son propuestas del equipo basadas en las metas de ejemplo del Bloque 6 de la entrevista, por validar:
 
| Curso de acción | Se ejecuta mediante |
|---|---|
| Inventariar y clasificar primero los atributos con datos personales | Inventario de atributos de negocio; Clasificación de atributos por categoría legal |
| Documentar la estructura técnica de S1, S3 y S4 y gestionar S2 vía proveedor | Gestión de metadatos técnicos |
| Establecer roles de gobierno (oficial, responsables de dato) y registrar decisiones | Gestión de responsables de datos; Gestión de trazabilidad y evidencia de decisiones |
 
### Cuellos de botella externos
 
La vista deja ver tres dependencias que no controla el equipo: el proveedor de S2, que debe entregar la estructura; la disponibilidad de Jurídica para validar clasificaciones; y la designación pendiente del oficial de protección de datos y de los responsables de dato.
 
---
 
## 1.4 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan
 
![V3a - Cadena de valor del negocio](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3a%20-%20Cadena%20de%20valor%20del%20negocio.png)
 
### Qué muestra
 
La cadena de valor primaria "Intermediación inmobiliaria (de la captación al cierre)" con seis etapas encadenadas por Triggering, tres eventos de negocio que disparan etapas y, bajo cada etapa, las capacidades que la habilitan (Serving). En la franja superior aparece la cadena de soporte "Gobierno de datos personales" y las tres capacidades transversales que sirven a toda la cadena.
 
### Cómo se lee
 
Las etapas van de izquierda a derecha. Las cajas bajo cada etapa son capacidades de la V2 que sirven a esa etapa; una misma capacidad puede aparecer en varias columnas porque sirve a más de una etapa. Cada evento se une con su etapa mediante una Association rotulada "dispara la etapa".
 
### Etapas de la cadena de valor
 
| Etapa | Qué ocurre | Capacidades que la habilitan |
|---|---|---|
| Captar y publicar | Captación del propietario con contrato de corretaje, fotos y publicación en web y portales | Captación de propietarios e inmuebles; Gestión de la información del inmueble; Valoración y fijación de precios de inmuebles; Gestión de contenidos de inmuebles; Gestión de canales web y portales |
| Atender interesados | Recepción por web, portales, teléfono y WhatsApp y registro en el CRM | Gestión de interesados; Atención de visitas y negociación; Gestión del conocimiento del cliente; Gestión de canales web y portales |
| Evaluar y negociar | Estudio y aprobación del candidato (arriendo) u oferta y negociación con revisión jurídica (venta) | Evaluación de candidatos a arrendamiento; Atención de visitas y negociación; Asesoría y revisión legal |
| Formalizar | Firma del contrato de arriendo, o promesa de compraventa y escritura | Gestión de contratos de arrendamiento; Gestión de la venta de inmuebles; Asesoría y revisión legal |
| Administrar la vigencia | Solo arriendo: cobro mensual, pago al propietario, reparaciones, reajuste anual y renovación | Gestión de contratos de arrendamiento; recaudo y cartera; pagos a propietarios; novedades y mantenimiento; contable y de facturación; tesorería; cobro jurídico; peticiones, quejas y reclamos |
| Cerrar | Acta de entrega y devolución de depósitos (arriendo) o liquidación de comisión (venta) | Renovación y cierre de contratos; Entrega de inmuebles y devolución de depósitos; Gestión de comisiones; Gestión contable y de facturación |
 
El arriendo recorre las seis etapas. La venta omite "Administrar la vigencia" y termina en "Cerrar" con la liquidación de la comisión.
 
### Eventos
 
| Evento | Etapa que dispara | Regla o efecto |
|---|---|---|
| Candidato aprobado | Formalizar | Un arriendo no se firma sin estudio aprobado |
| Contrato de arrendamiento firmado | Administrar la vigencia | Nacen los datos de las partes, que hoy se digitan de nuevo en S1 |
| Vencimiento o terminación del contrato | Cerrar | Da paso al acta de entrega y a la devolución de depósitos |
 
### Capacidades transversales y cadena de soporte
 
Tres capacidades sirven a toda la cadena de intermediación: Gestión de Datos e Información, Gestión de la protección de datos personales y Gestión de Tecnología de la Información. La cadena "Gobierno de datos personales (del dato desconocido al dato gobernado)" también se relaciona con la primaria mediante Serving: gobierna los datos que nacen en cada etapa de la intermediación (identificación y contacto del propietario, estudio financiero del candidato, contrato, pagos y mora, acta y saldos).
 
### Justificación
 
Esta vista ubica la solución dentro del negocio: la aplicación no es una etapa de la cadena primaria, sino una cadena de soporte cuyo insumo son los datos que producen esas etapas. Las capacidades de la V2 quedan ancladas a etapas concretas, así se puede responder en qué momento del negocio cada capacidad aporta valor.
 
---
 
## 1.5 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores
 
![V3b - Proceso E2E de gobierno de datos](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3b%20-%20Proceso%20E2E%20de%20gobierno%20de%20datos.png)
 
### Qué muestra
 
De arriba hacia abajo: la cadena de valor de gobierno de datos con cinco etapas, cuatro eventos que disparan el proceso, el proceso E2E "Gobierno E2E del dato personal (de la fuente al reporte)" con nueve pasos, y los actores y roles asignados a cada paso. Cada etapa de la cadena queda sobre los pasos que la realizan. El color de cada paso indica el apoyo de la solución.
 
### Cómo se lee
 
Los pasos del proceso se encadenan con Triggering de izquierda a derecha. Hay un ciclo de mantenimiento: "Controlar cambios de estructura" vuelve a disparar "Importar metadatos técnicos". Cada línea de la franja inferior es una Assignment de un actor o rol a un paso. La leyenda de colores está en la parte inferior de la vista.
 
### Pasos del proceso y apoyo de la solución
 
| Paso | Qué hace | Apoyo de la solución | Etapa de la cadena |
|---|---|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | TI y proveedores habilitan acceso de solo lectura a S1, S3, S4 y, vía proveedor, S2 | No (lo hace TI o el proveedor) | Conocer los datos |
| P2 Importar metadatos técnicos | Trae tipo de dato y longitud desde los diccionarios de los motores | Sí | Conocer los datos |
| P3 Inventariar atributos de negocio | Consolida los atributos distintos y suma los de fuentes sin motor (hojas, carpetas) | Sí | Conocer los datos |
| P4 Describir atributos (definición, responsable, calidad y validación) | Registra metadatos de negocio por atributo | Sí | Describir los datos |
| P5 Clasificar atributos por categoría legal | Asigna categoría con criterio y justificación | Sí | Clasificar los datos |
| P6 Validar jurídicamente la clasificación | Jurídica revisa y deja constancia; la herramienta registra | Parcial | Clasificar los datos |
| P7 Publicar diccionario de datos y catálogo de términos | Integra lo técnico y lo de negocio y asocia términos a atributos | Sí | Publicar y mantener el diccionario |
| P8 Controlar cambios de estructura | Detecta cambios entre importaciones y deja evidencia | Parcial | Publicar y mantener el diccionario |
| P9 Consultar y reportar (titulares, seguridad, SIC) | Ubica datos de una persona, informa atributos sensibles y prepara el reporte | Parcial | Usar y rendir cuentas |
 
Resumen: cinco pasos con apoyo de la solución (P2, P3, P4, P5 y P7), tres con apoyo parcial (P6, P8 y P9) y uno sin apoyo (P1). El proceso completo está marcado como "Sí (transversal)".
 
### Eventos que disparan el proceso
 
| Evento | Paso que dispara | Descripción |
|---|---|---|
| Nueva fuente de datos incorporada | P1 | Se incorpora un sistema o fuente que maneja datos de personas |
| Cambio de estructura en una base de datos | P8 | Un proveedor o TI modifica tablas o columnas, hoy sin aviso formal |
| Reclamo o solicitud de un titular | P9 | Una persona consulta, corrige o pide suprimir sus datos |
| Requerimiento de la SIC | P9 | La autoridad solicita información; la obligación concreta está por verificar |
 
### Actores y roles por paso
 
| Actor o rol | Tipo | Pasos asignados |
|---|---|---|
| Gerente general | Actor | Proceso E2E completo (aprueba políticas y asigna recursos) |
| Coordinador de TI | Actor | P1, P2, P3, P8 |
| Proveedor del CRM (S2) | Actor externo | P1 |
| Jefa de administración de arrendamientos | Actor | P3 |
| Director comercial | Actor | P3 |
| Responsable de dato de área | Rol por designar | P4 |
| Oficial de protección de datos | Rol por designar | P5, P7, P9 |
| Abogada interna | Actor | P5, P6 |
| Abogado externo | Actor | P6 |
| Servicio al cliente | Actor | P9 |
 
### Justificación
 
Esta vista es el punto de partida de la Fase 2: el proceso E2E es el que se descompone después en servicios por capas. Identificar el apoyo de la solución paso por paso evita sobreprometer: P1 es una tarea de TI y del proveedor, y P6, P8 y P9 dependen de decisiones o ejecuciones humanas, por lo que la herramienta solo registra o prepara.
 
---
 
## 1.6 V3C: proceso E2E y capacidades que realiza
 
![V3c - Proceso E2E y capacidades](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/192e266f42374043f8ea87a2868c98509428f996/mapa%20de%20capacidades%20y%20procesos/V3c%20-%20Proceso%20E2E%20y%20capacidades%20que%20realiza.png)
 
### Qué muestra
 
Los nueve pasos del proceso E2E arriba y, abajo, las 16 capacidades de la V2 que esos pasos realizan, unidas con 17 relaciones Realization. También conserva la secuencia de Triggering y el ciclo de mantenimiento entre P8 y P2. La vista tiene 26 conexiones.
 
### Cómo se lee
 
Una línea de Realization desde un paso hacia una capacidad significa que el paso es la forma concreta en que la organización ejerce esa capacidad. Un paso puede realizar varias capacidades, y se lee de arriba hacia abajo. Los pasos usan la leyenda de apoyo de la solución (naranja con apoyo, naranja claro apoyo parcial, gris sin apoyo) y las capacidades usan la de impacto de la V2 (naranja directo, naranja claro parcial, crema indirecto).
 
### Trazabilidad paso a capacidad
 
| Paso del proceso | Capacidades que realiza |
|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | Gestión de metadatos técnicos; Administración de accesos e identidades |
| P2 Importar metadatos técnicos | Gestión de metadatos técnicos |
| P3 Inventariar atributos de negocio | Inventario de atributos de negocio |
| P4 Describir atributos | Gestión de metadatos de negocio; Gestión de responsables de datos; Definición de políticas y reglas de calidad y validación |
| P5 Clasificar atributos por categoría legal | Clasificación de atributos por categoría legal |
| P6 Validar jurídicamente la clasificación | Validación jurídica de la clasificación; Resolución de conflictos y decisiones sobre datos |
| P7 Publicar diccionario de datos y catálogo de términos | Gestión del diccionario de datos; Gestión del catálogo de términos de negocio |
| P8 Controlar cambios de estructura | Gestión de cambios de estructura de datos; Gestión de trazabilidad y evidencia de decisiones |
| P9 Consultar y reportar (titulares, seguridad, SIC) | Atención de derechos de los titulares; Reporte regulatorio ante la SIC; Gestión de la seguridad de la información |
 
### Qué permite concluir
 
- Los pasos P2, P3, P4, P5 y P7 realizan capacidades con impacto directo, y son el núcleo de la solución.
- P6 realiza dos capacidades de impacto parcial; P8 realiza una de impacto parcial (cambios de estructura) y una directa (trazabilidad y evidencia de decisiones); P9 realiza una de impacto parcial (reporte ante la SIC) y dos indirectas (derechos de los titulares y seguridad de la información). Esto es coherente con el apoyo parcial de estos tres pasos en la V3b.
- P1 realiza una capacidad de impacto directo (metadatos técnicos), pero el paso lo ejecuta TI o el proveedor, y una capacidad de impacto indirecto (accesos e identidades), por eso se marca sin apoyo de la solución.
- Las capacidades fuera de alcance de la V2, como Medición y monitoreo de la calidad o Gestión de Datos Maestros, no tienen un paso que las realice: es la forma de mostrar que son brechas y no parte de la solución.

---

# 2. Descomposición de servicios del proceso E2E

La V4 responde seis preguntas, una por vista:
 
| Vista | Pregunta que responde |
|---|---|
| V4a | De dónde salen los servicios |
| V4b | Cómo se descomponen y cuáles se implementan |
| V4c | Quién los realiza y qué objetos del negocio gestionan |
| V4d | Con qué sistemas externos se interopera, qué se intercambia y en qué dirección |
| V4e | Cuál es el contrato de cada servicio de actividad |
| V4f | Cuál es el contrato de cada servicio de entidad, utilidad e interoperabilidad |

## 2.1 V4a: del proceso E2E a los servicios de actividad

![4A](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4a%20-%20Del%20proceso%20E2E%20a%20los%20servicios.png)

### Qué muestra
 
Los nueve pasos del proceso E2E "Gobierno E2E del dato personal" (P1 a P9), con flujo secuencial entre ellos, y los 14 servicios de actividad (capa 3) que realizan esos pasos mediante relaciones Realization.
 
### Cómo se lee
 
El proceso va de izquierda a derecha, desde la fuente de datos hasta el reporte. Cada línea punteada que baja desde un paso es una relación Realization hacia un servicio de actividad. Un servicio de actividad es la forma en que el negocio ve lo que hace un paso: expone una capacidad con un consumidor y unas reglas propias.
 
Cada servicio queda ligado a una capacidad del mapa de la V2, de modo que la descomposición se puede rastrear desde la estrategia hasta el servicio.
 
### Trazabilidad paso, servicio y capacidad
 
| Paso del proceso | Servicios de actividad | Capacidad de la V2 que soportan |
|---|---|---|
| P1 Identificar fuentes y gestionar acceso a sus metadatos | gestión del acceso a metadatos técnicos | Gestión de metadatos técnicos |
| P2 Importar metadatos técnicos | importación de metadatos técnicos | Gestión de metadatos técnicos |
| P3 Inventariar atributos de negocio | inventario de atributos de negocio | Inventario de atributos de negocio |
| P4 Describir atributos (definición, responsable, calidad y validación) | registro de metadatos de negocio; asignación de responsables de datos | Gestión de metadatos de negocio; Gestión de responsables de datos |
| P5 Clasificar atributos por categoría legal | clasificación de atributos | Clasificación de atributos por categoría legal |
| P6 Validar jurídicamente la clasificación | validación jurídica de la clasificación | Validación jurídica de la clasificación |
| P7 Publicar diccionario de datos y catálogo de términos | publicación del diccionario de datos; gestión del catálogo de términos de negocio | Gestión del diccionario de datos; Gestión del catálogo de términos de negocio |
| P8 Controlar cambios de estructura | control de cambios de estructura | Gestión de cambios de estructura de datos |
| P9 Consultar y reportar (titulares, seguridad, SIC) | ubicación de datos personales; información para seguridad de la información; información para el reporte regulatorio; seguimiento de completitud de atributos | Atención de derechos de los titulares; Gestión de la seguridad de la información; Reporte regulatorio ante la SIC; Gobierno de Datos |
 
### Criterio de partición
 
Un paso se parte en varios servicios cuando atiende capacidades distintas, porque cada servicio resultante tiene consumidores y reglas diferentes:
 
- P4 separa metadatos de negocio (definición, calidad, expresión regular) de responsables de datos (asignación y reasignación con histórico).
- P7 separa diccionario (consulta integrada de solo lectura) de catálogo de términos (gestión de significados y conflictos).
- P9 separa cuatro consumidores: el titular que reclama, seguridad de la información, el reporte regulatorio y la gerencia que mide completitud.
Si estos servicios se agruparan en uno solo, un cambio en las reglas de uno obligaría a modificar los demás. La separación reduce el acoplamiento y mantiene cada servicio cohesivo alrededor de una sola capacidad.
 
---

## 2.2 V4b: descomposición en cuatro capas de servicio
 
![4B](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4b%20-%20Descomposici%C3%B3n%20en%20cuatro%20capas%20de%20servicio.png)
 
### Qué muestra
 
Las cuatro capas de servicio, de arriba hacia abajo, más el bloque de servicios excluidos. La capa 1 se compone de la capa 2 y la capa 2 de la capa 3 mediante Composition. Cada servicio de capa 4 queda bajo el servicio de actividad que más lo usa mediante Serving. La vista dibuja solo el uso principal; el uso completo está en la matriz de esta sección y en el modelo como relaciones Serving adicionales.
 
### Las cuatro capas
 
| Capa | Qué es | Cantidad | Se implementa |
|---|---|---|---|
| 1. Servicio E2E | El proceso E2E expuesto como un solo servicio al negocio | 1 | No, agrupa |
| 2. Servicios de proceso | Uno por etapa de la cadena de valor de gobierno de datos | 5 | No, agrupan |
| 3. Servicios de actividad | Uno por paso o capacidad del proceso | 14 | Sí, como orquestación de la capa 4 |
| 4. Servicios de entidad y utilidad | Una entidad del dominio o una utilidad transversal | 13 | Sí. Es el tamaño sobre el que se construye la aplicación |
 
### Composición completa
 
- Servicio de gobierno del dato personal (capa 1)
  - Servicio de conocimiento de los datos (capa 2): gestión del acceso a metadatos técnicos; importación de metadatos técnicos; inventario de atributos de negocio
  - Servicio de descripción de los datos: registro de metadatos de negocio; asignación de responsables de datos
  - Servicio de clasificación de los datos: clasificación de atributos; validación jurídica de la clasificación
  - Servicio de publicación y mantenimiento del diccionario: publicación del diccionario de datos; gestión del catálogo de términos de negocio; control de cambios de estructura
  - Servicio de uso y rendición de cuentas: ubicación de datos personales; información para seguridad de la información; información para el reporte regulatorio; seguimiento de completitud de atributos

### Criterio de tamaño adecuado para un servicio de capa 4
 
Un servicio de capa 4 debe cumplir estas condiciones:
 
1. Gestiona una sola entidad del dominio o una sola utilidad.
2. Tiene entre 3 y 6 operaciones.
3. No depende de otro servicio de su misma capa.
4. Se explica con una frase del negocio.
Reglas de ajuste: si dos entidades cambian siempre juntas se unen en un servicio; si una entidad tiene dos dueños distintos se divide.
 
### Por qué la capa 4 se define por entidades
 
Las entidades son lo más estable del dominio: los pasos del proceso cambian, pero un atributo, una clasificación o un término siguen existiendo. Por eso la aplicación se construye sobre la capa 4 y la capa 3 solo orquesta llamadas a la capa 4. Las tres utilidades (bitácora, notificación y control de acceso) son transversales porque casi todos los servicios las usan. La bitácora es, además, la evidencia de decisiones que pide la gerencia.
 
Servicios de capa 4:
 
| Código | Servicio | Tipo |
|---|---|---|
| 4.1 | atributo de negocio | Entidad |
| 4.2 | metadato técnico | Entidad |
| 4.3 | fuente de datos | Entidad |
| 4.4 | metadato de negocio | Entidad |
| 4.5 | responsable de dato | Entidad |
| 4.6 | clasificación de atributo | Entidad |
| 4.7 | término de negocio | Entidad |
| 4.8 | diccionario de datos | Entidad |
| 4.9 | cambio de estructura | Entidad |
| 4.10 | bitácora y evidencia de decisiones | Utilidad |
| 4.11 | notificación | Utilidad |
| 4.12 | control de acceso por rol | Utilidad |
| 4.13 | informes y exportación | Entidad |
 
### Matriz de uso: capa 3 por capa 4
 
Una "X" indica que el servicio de actividad (fila) usa el servicio de capa 4 (columna).
 
| Capa 3 \ Capa 4 | 4.1 | 4.2 | 4.3 | 4.4 | 4.5 | 4.6 | 4.7 | 4.8 | 4.9 | 4.10 | 4.11 | 4.12 | 4.13 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| gestión del acceso a metadatos técnicos | | | X | | | | | | | X | | X | |
| importación de metadatos técnicos | | X | X | | | | | | X | X | | | |
| inventario de atributos de negocio | X | | X | | | | | | | X | | | |
| registro de metadatos de negocio | X | | | X | | | | | | X | X | | |
| asignación de responsables de datos | X | | | | X | | | | | X | | | |
| clasificación de atributos | X | | | | | X | | | | X | | | |
| validación jurídica de la clasificación | | | | | | X | | | | X | X | | |
| publicación del diccionario de datos | X | X | | X | | X | | X | | | | | |
| gestión del catálogo de términos de negocio | X | | | | | | X | | | X | | | |
| control de cambios de estructura | | X | | | | | | | X | X | X | | |
| ubicación de datos personales | | | X | | | X | | X | | | | | |
| información para seguridad de la información | | | | | X | X | | X | X | | | | |
| información para el reporte regulatorio | | | X | | | X | | X | | | | | X |
| seguimiento de completitud de atributos | X | | | X | X | X | | | | | X | | |
 
### Servicios excluidos
 
Los 16 servicios en gris de la vista son decisiones de alcance, cada una con su justificación:
 
| Código | Servicio excluido | Justificación |
|---|---|---|
| Z1 | Descubrimiento automático de datos personales (lectura de datos) | El negocio prefiere que la herramienta no lea datos de personas para no abrir otro punto de exposición de cédulas e ingresos (Bloque 8). La clasificación es manual. |
| Z2 | Publicación de definiciones y clasificación hacia los sistemas fuente | Nadie lo pide, no hay forma de recibirlo y los proveedores cobrarían por ello (Bloque 8). |
| Z3 | Modificación de estructuras o datos en los sistemas fuente | El negocio no espera que la herramienta cambie las bases de datos. |
| Z4 | Medición y monitoreo de la calidad de los datos | Exige leer datos; solo se pide definir políticas y expresiones regulares. Es una brecha frente a la expectativa de la gerencia. |
| Z5 | Depuración y deduplicación de datos | Fuera de alcance; exige datos personales. El 8 % de propietarios duplicados queda sin atender. |
| Z6 | Gestión de datos maestros | Fuera de alcance. Resolvería la duplicidad, pero es otro proyecto. |
| Z7 | Gestión de autorizaciones de titulares | Fuera de los cinco puntos del alcance; hoy son formatos dispersos. Candidato a otra solución. |
| Z8 | Trámite de reclamos de titulares | La solución solo informa dónde están los datos. El trámite sigue en Jurídica y Servicio al cliente. |
| Z9 | Gestión de incidentes con datos personales | Fuera de alcance; no hay procedimiento definido. |
| Z10 | Gestión de encargados del tratamiento (proveedores) | Fuera de alcance; las cláusulas de datos con proveedores siguen pendientes con la gerente. |
| Z11 | Retención y supresión de datos | Fuera de alcance; consumirá el diccionario cuando exista. |
| Z12 | Transmisión del reporte a la SIC | Formato, canal y plazos por verificar, y la obligación misma es incierta. Se exporta el informe y Jurídica lo presenta. |
| Z13 | Linaje de datos | No fue solicitado y las hojas y carpetas no tienen catálogo técnico que lo permita. |
| Z14 | Aprobación de políticas de datos | Decide la gerente fuera de la herramienta; el diccionario solo referencia las vigentes. |
| Z15 | Directorio e identidad corporativa (SSO) | La empresa no tiene uno; los roles se manejan localmente en el servicio de control de acceso. |
| Z16 | Integración con portales, aseguradora, banco, notarías y centrales de riesgo | Reciben datos del negocio pero no intercambian información con la herramienta. Extensión futura: registrarlos como destinatarios del atributo. |
 
---

## 2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos
 
![4C](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4c%20-%20Servicios%20de%20entidad%20y%20utilidad.png)
 
### Qué muestra
 
Para cada servicio de capa 4: los roles y actores asignados (Assignment) a la función de negocio que lo realiza (Realization) y los objetos pasivos que gestiona (Access). En la parte inferior de la vista está el modelo de objetos pasivos.
 
### Cómo se lee
 
La cadena de elementos para cada servicio es:
 
Rol o actor, Assignment, Función de negocio, Realization, Servicio de negocio, Access, Objeto pasivo.
 
Se usa una función por servicio para dejar claro quién responde por cada entidad.
 
### Asignaciones
 
| Servicio | Función que lo realiza | Roles y actores asignados | Objetos pasivos |
|---|---|---|---|
| atributo de negocio | Administración de atributos de negocio | Administrador del diccionario de datos | Atributo de negocio |
| metadato técnico | Administración de metadatos técnicos | Administrador del diccionario de datos; Coordinador de TI | Metadato técnico |
| fuente de datos | Administración de fuentes de datos y accesos | Administrador del diccionario de datos; Coordinador de TI | Fuente de datos; Autorización de acceso a metadatos |
| metadato de negocio | Administración de metadatos de negocio | Responsable de dato de área | Metadato de negocio |
| responsable de dato | Administración de responsables de datos | Administrador del diccionario de datos; Gerente general | Responsabilidad sobre el dato |
| clasificación de atributo | Administración de la clasificación de datos | Oficial de protección de datos; Abogada interna | Clasificación del atributo |
| término de negocio | Administración del catálogo de términos | Responsable de dato de área; Administrador del diccionario de datos | Término de negocio |
| diccionario de datos | Mantenimiento del diccionario integrado | Administrador del diccionario de datos | Diccionario de datos |
| cambio de estructura | Detección y registro de cambios de estructura | Coordinador de TI; Administrador del diccionario de datos | Cambio de estructura |
| bitácora y evidencia de decisiones | Conservación de evidencia de decisiones | Oficial de protección de datos | Evidencia de decisión |
| notificación | Gestión de avisos | Administrador del diccionario de datos | Aviso |
| control de acceso por rol | Administración de permisos | Administrador del diccionario de datos | Permiso de acceso |
| informes y exportación | Elaboración de informes | Oficial de protección de datos; Abogada interna | Informe regulatorio |
 
### Modelo de objetos pasivos
 
- El Atributo de negocio agrega su Metadato técnico, su Metadato de negocio, su Clasificación y su Responsabilidad.
- La Fuente de datos agrega los metadatos técnicos que se importan de ella.
- El Término de negocio se asocia a los atributos que describe.
- El Diccionario de datos agrega atributos y términos.

### Roles por designar
 
Tres de los roles no existen aún en la empresa y se modelaron como roles por designar, sin asignar personas:
 
- Oficial de protección de datos.
- Responsable de dato de área.
- Administrador del diccionario de datos.
La entrevista habla de "quien administre el diccionario" sin definirlo. Quién ocupe ese rol define los permisos del servicio de control de acceso por rol, y eso importa porque el diccionario revela dónde está la información sensible.
 
---

## 2.4 V4D: capa anticorrupción e interoperabilidad
 
![v4d](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4d%20-%20Capa%20anticorrupci%C3%B3n.png)

 
### Qué muestra
 
La parte superior (ENTRADA) muestra los servicios externos que alimentan la solución. La parte inferior (SALIDA) muestra los servicios de la solución que consumen el oficial, seguridad y Jurídica. Los servicios en naranja son los adaptadores de la capa anticorrupción. Los servicios en lila son los servicios externos.
 
La dirección se describe desde la solución: entrada es información que llega a la solución; salida es información que la solución entrega.
 
### Cómo se lee
 
En la entrada, el recorrido es: actor externo, servicio externo, adaptador, servicio de la solución. En la salida, el recorrido es el inverso: servicio de la solución, adaptador, consumidor.
 
### Qué es la capa anticorrupción
 
Es un patrón de DDD (Anti-Corruption Layer). Los sistemas legados, el CRM del proveedor y la SIC tienen sus propios modelos y formatos. El adaptador traduce esos modelos al modelo interno, de modo que un cambio de motor, de proveedor o del formato del reporte afecta solo al adaptador y no al dominio.
 
### Inventario de interoperabilidades
 
| # | Servicio externo | Tipo | Información | Dirección | Adaptador | Si no está disponible o no es válida |
|---|---|---|---|---|---|---|
| 1 | S1 Administración de arrendamientos (SQL Server) | Sistema legado | Estructura técnica: tablas, columnas, tipo, longitud, obligatoriedad. Autoriza la jefa de administración; ejecuta TI | Entrada | A1 | Se reintenta; se usa la última versión conocida y se anota su fecha |
| 2 | S3 Contable (SQL Server) | Sistema legado | Misma estructura. Autoriza el contador; ejecuta TI | Entrada | A1 | Igual |
| 3 | S4 Sitio web (MySQL) | Sistema legado | Misma estructura. Autoriza el analista de mercadeo con la gerente; ejecuta TI | Entrada | A1 | Igual |
| 4 | S2 CRM comercial (PostgreSQL) | Sistema de proveedor | Misma estructura, entregada por el proveedor. Autoriza el director comercial con la gerente | Entrada | A2 | El negocio acepta demoras de días; la fuente se muestra desactualizada |
| 5 | Proveedores de S1 a S4 | Proveedor | Aviso de cambios de estructura | Entrada | A3 | No hay aviso garantizado; la detección por diferencias entre importaciones lo compensa |
| 6 | Hojas, carpetas, correo y WhatsApp | Fuente no estructurada | Inventario manual: ubicación, tipo de dato personal, responsable | Entrada (manual) | A4 | Queda como "área sin cubrir" |
| 7 | Áreas de negocio y responsables de dato | Proceso interno | Definiciones, políticas de calidad, expresiones regulares y términos | Entrada (por pantalla) | Sin adaptador | Atributo incompleto, visible al oficial |
| 8 | Jurídica (abogada interna y abogado externo) | Proceso interno | Validación de la clasificación y su justificación | Entrada (por pantalla) | Sin adaptador | Clasificación "en revisión" con la opinión de cada parte |
| 9 | Oficial de protección de datos | Proceso interno | Atributos personales, categoría, ubicación, responsable, pendientes y cambios recientes | Salida | A5 | Se indica qué falta |
| 10 | Seguridad de la información (hoy, el coordinador de TI) | Proceso interno | Atributos sensibles y privados, sistemas de mayor riesgo, cambios que los afecten | Salida | A6 | Se indica qué falta |
| 11 | Superintendencia de Industria y Comercio (vía Jurídica) | Entidad regulatoria | Informe: bases, finalidad, responsable y encargado, tipos de datos, clasificación, medidas de seguridad, titulares aproximados. Formato por verificar | Salida (la presenta Jurídica a mano) | A7 | Información no validada: no se presenta como definitiva |
| 12 | Correo electrónico | Canal | Avisos por rol, sin datos de personas | Salida | A8 | El aviso queda pendiente en la aplicación |
| 13 | Portales, correo masivo, aseguradora, banco, notarías, centrales de riesgo | Terceros receptores de datos | Reciben datos del negocio, no de la herramienta | Sin intercambio | No aplica | Excluido (Z16); extensión futura: registrarlos como destinatarios del atributo |
| 14 | Dispositivos | No aplica | Ninguno identificado en la entrevista (la huella de la cédula es un dato, no un dispositivo) | No aplica | No aplica | No aplica |
 
### Adaptadores
 
| Adaptador | Dirección | Sirve a | Qué traduce |
|---|---|---|---|
| A1 adaptación de metadatos técnicos de motores relacionales | Entrada | importación de metadatos técnicos | Traduce el catálogo de SQL Server y MySQL (S1, S3, S4) al modelo interno de metadato técnico y normaliza tipos entre motores |
| A2 adaptación de metadatos técnicos del CRM (S2) | Entrada | importación de metadatos técnicos | Traduce lo que entregue el proveedor del CRM (formato por acordar) al modelo interno; tolera demoras de días |
| A3 recepción de avisos de cambio de los proveedores | Entrada | control de cambios de estructura | Recibe y registra los avisos de cambio de estructura; no se confía en que lleguen |
| A4 carga del inventario de fuentes no estructuradas | Entrada | inventario de atributos de negocio | Recibe el inventario manual de hojas, carpetas, correo y WhatsApp, que no tienen catálogo técnico |
| A5 entrega de información al oficial de protección de datos | Salida | ubicación de datos personales | Presenta atributos personales, categoría, ubicación, responsable y faltantes en la vista que usa el oficial |
| A6 entrega de información a seguridad de la información | Salida | información para seguridad de la información | Presenta atributos sensibles y privados, sistemas de riesgo y cambios de riesgo en la vista de seguridad |
| A7 generación del informe para la SIC | Salida | información para el reporte regulatorio | Da forma de informe a la información regulatoria; el formato exigido está por verificar |
| A8 notificación por correo electrónico | Salida | notificación | Convierte un aviso interno en un correo sin datos de personas |
 
### Restricciones de diseño
 
- Todos los intercambios de entrada son de solo estructura: la herramienta no lee datos de personas, como pidieron la gerente y la abogada.
- Las áreas de negocio y Jurídica interactúan por pantalla con la propia aplicación, por eso no necesitan adaptador.
- La SIC no recibe nada directamente de la solución: se exporta el informe y Jurídica lo presenta de forma manual.
- Ante una fuente caída se trabaja con la última versión conocida y se muestra su fecha, nunca se bloquea el diccionario.

---

## 2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)
 
![V4E](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4e%20-%20Contract%20First%20contratos%20de%20los%20servicios%20capa%203.png)
 
### Qué muestra
 
Cada servicio de capa 3, su contrato (elemento Contract de ArchiMate, relación de especificación) y los objetos pasivos que el contrato agrega (Aggregation).
 
### Qué significa Contract First
 
El contrato se diseña antes que la aplicación. Fija lo que el consumidor puede pedir y lo que el servicio promete. Cada contrato define cinco campos, que están guardados como propiedades del elemento Contract en Archi:
 
| Campo | Contenido |
|---|---|
| Operaciones | Firmas de las operaciones que expone el servicio |
| Entrada | Datos que debe recibir |
| Salida | Resultado que entrega |
| Reglas de negocio | Condiciones que el servicio garantiza o exige |
| Excepciones | Qué pasa cuando falta información o algo falla |
 
Las capas 1 y 2 no tienen contrato propio porque solo agrupan.
 
### Regla común de excepciones
 
Los contratos de capa 3 son los que ven los usuarios del negocio, por eso sus excepciones siguen la regla de la gerente: cuando la información falta o es dudosa, el sistema indica qué falta y no presenta un dato dudoso como correcto.
 
### Ejemplo completo: 3.6 Servicio de clasificación de atributos
 
| Campo | Contenido |
|---|---|
| Operaciones | proponerClasificacion(atributo, categoría, criterio, justificación); marcarEnRevision(atributo, opinión); consultarPendientes() |
| Entrada | atributo, categoría, criterio, justificación, fuente normativa |
| Salida | clasificación en estado propuesta o en revisión |
| Reglas de negocio | Categorías según el marco normativo (por verificar). Si hay discusión queda "en revisión" con la opinión de cada parte |
| Excepciones | Sin justificación no se guarda |
 
### Resumen de los 14 contratos de capa 3
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| 3.1 | gestión del acceso a metadatos técnicos | solicitarAcceso(fuente); registrarAutorizacion(fuente, autorizador); registrarCuentaSoloLectura(fuente); revocarAcceso(fuente) | Solo lectura, cuenta propia. Sin autorización no se habilita la importación |
| 3.2 | importación de metadatos técnicos | importarEstructura(fuente); reintentarImportacion(fuente); consultarEstadoImportacion(fuente) | Solo estructura. Fuente no disponible: se reintenta y se usa la última versión conocida |
| 3.3 | inventario de atributos de negocio | inventariarAtributos(fuente); registrarAtributoManual(datos); vincularColumna(atributo, columna) | Columnas equivalentes se consolidan en un atributo. Fuente sin inventario queda "sin cubrir" |
| 3.4 | registro de metadatos de negocio | registrarMetadatosNegocio(atributo, definición, calidad, regex); solicitarCompletar(atributo) | La regex debe ser válida y no se ejecuta contra datos. Dato faltante: atributo incompleto |
| 3.5 | asignación de responsables de datos | asignarResponsable(atributo, responsable); reasignarResponsable(atributo, responsable); listarSinResponsable() | Todo atributo con datos personales debe tener responsable. La reasignación conserva histórico |
| 3.6 | clasificación de atributos | proponerClasificacion; marcarEnRevision; consultarPendientes | Sin justificación no se guarda |
| 3.7 | validación jurídica de la clasificación | validar(clasificación, justificación); objetar(clasificación, motivo); consultarPendientes() | La valida solo Jurídica o el oficial. Sin validar no se presenta como definitiva |
| 3.8 | publicación del diccionario de datos | publicarVersion(); consultarVersionPublicada(); compararVersiones(a, b) | Publica todo, pero marca atributos incompletos y la antigüedad de la información técnica |
| 3.9 | gestión del catálogo de términos de negocio | proponerTermino(término, significado); aprobarTermino(término); asociarAtributos(término, atributos); resolverConflicto(término) | Dos significados se registran ambos y se marca el conflicto. Término sin atributos: advertencia |
| 3.10 | control de cambios de estructura | detectarCambios(fuente); notificarCambio(cambio); registrarImpacto(cambio) | Un cambio sobre un atributo sensible se marca de riesgo y no altera la clasificación por sí solo |
| 3.11 | ubicación de datos personales | listarAtributosPersonales(filtro); ubicarAtributo(atributo); sistemasConDatosDeTipoDeTitular(tipo) | Responde por atributo y tipo de titular, no por persona |
| 3.12 | información para seguridad de la información | listarAtributosSensibles(); listarSistemasDeRiesgo(); listarCambiosDeRiesgo(); listarSinResponsable() | Solo atributos sensibles y privados, sin datos de personas |
| 3.13 | información para el reporte regulatorio | prepararInforme(parámetros); validarCompletitud(informe); exportarInforme(informe, formato) | No se transmite: lo presenta Jurídica. Información no validada no se presenta como definitiva |
| 3.14 | seguimiento de completitud de atributos | calcularCobertura(); listarIncompletos(); listarSinClasificar() | El cálculo es sobre atributos, no sobre datos. Sin atributos inventariados: cobertura no calculable |
 
---

## 2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad
 
![V4F](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/bd823eea7ac9f57cca900c48089c03c943edf38e/descomposicion%20de%20servicios/V4f%20-%20Contract%20First%20contratos%20entidad%2C%20utilidad%20e%20interoperabilidad.png)
 
### Qué muestra
 
Los contratos de los 13 servicios de capa 4 y de los 8 adaptadores de la capa anticorrupción, con los objetos pasivos que agregan. Los servicios de entidad y utilidad se muestran en amarillo claro y los adaptadores en naranja.
 
### Por qué son el nivel de construcción
 
Estos contratos son los que sirven de base a la capa de aplicaciones: cada uno corresponde a una entidad, una utilidad o un adaptador. Son pequeños e independientes del proceso, por eso se reutilizan desde varios servicios de actividad. Los de los adaptadores dejan por escrito qué formato se espera de cada sistema externo y qué ocurre si no llega. Las operaciones están escritas como firmas del negocio y se refinan al pasar a la capa de aplicaciones.
 
### Ejemplo completo de entidad: 4.6 Servicio de clasificación de atributo
 
| Campo | Contenido |
|---|---|
| Operaciones | proponer(atributo, categoría, criterio, justificación); registrarValidacion(id, decisión); marcarEnRevision(id, opinión); consultar(atributo); listarPendientes() |
| Entrada | atributo, categoría (pública, semiprivada, privada, sensible, no personal), criterio, justificación, fuente normativa, autor |
| Salida | clasificación con estado (propuesta, en revisión, validada), versión y fecha |
| Reglas de negocio | Se propone añadir la categoría "no personal". La valida solo Jurídica u oficial. Reclasificar crea versión |
| Excepciones | Sin justificación no se guarda; sin validar no es definitiva |
 
### Ejemplo completo de adaptador: A1 Servicio de adaptación de metadatos técnicos de motores relacionales
 
| Campo | Contenido |
|---|---|
| Operaciones | leerCatalogo(motor, conexión); traducirAModeloInterno(catálogo) |
| Entrada | Catálogo del sistema del motor: tablas, columnas, tipo, longitud, obligatoriedad, relaciones |
| Salida | Metadatos técnicos en el modelo interno, con tipos normalizados |
| Reglas de negocio | Solo el catálogo del sistema, nunca tablas de negocio. Cuenta propia de solo lectura |
| Excepciones | Fallo de conexión: se reintenta y la fuente queda "desactualizada" |
 
### Resumen de los contratos de capa 4
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| 4.1 | atributo de negocio | crearAtributo(datos); consultarAtributo(id); modificarAtributo(id, datos); listarAtributos(filtro); obtenerVersiones(id) | Un atributo puede mapearse a varias columnas. Cada cambio crea versión. Es "incompleto" si falta definición, responsable o clasificación |
| 4.2 | metadato técnico | registrarEstructura(fuente, versión, columnas); consultarMetadatoTecnico(atributo); listarVersiones(fuente) | Solo estructura. Se conserva la versión anterior y se muestra la fecha |
| 4.3 | fuente de datos | registrarFuente(datos); consultarFuente(id); registrarAutorizacion(fuente, autorizador); listarFuentes(filtro) | Toda fuente tiene autorizador y constancia de acceso. La no inventariada es "área sin cubrir" |
| 4.4 | metadato de negocio | registrarMetadatoNegocio(atributo, datos); consultar(atributo); modificar(atributo, datos); validarExpresion(regex) | Definición obligatoria. La regex se valida sintácticamente y no se ejecuta contra datos |
| 4.5 | responsable de dato | asignar(atributo, responsable); reasignar(atributo, responsable); consultar(atributo); listarSinResponsable() | Todo atributo con datos personales requiere responsable. Sin responsable: alerta al oficial |
| 4.6 | clasificación de atributo | proponer; registrarValidacion; marcarEnRevision; consultar; listarPendientes | Ver ejemplo completo arriba |
| 4.7 | término de negocio | crearTermino(datos); modificarTermino(id, datos); asociarAtributo(término, atributo); desasociarAtributo(término, atributo); marcarConflicto(término); consultar(término) | Dos significados se registran ambos y se marca el conflicto |
| 4.8 | diccionario de datos | consultarDiccionario(filtros); obtenerFichaAtributo(id); listarIncompletos(); buscarPorTermino(término) | Solo lectura. Siempre indica qué falta y qué tan antigua es la información técnica |
| 4.9 | cambio de estructura | registrarDiferencias(fuente, versiónA, versiónB); consultarCambios(fuente, rango); marcarRevisado(cambio) | Un cambio sobre un atributo sensible se marca de riesgo. No modifica clasificaciones |
| 4.10 | bitácora y evidencia de decisiones | registrarEvento(actor, acción, objeto, antes, después); consultarEventos(filtros); exportarEvidencia(filtros) | Evento inmutable. Si no se puede registrar, la operación de origen no se confirma |
| 4.11 | notificación | programarAviso(tipo, rol, referencia); listarAvisos(rol); marcarAtendido(aviso) | Los avisos van por rol y nunca incluyen datos de personas |
| 4.12 | control de acceso por rol | asignarRol(usuario, rol); verificarPermiso(usuario, operación); listarPermisos(rol) | Roles: administrador, responsable de dato, oficial, jurídica, TI, consulta. Sin permiso: se deniega y se registra en la bitácora |
| 4.13 | informes y exportación | generarInforme(tipo, parámetros); exportar(informe, formato) | Marca qué falta o no está validado. No contiene datos de personas |
 
### Resumen de los contratos de adaptadores
 
| Código | Servicio | Operaciones | Regla o excepción central |
|---|---|---|---|
| A1 | metadatos técnicos de motores relacionales | leerCatalogo(motor, conexión); traducirAModeloInterno(catálogo) | Ver ejemplo completo arriba |
| A2 | metadatos técnicos del CRM (S2) | recibirEntregaEstructura(entrega); traducirAModeloInterno(entrega) | La empresa no tiene credenciales propias; se acepta demora de días. Sin entrega: se conserva la última versión con aviso |
| A3 | avisos de cambio de los proveedores | recibirAviso(aviso); registrarAviso(aviso, fuente) | No se confía en que el aviso llegue. Aviso sin fuente identificable: queda pendiente de clasificar |
| A4 | inventario de fuentes no estructuradas | validarPlantilla(archivo); cargarInventario(archivo) | Carga manual guiada; no se cargan archivos con datos de personas. Plantilla inválida: se rechaza indicando las filas |
| A5 | información al oficial de protección de datos | consultarAtributosPersonales(filtro); consultarPendientes(); consultarCambiosRecientes(rango) | Solo lectura y sin datos de personas. Muestra qué falta |
| A6 | información a seguridad de la información | obtenerAtributosSensibles(); obtenerSistemasDeRiesgo(); obtenerCambiosDeRiesgo() | Solo atributos sensibles y privados |
| A7 | informe para la SIC | generarInformeRegulatorio(parámetros); exportar(informe, formato) | Formato por verificar. La presenta Jurídica de forma manual |
| A8 | notificación por correo electrónico | enviarAviso(destinatario, plantilla, referencia) | El cuerpo no incluye datos de personas. Servidor no disponible: el aviso queda pendiente |
 
Total: 14 contratos de actividad, 13 de entidad y utilidad y 8 de adaptadores, es decir, 35 contratos. Son un primer borrador de operaciones y reglas que se refina en la capa de aplicaciones.
 
---

# 3. Dominios y lenguaje ubicuo

La Fase 3 responde tres preguntas, repartidas entre las vistas así:

| Vista | Pregunta que responde |
|---|---|
| V5 | En qué partes se divide el problema del dominio y cuáles son el núcleo de la solución |
| V7 | Cómo se llaman las cosas del proceso y su entorno, y a qué subdominio o grupo pertenece cada término |
| V7b | Qué términos significan cosas distintas según el contexto, y cuáles son esos significados |

Elementos de ArchiMate que se agregan en esta fase:

| Elemento | Capa | Uso en este modelo |
|---|---|---|
| Grouping | Otros | El dominio, cada subdominio y los dos grupos de lenguaje que no pertenecen a un subdominio |
| Business Object | Negocio | Conceptos que maneja cada subdominio, los mismos de la V4c |
| Representation | Negocio | Cada término del glosario |
| Meaning | Motivación | Cada significado de un término en un contexto |

Relaciones nuevas: **Serving** entre subdominios ("A sirve a B" se lee "B depende de A") y **Association** entre un significado y su término. En esta sección, P1 a P9 son los pasos del proceso E2E (V3b) y R1 a R10 los requisitos de la V1.

---

## Análisis del ecosistema

<!-- Base para reescribir con palabras propias. Cada afirmación lleva su bloque de la entrevista: verificar contra el registro. -->

Este análisis describe el entorno en que operará la solución, siguiendo el primer paso del método de extracción de dominios: entender la estructura organizacional del problema para tener una visión general del entorno. Ninguna área de nuestro caso tiene el gobierno de los datos como función: varias personas participan en identificar, documentar y controlar los datos, pero ninguna lo tiene asignado y cada una hace una parte por costumbre (Bloque 3). Por eso las personas se agrupan según su relación con los datos. Los grupos se solapan: la abogada interna juzga lo legal y a la vez sería quien consulte la información (Bloque 8), y la gerente general decide y a la vez espera recibir un listado de datos personales clasificado (Bloque 6).

**Los sistemas.** Los datos están en cinco fuentes, más canales informales y portales. S1 es un software de administración de arrendamientos, comprado y alojado en servidor propio (SQL Server). S2 es un CRM comercial hecho a la medida por un proveedor y alojado en la nube (PostgreSQL). S3 es un sistema contable comercial (SQL Server, otra instancia). S4 es el sitio web (MySQL). S5 son las hojas de cálculo y las carpetas compartidas, sin motor de base de datos (Bloque 1). Fuera de las cinco están el correo y el WhatsApp de los asesores, que guardan cédulas, certificados y datos de contacto (Bloque 8), y los portales inmobiliarios, no controlados por la empresa (Bloque 1). Los portales actúan en dos sentidos: reciben las fichas de los inmuebles y envían interesados por correo, que se copian a mano a S2 (Bloques 1 y 8). La conexión entre los sistemas es mínima: S2 publica fichas en S4 y en los portales, el asesor vuelve a digitar en S1 los datos del contrato, y S1 envía a S3 un archivo plano cada noche (Bloque 1).

**Quienes generan y usan los datos.** El director comercial y los asesores veteranos conocen lo de captación e interesados. La jefa de administración y la analista más antigua conocen lo de contratos y cánones, y el contador lo contable. Ese conocimiento está repartido, sin documentar, y se pierde si la persona se va (Bloque 3). Los asesores recogen más datos que nadie y los guardan en sus celulares, y Mercadeo decide qué se publica y a quién se envía publicidad sin consultar a nadie. Ambos figuran entre quienes hoy no participan en el gobierno de los datos (Bloque 3). Cada área nombra distinto lo mismo: "activo" es un interesado con seguimiento abierto para Comercial y un contrato vigente para Administración (Bloque 2), y una misma columna, VR_CAN, la definen de tres formas la analista, el contador y el proveedor (Bloque 5).

**Quienes administran lo técnico.** El coordinador de TI administra servidores, accesos y puede consultar los diccionarios de S1, S3 y S4 (Bloque 1), pero no conoce el significado de negocio de muchos campos (Bloque 3). La estructura de S2 solo se obtiene mediante un pedido al proveedor (Bloque 1), que responde en días (Bloque 8). Los proveedores cambian las estructuras a pedido de cada área: en S3 TI casi nunca se entera, y en S2 el aviso llega solo cuando el proveedor quiere (Bloque 5). El proveedor del CRM guarda datos de la empresa y no hay un documento que defina sus responsabilidades sobre ellos (Bloque 3). En general los proveedores pueden ver datos (Bloque 8). Las hojas, las carpetas, el correo y WhatsApp no tienen diccionario, y ahí vive una parte importante de los datos delicados (Bloque 1).

**Quienes juzgan lo legal.** La abogada interna da su opinión por correo o de palabra, sin dejar registro, y a veces interviene el abogado externo (Bloque 4). Además recibe los reclamos de las personas sobre sus datos, sin nombramiento formal (Bloque 1). Cuando el negocio cambia el uso de un dato, como el teléfono del propietario compartido con un portal, no se revisa la clasificación ni la autorización (Bloque 4).

**Quienes deberían decidir.** La gerente general aprueba las políticas y nunca ha aprobado una sobre datos (Bloques 1 y 3). Cuando dos áreas discrepan, decide caso por caso, casi siempre por correo, y la decisión no se guarda como definición oficial. Quiere que "los de sistemas decidan", pero TI responde que eso no le corresponde (Bloque 3). El oficial de protección de datos es un cargo por decidir y los responsables de dato son personas por decidir (Bloque 3). Los desacuerdos ya existen: la abogada piensa que cada área debería decidir el uso de sus datos y ella solo asesorar, el director comercial opina que "eso le toca a Jurídica" y la jefa de administración teme recibir más trabajo sin más personal (Bloque 3).

**Quienes necesitarían consultar.** La abogada, que hoy hace de oficial de forma informal, pediría los atributos con datos personales, su categoría, dónde están y quién responde por ellos. No existe un área de seguridad de la información: la función la cumple de forma parcial el coordinador de TI, que necesitaría la lista de atributos sensibles y privados y dónde están (Bloque 8). Servicio al cliente apoya a Jurídica en las solicitudes de los titulares (Bloque 2). La gerente general espera en seis meses un listado de datos personales clasificado y con responsables (Bloque 6). La empresa nunca ha preparado un reporte ante la SIC y no se ha determinado si estaba obligada a registrar sus bases; la gerente general quiere resolver esa duda con el abogado externo (Bloque 7).

**Lo que rodea al dominio.** Varias actividades ya tienen quien las haga, de forma informal: las autorizaciones, las solicitudes de los titulares, la corrección de duplicados, el control de accesos y las copias de seguridad. El depurar datos viejos no tiene un responsable, y reportar incidentes carece de procedimiento definido (Bloque 2). Alrededor hay terceros que reciben datos del negocio: portales, aseguradora, banco y notarías (Bloque 8). Otros acceden a información delicada: el abogado externo ve contratos, cédulas y expedientes de cobro, y los practicantes y contratistas acceden a hojas y carpetas (Bloque 8).

**Dónde queda la herramienta.** Se ubicaría al lado de estas fuentes sin reemplazarlas: el negocio no espera que cambie las bases de datos, y sí que el diccionario refleje los cambios que hagan los proveedores. Recibiría la estructura de S1, S3 y S4 que entrega TI, la de S2 que entrega el proveedor, un inventario hecho a mano de las hojas, las carpetas, el correo y WhatsApp, las definiciones y reglas de calidad de los responsables de dato, y la clasificación con su justificación, que el negocio espera de Jurídica o del oficial y no de cada área por su cuenta (Bloques 4 y 8). Entregaría información a la abogada que hace de oficial, a TI por su función de seguridad y a los abogados para preparar un eventual reporte a la SIC, que se exportaría como informe. La gerente general y la abogada prefieren que no lea datos de personas, solo la estructura, para no abrir otro punto de exposición de cédulas e ingresos. La entrevista lo presenta como un deseo que el equipo puede discutir, y el equipo lo adoptó como restricción todavía candidata (C1, H-13). Esa adopción es decisión del equipo, no del escenario.

---

## 3.1 V5: dominios y subdominios

![V5 - Dominios y subdominios](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/main/dominios%20y%20lenguajes%20ubicuos/V5%20-%20Dominios%20y%20subdominios.png)

### Qué muestra

El dominio de Gestión del Dato Personal, en la parte que cubre la solución (el gobierno del dato personal), dividido en 8 subdominios. Cada uno está clasificado como Core, de soporte o genérico. La vista muestra las dependencias entre subdominios y los objetos de negocio que maneja cada uno: 8 subdominios, 13 objetos y 13 relaciones Serving.

### Cómo se lee

- Cada rectángulo grande es un subdominio. Su color indica el tipo: naranja fuerte Core, naranja claro soporte y gris genérico. **No es el impacto de la solución de la V2**: la leyenda de la vista lo aclara.
- Cada subdominio lleva tres propiedades: `Subdominio DDD` (Core, Supporting o Generic, los mismos valores de la V2), `Requisitos` y `Pasos E2E`.
- Una flecha de A a B es una relación Serving y se lee "A sirve a B", es decir, B depende de A.
- Los objetos dentro de cada subdominio son los mismos de la V4c, no copias.

### Subdominios y su clasificación

| # | Subdominio | Tipo | Pasos del E2E | Requisitos | Objetos de negocio |
|---|---|---|---|---|---|
| 1 | Fuentes y metadatos técnicos | Soporte | P1, P2, P8 | R1, R7, R8 | Fuente de datos, Autorización de acceso a metadatos, Metadato técnico, Cambio de estructura |
| 2 | Atributos de negocio y su descripción | **Core** | P3, P4 | R3, R4 | Atributo de negocio, Metadato de negocio |
| 3 | Clasificación y validación jurídica | **Core** | P5, P6 | R2 | Clasificación del atributo |
| 4 | Responsables, autoridad y decisiones | Soporte | P4 (en parte) | R10; R3 y R8 (en parte) | Responsabilidad sobre el dato, Evidencia de decisión |
| 5 | Catálogo de términos | Soporte | Parte de P7 | R6 | Término de negocio |
| 6 | Diccionario integrado | **Core** | Parte de P7 | R5 | Diccionario de datos |
| 7 | Consulta y reporte | Soporte | P9 | R9 | Informe regulatorio |
| 8 | Control de acceso por rol | Genérico | Transversal | R10 (parte técnica) | Permiso de acceso |

### Argumento de cada subdominio y su relación con la V2

| # | Argumento | Capacidades de la V2 (propiedad Subdominio DDD) |
|---|---|---|
| 1 | Alimenta a todos los demás con la estructura técnica, pero importarla es una función habitual y no es lo que el negocio pidió. Lo específico (CRM vía proveedor, solo estructura) queda en la capa anticorrupción. Una columna renombrada en S2 dejó a S4 tres días sin actualizar precios (Bloque 5) | Gestión de metadatos técnicos, Gestión de cambios de estructura de datos (Supporting) |
| 2 | Cubre "conocer" y "describir": inventario, definición, calidad y validación del atributo. Es el concepto del que dependen el 3, el 4, el 5 y el 6. VR_CAN tiene tres definiciones (Bloque 5) y las reglas de calidad están dentro del código de cada sistema (Bloque 4) | Gestión de metadatos de negocio, Inventario de atributos de negocio (Core); Definición de políticas y reglas de calidad y validación (Supporting) |
| 3 | Cubre "clasificar": categorías legales, validación de Jurídica y estados propuesta, en revisión y validada. Hoy la abogada responde sin dejar registro y la categoría puede depender del uso (Bloque 4) | Clasificación de atributos por categoría legal (Core); Validación jurídica de la clasificación (Supporting) |
| 4 | Nadie tiene autoridad para aprobar definiciones y la gerente decide por correo sin guardar la decisión (Bloque 3). No hay procedimiento cuando falta un responsable (Bloque 5). La evidencia es una ausencia. Sube a Core si R10 se cierra con reglas propias | Gestión de responsables de datos, Gestión de trazabilidad y evidencia de decisiones, Resolución de conflictos y decisiones sobre datos (Supporting) |
| 5 | Cada área nombra distinto lo mismo (Bloque 2). Gestionar términos y conflictos es funcionalidad habitual de un catálogo | Gestión del catálogo de términos de negocio (Supporting) |
| 6 | Cubre "describir" al reunir lo técnico y lo de negocio por atributo, y R5 es requisito explícito del enunciado. Versiona lo publicado y marca lo incompleto. Es el más débil: es una vista de lectura, sin escenario propio en la entrevista y con riesgo de dominio anémico | Gestión del diccionario de datos (Core) |
| 7 | La abogada y TI necesitarían consultar (Bloque 8). La ubicación de datos responde al dolor n.º 1 de la gerente (Bloque 5), pero el formato del informe es genérico | Reporte regulatorio ante la SIC (Supporting) |
| 8 | Roles locales, sin directorio corporativo (Z15). Sin escenario propio fuerte. Se mantiene como decisión de diseño | Administración de accesos e identidades (Generic) |

En la V2, Gestión de Metadatos y Clasificación de Datos están marcadas como Core, pero son capacidades madre cuyas hijas incluyen varias Supporting. El Core se lee en las capacidades de la hoja.

### Dependencias entre subdominios

| Subdominio | Depende de | Evidencia |
|---|---|---|
| 1 Fuentes y metadatos técnicos | 8 | La gestión del acceso a metadatos usa el control de acceso (matriz de uso de la V4b) |
| 2 Atributos y su descripción | 1 | El contrato 3.3 vincula columnas técnicas con atributos y usa la fuente de datos |
| 3 Clasificación y validación jurídica | 2, 4 | No se clasifica lo que no se ha inventariado (V2b). La autoridad y la evidencia de decisiones son del 4 |
| 4 Responsables, autoridad y decisiones | 2 | El responsable se asigna a un atributo (contrato 3.5) |
| 5 Catálogo de términos | 2 | El contrato 3.9 asocia términos a atributos |
| 6 Diccionario integrado | 1, 2, 3 | El contrato 3.8 usa metadato técnico, atributo, metadato de negocio y clasificación |
| 7 Consulta y reporte | 1, 3, 4, 6 | Los contratos 3.11 a 3.14 usan diccionario, clasificación, responsable, fuente y cambio de estructura |
| 8 Control de acceso por rol | Ninguna | |

Son 13 relaciones. La dependencia del 1 respecto al 4 (por la bitácora) se retiró porque la bitácora técnica no es subdominio y creaba el ciclo 1, 2, 4, 1. Entre el 2 y el 4 la dependencia va del 4 al 2, porque el responsable se asigna a un atributo. El control de acceso solo se conecta con el 1, tal como lo marca la matriz de la V4b.

### Contraste de los cortes con el ecosistema

Los subdominios salieron del proceso y de tres criterios: lenguaje propio, actores distintos y razón de cambio distinta. El ecosistema permite ver cuáles tienen un grupo distinto detrás. Esta lectura es del equipo, no de la entrevista.

- **Fuentes y metadatos técnicos** tiene grupo propio: TI y los proveedores, con S2 accesible solo mediante el proveedor.
- **Clasificación y validación jurídica** también: la abogada interna y, a veces, el abogado externo.
- **Atributos y su descripción** y **catálogo de términos** comparten el mismo grupo, las áreas que generan y usan los datos. Separarlos es una decisión de diseño: el concepto del dato frente a la palabra con que cada área lo nombra. El conflicto de significado aparece entre áreas y se manifiesta en el dato, como en VR_CAN (Bloque 5).
- **Responsables, autoridad y decisiones** se apoya en una ausencia: nadie tiene la autoridad, el oficial está por decidir y los responsables por designar. A eso se suman los desacuerdos sobre quién debería decidir.
- **Consulta y reporte** se apoya en quienes necesitarían consultar, aunque el informe nunca se haya preparado.
- **Diccionario integrado** y **control de acceso** no corresponden a ningún grupo de personas. Son decisiones de diseño. El Bloque 7 solo advierte que el propio diccionario puede ser información delicada.

## 3.2 V7: lenguaje ubicuo

![V7](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/main/dominios%20y%20lenguajes%20ubicuos/V7%20-%20Lenguaje%20ubicuo.png)


### Qué muestra

Los 35 términos del glosario en 10 agrupaciones: los 8 subdominios de la V5 (25 términos) y dos grupos que no son subdominios, el lenguaje del negocio inmobiliario (7) y el lenguaje jurídico (3).

### Cómo se lee

- Cada término es una Representation. Su definición está en Documentation y su ejemplo en la propiedad `Ejemplo`.
- Los subdominios llevan el color de la V5. Los dos grupos de lenguaje no tienen color, porque no son subdominios.
- Trece términos tienen un objeto equivalente en la V5, y la propiedad `Objeto de negocio en la V5` lo indica. En *Clasificación* y *Responsable de dato* el nombre del objeto es distinto (*Clasificación del atributo* y *Responsabilidad sobre el dato*).

### Glosario

| Término | Subdominio o grupo | Definición | Ejemplo |
|---|---|---|---|
| **Fuente de datos** | 1 · Fuentes y metadatos técnicos | Sistema o lugar donde hay datos que deben documentarse. Puede tener diccionario técnico (una base de datos) o no tenerlo (hojas, carpetas, correo, mensajería). Una fuente identificada pero sin inventariar se muestra como *área sin cubrir*. | S2, un CRM en la nube, solo entrega su estructura mediante un pedido al proveedor, y las hojas de cálculo no tienen diccionario (Bloque 1) |
| **Metadato técnico** | 1 · Fuentes y metadatos técnicos | Descripción de la estructura de una columna en un sistema fuente: tabla, columna, tipo de dato, longitud y obligatoriedad. Se lee del diccionario del motor y no incluye los registros. Es la parte técnica de un *atributo de negocio*. | El negocio dice que la cédula tiene hasta 10 dígitos, pero en S2 el campo acepta 20 caracteres, incluidas letras (Bloque 5) |
| **Autorización de acceso a metadatos** | 1 · Fuentes y metadatos técnicos | Constancia de quién autorizó, y cuándo, el acceso de solo lectura a la estructura de una fuente. Sin ella no se habilita la importación. No es la autorización que firma un *titular* ni un *permiso de acceso* a la herramienta. | Para S1 autoriza la jefa de administración y ejecuta el coordinador de TI (Bloque 8) |
| **Importación** | 1 · Fuentes y metadatos técnicos | Lectura de la estructura técnica de una fuente para traerla a la herramienta. Solo trae estructura, nunca registros con datos de personas. | S2 tarda días en entregar su estructura, y el negocio acepta tener esa fuente desactualizada si se sabe (Bloque 8) |
| **Cambio de estructura** | 1 · Fuentes y metadatos técnicos | Diferencia detectada entre dos importaciones de una misma fuente: tabla o columna agregada, renombrada o modificada. No es un cambio de clasificación ni de definición. | El proveedor de S2 renombró una columna y la publicación hacia S4 dejó de actualizar los precios durante tres días (Bloque 5) |
| **Atributo de negocio** | 2 · Atributos de negocio y su descripción | Concepto de dato que se documenta una sola vez, con su definición, su responsable y su clasificación, aunque esté guardado en varias columnas de varios sistemas. No es la columna o campo de un sistema fuente, que es solo la ubicación técnica del dato (ver *metadato técnico*). | La cédula está en S1, que acepta de 7 a 11 caracteres, y en S2, que acepta letras (Bloque 4): son dos columnas de un mismo atributo |
| **Metadato de negocio** | 2 · Atributos de negocio y su descripción | Descripción de un atributo hecha desde el negocio: su definición, su responsable, su política de calidad y su expresión regular. La asignación del responsable, su historial y quién lo designa se gestionan aparte (ver *responsable de dato*). | La columna VR_CAN de S1 tiene tres definiciones en uso y ningún responsable asignado (Bloque 5) |
| **Política de calidad** | 2 · Atributos de negocio y su descripción | Regla que describe cómo debe ser el valor de un atributo (formato, longitud, obligatoriedad). Se documenta, no se ejecuta contra los datos. | La cédula debería tener solo números, de 6 a 10 dígitos y sin puntos (Bloque 4) |
| **Expresión regular** | 2 · Atributos de negocio y su descripción | Patrón de texto que valida el formato de un atributo. Se registra y se comprueba que sea sintácticamente válida, pero no se ejecuta contra datos reales. Valida el formato, no que el dato sea verdadero ni lícito. | `^[0-9]{6,10}$` para la cédula, ilustrativa (Bloque 4) |
| **Atributo incompleto** | 2 · Atributos de negocio y su descripción | Atributo al que le falta definición, responsable o clasificación. Se muestra como incompleto y no como correcto. | Nadie recuerda con certeza qué guarda la columna OBS3 de S1, así que le faltaría la definición (Bloque 5) |
| **Clasificación** | 3 · Clasificación y validación jurídica | Asignación a un atributo de una *categoría legal*, con su criterio y su justificación. No incluye la *finalidad* del dato. | La abogada considera privada la cuenta bancaria del propietario (Bloque 4) |
| **Categoría legal** | 3 · Clasificación y validación jurídica | Cada nivel con que se clasifica un atributo. Las clases pública, semiprivada y privada las define la Ley 1266 de 2008, y la Ley 1581 de 2012 añade otras categorías. El Decreto 1377 de 2013 completa la de dato público: es el que no cae en las otras tres. El dato semiprivado no es íntimo, reservado ni público, y su conocimiento puede interesar a cierto sector o a la sociedad, por ejemplo la información financiera y crediticia de la actividad comercial o de servicios. El privado, por ser íntimo o reservado, solo le interesa a su titular. El sensible es el que afecta la intimidad del titular, y su definición completa está en el art. 5 de la Ley 1581. En el habla cotidiana "delicado" es una intuición; aquí son categorías con definición legal. | La abogada considera sensible el estado de salud escrito en "observaciones" y dice que no debería estar ahí (Bloque 4) |
| **Estado de la clasificación** | 3 · Clasificación y validación jurídica | Punto de revisión de una clasificación: propuesta, en revisión o validada. Es definitiva solo cuando la valida quien tenga la autoridad, hoy Jurídica o el oficial (por definir en R10). Un atributo sin clasificación no tiene estado y se muestra como "sin clasificar". Ver *estado*. | La abogada duda entre privado y semiprivado para el historial de mora (Bloque 4); la clasificación quedaría "en revisión", con la opinión de cada parte (Bloque 8) |
| **Finalidad** | 3 · Clasificación y validación jurídica (fuera del modelo) | Propósito para el cual se usa un dato personal. La herramienta no la registra: es una exclusión explícita, y su cambio no se detecta por software. | El teléfono del propietario se recogía para la captación, y luego Mercadeo lo compartió con un portal (Bloque 4) |
| **Responsable de dato** | 4 · Responsables, autoridad y decisiones | Persona o rol de negocio que responde por la definición y la calidad de un atributo, y queda registrado como tal. Se distingue del *administrador técnico* (TI, que conoce la estructura pero no decide el significado), del *oficial de protección de datos* y del *Responsable del Tratamiento* (término legal). | Un teléfono errado: TI dice que "es del negocio", Comercial dice que es de Administración, y nadie lo corrige (Bloque 5) |
| **Oficial de protección de datos** | 4 · Responsables, autoridad y decisiones | Rol por designar, hoy inexistente. La gerencia imagina que mantendría las políticas, atendería los reclamos de los titulares y sería el contacto con la autoridad. Si la ley exige designarlo está por verificar. No es el *responsable de dato*. | Ante la solicitud de un titular que pide suprimir sus datos, necesitaría saber en qué sistemas están (Bloque 2) |
| **Administrador del diccionario** | 4 · Responsables, autoridad y decisiones | Rol por designar que mantiene el diccionario y el catálogo en la herramienta. No es el administrador técnico de TI ni el "administrador" de permisos. | TI entrega la estructura técnica a "quien administre el diccionario", sin que esté definido quién es (Bloque 8) |
| **Evidencia de decisión** | 4 · Responsables, autoridad y decisiones | Registro inmutable de una decisión sobre un atributo (clasificación, definición o responsable): quién, cuándo, con qué criterio y qué cambió. El registro técnico guarda además denegaciones e importaciones, que no son decisiones. | El negocio querría mostrar quién clasificó un dato, con qué criterio y cuándo (Bloque 7) |
| **Término de negocio** | 5 · Catálogo de términos | Palabra con que las áreas nombran un concepto, registrada con su significado y asociada a los atributos que la describen. Puede tener un significado por área. | "Activo" es un interesado con seguimiento abierto para Comercial y un contrato vigente para Administración (Bloque 2) |
| **Catálogo de términos** | 5 · Catálogo de términos | Conjunto de términos de negocio con sus significados y los atributos asociados. Se consulta junto al *diccionario de datos*, que puede buscar un atributo por término. | Quien busque el atributo asociado a "canon" encontraría las dos columnas que lo guardan (Bloques 2 y 5) |
| **Conflicto de significado** | 5 · Catálogo de términos | Un término con más de un significado. Hay dos casos: (a) significados distintos por área, que se mantienen, uno por contexto; (b) disputa dentro de un mismo contexto sobre la definición de un atributo, que la organización debe decidir. | (a) "Canon" es el valor pactado al firmar para Comercial y el cobrado hoy para Administración (Bloque 2). (b) Tres definiciones de VR_CAN (Bloque 5) |
| **Diccionario de datos** | 6 · Diccionario integrado | Vista de solo lectura de cada atributo con su metadato técnico, su metadato de negocio, su clasificación y su responsable, más los términos asociados. Se publica por versiones y marca lo incompleto y la antigüedad de la información técnica. | La ficha de VR_CAN reuniría su estructura en S1, sus tres definiciones y la ausencia de responsable (Bloque 5) |
| **Informe regulatorio** | 7 · Consulta y reporte | Informe con información sobre las bases de datos y su clasificación, para que Jurídica lo presente a la autoridad. La herramienta no lo transmite y su formato está por verificar. Si no está validado, no se presenta como definitivo. | Habría que reunir la lista de bases con datos personales, su finalidad, responsable y encargado, clasificación y medidas de seguridad (Bloque 8) |
| **Permiso de acceso** | 8 · Control de acceso por rol | Autorización para que un *rol* realice una operación en la herramienta, como consultar, proponer o aprobar. No es la *autorización de acceso a metadatos* ni la de un *titular*. | Quién puede ver y modificar la clasificación y las definiciones es un punto a revisar antes de dar el diseño por suficiente (Bloque 7) |
| **Rol** | 8 · Control de acceso por rol | En la herramienta, conjunto de permisos que se asigna a un usuario. En el negocio y en las vistas de ArchiMate, función que alguien cumple (responsable de dato de área, oficial), que no es un cargo. | Quién propone una definición y quién la aprueba tendrían roles distintos, y esa autoridad sigue por definir (R10, Bloque 3) |
| **Cliente** | Lenguaje del negocio inmobiliario | Para Comercial es el interesado que busca inmueble; para Administración, el arrendatario; para Contabilidad, el propietario que paga la administración. | Ilustrativo: una consulta de "clientes" daría interesados si la hace Comercial y propietarios si la hace Contabilidad. La entrevista solo da los significados (Bloque 2) |
| **Propietario** | Lenguaje del negocio inmobiliario | Para Comercial es quien firmó el contrato de corretaje; para Administración y Contabilidad, el titular de la cuenta bancaria a la que se paga, que a veces es otra persona. | Quien firmó el contrato de corretaje puede no ser a quien se le paga (Bloque 2) |
| **Interesado** | Lenguaje del negocio inmobiliario | Persona que busca un inmueble y queda registrada con un asesor. No es el *interesado* (stakeholder) de ArchiMate en la V1. | Hay interesados de 2016 que nunca contrataron y siguen en S2 (Bloque 1) |
| **Inmueble** | Lenguaje del negocio inmobiliario | Bien que se vende o se arrienda. S1 registra los administrados y S2 los que están en oferta. Que sean el mismo bien en dos momentos es inferencia del equipo, no está en la entrevista. | S2 publica la ficha del inmueble en el sitio web S4 (Bloque 1) |
| **Estado** | Lenguaje del negocio inmobiliario | Palabra con varios sentidos: para Comercial, el inmueble está publicado, reservado, vendido o arrendado; para Administración, ocupado, desocupado o en reparación; en S1, el campo describe el contrato (6 valores técnicos); en la herramienta hay un *estado de la clasificación* y un estado de importación (disponible o desactualizada). | "Estado" significa "publicado o no" en S2 y "contrato vigente" en S1 (Bloque 1) |
| **Activo** | Lenguaje del negocio inmobiliario | Para Comercial es un interesado con seguimiento abierto; para Administración, un contrato vigente. | El reporte de morosidad de septiembre incluyó contratos terminados porque "estado = activo" significa cosas distintas en S1 y S2 (Bloque 2) |
| **Canon** | Lenguaje del negocio inmobiliario | Para Comercial es el valor pactado al firmar; para Administración, el valor que se cobra hoy, ya reajustado. | Tras el reajuste anual (Bloque 1), el valor pactado y el cobrado dejan de coincidir |
| **Titular** | Lenguaje jurídico | Persona natural a quien pertenecen los datos personales que se tratan (Ley 1581 de 2012, art. 3). Puede ser propietario, arrendatario, interesado u otra. No es el "titular de la cuenta bancaria" del propietario. | Un propietario pide que borren sus datos y nadie sabe en cuántos lugares están (Bloque 1) |
| **Dato personal** | Lenguaje jurídico | Cualquier información que se relacione con una persona natural identificada o que pueda llegar a identificarse (Ley 1581 de 2012, art. 3). La herramienta no lee datos personales, solo la estructura de dónde están (restricción C1). | La gerente y la abogada no quieren abrir otro punto de exposición de cédulas e ingresos (Bloque 8) |
| **Responsable y Encargado del Tratamiento** | Lenguaje jurídico | Términos legales de la Ley 1581 (art. 3). El Responsable es quien decide, solo o con otros, sobre la base de datos o el tratamiento. El Encargado es la persona natural o jurídica, pública o privada, que realiza el tratamiento por cuenta del Responsable. No es el *responsable de dato*. | El proveedor del CRM guarda datos de la empresa y tiene acceso a ellos, sin documento que defina sus responsabilidades (Bloques 3 y 7) |

---

## 3.3 V7b: términos con varios significados

![V7b - Términos con varios significados](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/blob/main/dominios%20y%20lenguajes%20ubicuos/V7b%20-%20Términos%20con%20varios%20significados.png)

### Cómo se lee

Los diez términos son los mismos elementos de la V7. Cada significado es un Meaning unido a su término con una Association, y su propiedad `Contexto` dice dónde aplica. Cliente, Propietario, Estado, Activo, Canon y Titular vienen de la entrevista. Interesado, Rol y Atributo de negocio salen del vocabulario del equipo, y Responsable de dato mezcla las dos fuentes.

| Término | Contexto | Significado |
|---|---|---|
| Cliente | Comercial | Interesado que busca inmueble |
| Cliente | Administración | Arrendatario |
| Cliente | Contabilidad | Propietario que paga la administración |
| Propietario | Comercial | Quien firmó el contrato de corretaje |
| Propietario | Administración y Contabilidad | Titular de la cuenta bancaria a la que se paga, que a veces es otra persona |
| Estado | Comercial | Publicado, reservado, vendido o arrendado |
| Estado | Administración | Ocupado, desocupado o en reparación |
| Estado | Sistema S1 | Describe el contrato (6 valores técnicos) |
| Estado | Herramienta | Estado de la clasificación: propuesta, en revisión o validada |
| Estado | Herramienta | Estado de importación: disponible o desactualizada |
| Activo | Comercial | Interesado con seguimiento abierto |
| Activo | Administración | Contrato vigente |
| Canon | Comercial | Valor pactado al firmar |
| Canon | Administración | Valor que se cobra hoy, ya reajustado |
| Interesado | Comercial | Persona que busca un inmueble y queda registrada con un asesor |
| Interesado | ArchiMate (V1) | Stakeholder: persona, equipo u organización con interés en la solución |
| Rol | Herramienta | Conjunto de permisos que se asigna a un usuario |
| Rol | Negocio y ArchiMate | Función que alguien cumple, como responsable de dato de área u oficial; no es un cargo |
| Responsable de dato | Negocio | Persona o rol de negocio que responde por la definición y la calidad de un atributo |
| Responsable de dato | TI | Administrador técnico: conoce la estructura de la base de datos, pero no decide el significado |
| Responsable de dato | Legal | Responsable del Tratamiento: quien decide sobre la base de datos o el tratamiento (Ley 1581, art. 3) |
| Titular | Legal | Persona natural a quien pertenecen los datos personales (Ley 1581, art. 3) |
| Titular | Administración y Contabilidad | Titular de la cuenta bancaria a la que se paga al propietario |
| Atributo de negocio | Herramienta | Concepto de dato documentado una sola vez, guardado en varias columnas de varios sistemas |
| Atributo de negocio | Sistema fuente | Columna o campo: la ubicación técnica del dato |

---

# V10 trazabilidad vertical

![V10 - Trazabilidad vertical](https://github.com/restrepo0510/Evaluacion_3_DDD_Archimate/tree/f72a6f8b41602e87ca24d183a394e8fe6308c789/trazabilidad%20vertical)

### Qué muestra

Una sola vista transversal que recorre las cuatro capas del modelo de arriba abajo: Motivación, Estrategia, Negocio y Aplicación. Parte de la meta general y sus cinco sub-metas, baja por los resultados esperados, las restricciones y los requisitos de la aplicación, llega a las capacidades que realizan cada requisito y a los pasos del proceso E2E que realizan esas capacidades, y termina en los servicios de aplicación que apoyan cada paso y en los componentes que los prestan. Responde la pregunta que pide el enunciado: **por qué existe cada componente**, es decir, qué meta y qué capacidad lo justifican.

### Cómo se lee

Cada banda se conecta solo con la contigua, así que cada hilo se sigue en vertical sin saltar capas. Todas las flechas apuntan hacia arriba, de lo construido a lo que se persigue:

| Banda | Elementos | Relación hacia la banda superior | Lectura |
|---|---|---|---|
| Motivación · Metas | G1 con G2–G6 anidadas | Agregación (por anidamiento) | qué se quiere lograr |
| Motivación · Resultados esperados | O1–O9 | Realización → meta | cómo se sabrá que se logró |
| Motivación · Restricciones | C1–C4, cada una junto a su requisito | Influencia «restringe» → requisito | qué limita al requisito |
| Motivación · Requisitos de la aplicación | R1–R10 | Realización → resultado | qué debe hacer la aplicación |
| Estrategia · Capacidades | 13 capacidades de la V2 | Realización → requisito | qué habilidad de la organización cumple el requisito |
| Negocio · Proceso E2E | P1–P9 dentro de "Gobierno E2E del dato personal" | Realización → capacidad | cómo se ejerce la capacidad en el día a día |
| Aplicación · Servicios de aplicación | 12 servicios | Servicio → paso | qué funcionalidad del software apoya el paso |
| Aplicación · Componentes | 8, uno por subdominio de la V5 | Asignación → servicio de aplicación | qué parte del software presta el servicio |

Cada elemento está ubicado debajo de los elementos a los que se conecta, para que las líneas bajen casi en vertical y se crucen lo menos posible. Las capacidades conservan el color de impacto de la V2 y los pasos el color de apoyo de la solución de la V3b, así que la misma vista muestra dónde la herramienta opera de lleno y dónde solo registra o prepara. Motivación usa el morado estándar de ArchiMate y Aplicación el azul.

> **Códigos.** G, O, R y C son los de la V1; P1–P9 son los pasos del proceso E2E. Los componentes se numeran como el subdominio de la V5 al que corresponden.

### Hilos completos, de la meta al componente

Cada fila es un recorrido de arriba abajo. Es la respuesta a «por qué existe cada componente».

| Meta | Resultado | Requisito | Capacidad | Paso | Servicio de aplicación | Componente |
|---|---|---|---|---|---|---|
| G2 Conocer los datos | O1 Metadatos técnicos de S1–S4 importados | R1 Importar metadatos técnicos (restringido por C1 y C3) | Gestión de metadatos técnicos | P1, P2 | fuentes y autorizaciones; importación de estructura | 1 Fuentes y metadatos técnicos |
| G2 Conocer los datos | O2 Fuentes no estructuradas inventariadas | R7 Registrar manualmente fuentes no estructuradas | Inventario de atributos de negocio | P3 | inventario de atributos | 2 Atributos de negocio |
| G3 Clasificar los datos | O3 Atributos con clasificación registrada | R2 Registrar la clasificación (restringido por C2) | Clasificación de atributos por categoría legal; Validación jurídica de la clasificación | P5, P6 | clasificación; validación jurídica; responsables y evidencia | 3 Clasificación y validación jurídica; 4 Responsables y decisiones |
| G4 Describir los datos | O4 Atributos con definición y responsable | R3 Registrar definición y responsable | Gestión de metadatos de negocio; Gestión de responsables de datos | P4 | descripción de atributos; responsables y evidencia | 2 Atributos de negocio; 4 Responsables y decisiones |
| G4 Describir los datos | O4 Atributos con definición y responsable | R10 Gestionar roles de edición y aprobación | Gestión de responsables de datos; Administración de accesos e identidades | P4, P1 | responsables y evidencia; control de acceso | 4 Responsables y decisiones; 8 Control de acceso por rol |
| G4 Describir los datos | O5 Atributos con política de calidad y regla | R4 Registrar políticas de calidad y expresiones regulares | Definición de políticas y reglas de calidad y validación | P4 | descripción de atributos | 2 Atributos de negocio |
| G4 Describir los datos | O6 Términos asociados y conflictos identificados | R6 Gestionar el catálogo de términos | Gestión del catálogo de términos de negocio | P7 | catálogo de términos | 5 Catálogo de términos |
| G4 Describir los datos | O7 Diccionario integrado consultable | R5 Gestionar el diccionario integrado | Gestión del diccionario de datos | P7 | diccionario integrado | 6 Diccionario integrado |
| G5 Mantener el diccionario vigente | O8 Historial de importaciones y cambios | R8 Registrar importaciones y detectar cambios | Gestión de cambios de estructura de datos; Gestión de trazabilidad y evidencia de decisiones | P8 | cambios de estructura | 1 Fuentes y metadatos técnicos |
| G6 Contar con evidencia consultable | O9 Metadatos consultables y exportables | R9 Consultar y exportar metadatos (restringido por C4) | Gestión del diccionario de datos; Reporte regulatorio ante la SIC | P7, P9 | diccionario integrado; consulta y reporte | 6 Diccionario integrado; 7 Consulta y reporte |

Un hilo completo, de arriba abajo: la meta *Clasificar los datos* se logra con el resultado *Atributos con clasificación registrada*, que realiza el requisito *Registrar la clasificación de cada atributo*, limitado por la restricción *Obligaciones legales por verificar con Jurídica*. Ese requisito lo realiza la capacidad *Clasificación de atributos por categoría legal*, que se ejerce en el paso *Clasificar atributos por categoría legal*. Al paso lo apoya el *Servicio de aplicación de clasificación*, que presta el *Componente de clasificación y validación jurídica*.

### Relaciones nuevas: capacidad → requisito

Estas 15 realizaciones no existían en el modelo: la V1 llega hasta el requisito y la V2 empieza en la capacidad. Son el puente entre Motivación y Estrategia.

| Capacidad | Requisito que realiza | Justificación |
|---|---|---|
| Gestión de metadatos técnicos | R1 Importar metadatos técnicos desde los motores | La importación de la estructura de S1 a S4 es la forma en que se ejerce la capacidad |
| Inventario de atributos de negocio | R7 Registrar manualmente fuentes no estructuradas | El inventario suma los atributos de fuentes sin motor, que solo se registran a mano (V3b, P3) |
| Clasificación de atributos por categoría legal | R2 Registrar la clasificación de cada atributo | Registrar la categoría legal es la capacidad de clasificar |
| Validación jurídica de la clasificación | R2 Registrar la clasificación de cada atributo | El estado "validada" depende de Jurídica (principio P5 de la V1) |
| Gestión de metadatos de negocio | R3 Registrar definición y responsable por atributo | La definición es metadato de negocio |
| Gestión de responsables de datos | R3 Registrar definición y responsable por atributo | El responsable por atributo lo gestiona esta capacidad |
| Definición de políticas y reglas de calidad y validación | R4 Registrar políticas de calidad y expresiones regulares | Política y expresión regular son reglas de calidad y validación |
| Gestión del diccionario de datos | R5 Gestionar el diccionario de datos integrado | Correspondencia directa |
| Gestión del catálogo de términos de negocio | R6 Gestionar el catálogo de términos y asociarlos a atributos | Correspondencia directa |
| Gestión de cambios de estructura de datos | R8 Registrar importaciones y detectar cambios de estructura | Detectar diferencias entre importaciones es gestionar cambios de estructura |
| Gestión de trazabilidad y evidencia de decisiones | R8 Registrar importaciones y detectar cambios de estructura | El historial de cambios de clasificación y definición es evidencia trazable |
| Gestión del diccionario de datos | R9 Consultar y exportar metadatos | Lo que se consulta y exporta es el diccionario publicado |
| Reporte regulatorio ante la SIC | R9 Consultar y exportar metadatos | La exportación prepara lo que Jurídica presenta ante la SIC |
| Gestión de responsables de datos | R10 Gestionar roles de edición y aprobación | Quién propone y quién aprueba se apoya en los responsables de datos |
| Administración de accesos e identidades | R10 Gestionar roles de edición y aprobación | Los roles se aplican como permisos locales de la herramienta (Z15) |

### Servicios y componentes de aplicación

Los servicios de aplicación son la versión en software de los servicios de negocio de la V4: cada uno se basa en los contratos de capa 3 y capa 4 de la V4e y la V4f. Se propone **un componente por subdominio de la V5**, porque cada subdominio tiene lenguaje, actores y razón de cambio propios, y esos son los límites naturales del software.

| # | Componente (subdominio V5) | Servicios de aplicación que presta | Paso al que sirven | Contratos en que se basan |
|---|---|---|---|---|
| 1 | Fuentes y metadatos técnicos (Soporte) | fuentes y autorizaciones; importación de estructura; cambios de estructura | P1; P2; P8 | 3.1, 3.2, 3.10, 4.2, 4.3, 4.9; usa los adaptadores A1 a A4 |
| 2 | Atributos de negocio (Core) | inventario de atributos; descripción de atributos | P3; P4 | 3.3, 3.4, 4.1, 4.4 |
| 3 | Clasificación y validación jurídica (Core) | clasificación; validación jurídica | P5; P6 | 3.6, 3.7, 4.6 |
| 4 | Responsables y decisiones (Soporte) | responsables y evidencia | P4 y P6 | 3.5, 4.5, 4.10; el contrato 3.7 agrega la Evidencia de decisión |
| 5 | Catálogo de términos (Soporte) | catálogo de términos | P7 | 3.9, 4.7 |
| 6 | Diccionario integrado (Core) | diccionario integrado | P7 | 3.8, 4.8 |
| 7 | Consulta y reporte (Soporte) | consulta y reporte | P9 | 3.11 a 3.14, 4.11, 4.13; usa los adaptadores A5 a A8 |
| 8 | Control de acceso por rol (Genérico) | control de acceso | P1 | 4.12 |

El componente 1 presta el servicio de cambios de estructura, que apoya a P8, al otro extremo del proceso. Esa línea de asignación rodea la banda de componentes por debajo para no cruzar las demás.

