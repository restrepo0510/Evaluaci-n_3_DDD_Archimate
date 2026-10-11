# Gobierno de datos Hogar Andino Inmobiliaria S.A.S. 

- [1. Entendimiento del negocio y mapa de capacidades](#1-entendimiento-del-negocio-y-mapa-de-capacidades)
  - [1.1 V2: mapa de capacidades](#11-v2-mapa-de-capacidades)

  - [1.2 V2B: dependencias de gobierno de datos, recursos y cursos de acción](#12-v2b-dependencias-de-gobierno-de-datos-recursos-y-cursos-de-acción)

  - [1.3 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan](#13-v3a-cadena-de-valor-del-negocio-eventos-y-capacidades-que-la-habilitan)
  
  - [1.4 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores](#14-v3b-proceso-e2e-de-gobierno-de-datos-cadena-de-valor-eventos-y-actores)
  
  - [1.5 V3C: proceso E2E y capacidades que realiza](#15-v3c-proceso-e2e-y-capacidades-que-realiza)
    
- [2. Descomposición de servicios del proceso E2E](#2-descomposición-de-servicios-del-proceso-e2e)
  - [2.1 V4a: del proceso E2E a los servicios de actividad](#21-v4a-del-proceso-e2e-a-los-servicios-de-actividad)
  
  - [2.2 V4b: descomposición en cuatro capas de servicio](#22-v4b-descomposición-en-cuatro-capas-de-servicio)
   
  - [2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos](#23-v4c-servicios-de-entidad-y-utilidad-roles-funciones-y-objetos-pasivos)

  - [2.4 V4D: capa anticorrupción e interoperabilidad](#24-v4d-capa-anticorrupción-e-interoperabilidad)
   
  - [2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)](#25-v4e-contract-first-contratos-de-los-servicios-de-actividad-capa-3)

  - [2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad](#26-v4f-contract-first-contratos-de-entidad-utilidad-e-interoperabilidad)

# 1. Entendimiento del negocio y mapa de capacidades 

La Fase 1 responde cinco preguntas, que se reparten entre las vistas así:
 
| Vista | Pregunta que responde |
|---|---|
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
| Business Process | Negocio | Pasos del proceso E2E |
| Business Event | Negocio | Hechos que disparan una etapa o un paso |
| Business Actor y Business Role | Negocio | Quién ejecuta o responde por cada paso |
| Grouping | Otros | Franjas de la V2 |
 
Relaciones que se usan:
 
| Relación | Significado en este modelo |
|---|---|
| Composition | Una capacidad de Nivel 1 se compone de las de Nivel 2, y estas de las de Nivel 3 |
| Serving | La capacidad origen sirve a la capacidad o a la etapa destino; "A sirve a B" también se lee "B depende de A" |
| Realization | Un paso del proceso realiza una capacidad |
| Assignment | Un actor, rol o recurso se asigna a un paso o a una capacidad |
| Triggering | Secuencia entre etapas o pasos, o un evento que dispara una etapa o un paso |
| Association | Un curso de acción se ejecuta mediante una capacidad, o un evento se asocia con la etapa que dispara |
 
---
 
## 1.1 V2: mapa de capacidades
 
![V2 - Mapa de capacidades de Hogar Andino](images/V2.png)
 
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
 
## 1.2 V2b: dependencias de gobierno de datos, recursos y cursos de acción
 
![V2b - Dependencias de gobierno de datos](images/V2b.png)
 
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
 
## 1.3 V3A: cadena de valor del negocio, eventos y capacidades que la habilitan
 
![V3a - Cadena de valor del negocio](images/V3a.png)
 
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
 
## 1.4 V3B: proceso E2E de gobierno de datos, cadena de valor, eventos y actores
 
![V3b - Proceso E2E de gobierno de datos](images/V3b.png)
 
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
 
## 1.5 V3C: proceso E2E y capacidades que realiza
 
![V3c - Proceso E2E y capacidades](images/V3c.png)
 
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
