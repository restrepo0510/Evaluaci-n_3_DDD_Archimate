- [2. Descomposición de servicios del proceso E2E](#2-descomposición-de-servicios-del-proceso-e2e)
  - [2.1 V4a: del proceso E2E a los servicios de actividad](#21-v4a-del-proceso-e2e-a-los-servicios-de-actividad)
  
  - [2.2 V4b: descomposición en cuatro capas de servicio](#22-v4b-descomposición-en-cuatro-capas-de-servicio)
   
  - [2.3 V4c: servicios de entidad y utilidad, roles, funciones y objetos pasivos](#23-v4c-servicios-de-entidad-y-utilidad-roles-funciones-y-objetos-pasivos)

  - [2.4 V4D: capa anticorrupción e interoperabilidad](#24-v4d-capa-anticorrupción-e-interoperabilidad)
   
  - [2.5 V4E: Contract First, contratos de los servicios de actividad (capa 3)](#25-v4e-contract-first-contratos-de-los-servicios-de-actividad-capa-3)

  - [2.6 V4F: Contract First, contratos de entidad, utilidad e interoperabilidad](#26-v4f-contract-first-contratos-de-entidad-utilidad-e-interoperabilidad)

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
