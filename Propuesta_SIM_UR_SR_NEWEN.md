# Propuesta de actualizacion UR/SR - SIM NEWEN

## 1. Objetivo
Este documento consolida una propuesta de actualizacion de Requisitos de Usuario (`UR`) y Requisitos de Sistema (`SR`) para el Subsistema Simulador de Vuelo (`SIM`) del programa `NEWEN`.

La propuesta se construye a partir de:
- `CDR SIM`: [11713P02CDD019_ANEXO A SIMULADOR DE VUELO (SIM).docx](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11713P02CDD019_ANEXO A SIMULADOR DE VUELO (SIM).docx>)
- `CDR General`: [11713P01CDD039_CUERPO_CDR -PROGRAMA NEWEN.docx](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11713P01CDD039_CUERPO_CDR -PROGRAMA NEWEN.docx>)
- `REQ Sistema SIM`: [11113P04REQ001 Sistemas SIM.docx](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11113P04REQ001 Sistemas SIM.docx>)
- `REQ Software SIM`: [11113P04REQ002 Software SIM.docx](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11113P04REQ002 Software SIM.docx>)
- `REQ Hardware SIM`: [11113P04REQ003 Hardware SIM.docx](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11113P04REQ003 Hardware SIM.docx>)
- `Contrato 97/2023`: [11713P01COT001 Contrato N° 97 - 2023.pdf](<C:\Users\juan.cornejo\Desktop\docs NEWEN\11713P01COT001 Contrato N° 97 - 2023.pdf>)
- Definiciones operacionales entregadas por el usuario en esta conversacion.

## 2. Criterios de trabajo
- El foco es solo `SIM`.
- El objetivo de entrenamiento es instruccion basica de vuelo para pilotos iniciales.
- La operacion por instrumentos se considera deseable y debe quedar soportada como capacidad de entrenamiento basica.
- La base normativa es `diseno alineado a FTD Nivel 6`; no se formula como requisito de certificacion efectiva ante autoridad.
- La cabina es fisica y el mundo exterior es virtual.
- La tecnologia visual definida para el concepto de realidad mixta es `Varjo XR-4 Secure Edition`.
- El vuelo en formacion y la acrobacia se consideran obligatorios.
- El instructor tambien cumplira rol de `ATC` para practica de comunicacion con el alumno.
- La interfaz con `MPS` y `DBS` se mantiene `TBD` a nivel de formato/protocolo.
- La transportabilidad ya esta considerada por diseno fisico con ruedas y anclajes.
- El mantenimiento esperado por usuario es `Nivel 1`, con accesos de revision a electronica y panel electrico.

## 3. Observaciones de linea base
- El `CDR SIM` es la mejor base tecnica actual para el subsistema.
- Los documentos `REQ` anteriores siguen siendo utiles como antecedentes, pero no deben tomarse como autoridad unica.
- El contrato y el `CDR` confirman al menos estos elementos del `SIM`:
  - cabina fisica
  - estacion de instructor
  - sistema visual inmersivo / realidad mixta
  - `force feedback`
  - 3 estaciones de simulacion
  - integracion con `MPS` y `DBS`
  - `UPS`
  - vuelo en formacion
  - entrenamiento de acrobacia
- La version anterior mezclaba `Pillan II` y `NEWEN`; esta propuesta normaliza todo a `NEWEN / T-40 NEWEN`.

## 4. Segmentacion propuesta

### 4.1 UR
| ID | Categoria | Descripcion |
|---|---|---|
| UR-SIM-001 | Mision de entrenamiento | El `SIM` debe apoyar la instruccion basica de vuelo para pilotos que recien inician su formacion. |
| UR-SIM-002 | Capacidades de entrenamiento | El `SIM` debe permitir la practica de procedimientos normales, procedimientos de emergencia, vuelo por instrumentos, vuelo en formacion y acrobacia. |
| UR-SIM-003 | Marco de diseno | El `SIM` debe ser disenado en alineacion con las capacidades esperadas para un `FTD Nivel 6`. |
| UR-SIM-004 | Configuracion fisica | El `SIM` debe contar con una cabina fisica de alta fidelidad y una representacion virtual del entorno exterior de vuelo. |
| UR-SIM-005 | Operacion instructor | El `SIM` debe contar con una estacion de instructor que permita reposicionamiento, control de clima, generacion de fallas, monitoreo del alumno, reinicio de la simulacion y practica de comunicacion tipo `ATC` con el alumno. |
| UR-SIM-006 | Operacion multiestacion | El `SIM` debe permitir entrenamiento distribuido entre 3 estaciones de simulacion. |
| UR-SIM-007 | Transportabilidad | El `SIM` debe ser transportable dentro del entorno operativo previsto. |
| UR-SIM-008 | Mantenibilidad | El `SIM` debe permitir mantenimiento Nivel 1 por parte del usuario, con accesos a revision de electronica y panel electrico. |
| UR-SIM-009 | Integracion | El `SIM` debe intercambiar informacion con `MPS` y `DBS` mediante interfaces a definir. |
| UR-SIM-010 | Realismo e inmersion | El `SIM` debe entregar una experiencia inmersiva y suficientemente realista para apoyar la transferencia al vuelo real. |

### 4.2 SR funcionales
| ID | Categoria | Descripcion |
|---|---|---|
| SR-SIM-001 | Modelo de aeronave | El `SIM` emulara de manera realista la disposicion de cabina, controles, instrumentacion y comportamiento general de la `T-40 NEWEN`. |
| SR-SIM-002 | Cabina fisica | La cabina del piloto sera fisica e incluira los controles, paneles e instrumentos necesarios para la instruccion basica de vuelo. |
| SR-SIM-003 | Mundo exterior | El entorno exterior de vuelo sera generado virtualmente y presentado al alumno mediante el sistema visual definido. |
| SR-SIM-004 | Base del simulador | El simulador sera de base fija. |
| SR-SIM-005 | Entrenamiento visual e instrumental | El `SIM` soportara instruccion visual e instruccion por instrumentos en los escenarios definidos para entrenamiento basico. |
| SR-SIM-006 | Meteorologia | El `SIM` simulara condiciones meteorologicas y de visibilidad relevantes para entrenamiento. |
| SR-SIM-007 | Combustible | El `SIM` simulara cambios de combustible y su efecto sobre el vuelo. |
| SR-SIM-008 | Force feedback | El `SIM` contara con `force feedback` al menos en baston y pedales. |
| SR-SIM-009 | Respuesta de mandos | El hardware y software del simulador ajustaran la respuesta de esfuerzo de control en el envelope de entrenamiento definido. |
| SR-SIM-010 | Reposicionamiento | La estacion de instructor permitira reposicionar la aeronave simulada a estados predefinidos o configurables. |
| SR-SIM-011 | Control meteorologico | La estacion de instructor permitira modificar variables meteorologicas y de visibilidad durante la sesion. |
| SR-SIM-012 | Fallas | La estacion de instructor permitira inyectar fallas de sistema y/o aeronave durante la sesion. |
| SR-SIM-013 | Monitoreo | La estacion de instructor permitira monitorear en tiempo real el estado de vuelo y desempeno del alumno. |
| SR-SIM-014 | Reinicio | La estacion de instructor permitira reiniciar la simulacion en forma controlada. |
| SR-SIM-014A | Comunicacion ATC | La estacion de instructor permitira al instructor desempenar el rol de `ATC` durante la sesion para practicar comunicaciones con el alumno. |
| SR-SIM-015 | Multiestacion | El sistema estara compuesto por 3 cabinas de simulacion, cada una con su estacion de instructor asociada. |
| SR-SIM-016 | Vuelo en formacion | El sistema permitira entrenamiento de vuelo en formacion entre las 3 estaciones de simulacion. |
| SR-SIM-017 | Control unico en formacion | Durante una sesion de vuelo en formacion, solo una estacion de instructor tendra control maestro de la sesion. |
| SR-SIM-018 | Acrobacia | El sistema permitira entrenamiento en maniobras acrobaticas. |
| SR-SIM-019 | Escenarios | El `SIM` soportara escenarios normales, anormales y de emergencia. |
| SR-SIM-020 | Integracion externa | El `SIM` intercambiara informacion con `MPS` y `DBS` mediante una interfaz externa definida en un documento posterior. |

### 4.3 SR de plataforma, hardware y arquitectura
| ID | Categoria | Descripcion |
|---|---|---|
| SR-SIM-021 | Visualizacion interior | El sistema visual permitira visualizar los elementos interiores de cabina con fidelidad suficiente para la instruccion basica. |
| SR-SIM-022 | Visualizacion exterior | La vision exterior a la cabina sera de naturaleza virtual y utilizara la tecnologia `Varjo XR-4 Secure Edition`, cubriendo el campo visual soportado por esa solucion dentro del concepto de entrenamiento adoptado. |
| SR-SIM-022A | Plataforma visual | El sistema visual de realidad mixta se implementara sobre `Varjo XR-4 Secure Edition` o su configuracion secure equivalente aprobada para el programa. |
| SR-SIM-023 | Latencia | El sistema visual operara con una latencia objetivo no mayor a `150 ms`. |
| SR-SIM-024 | COTS | El diseno considerara uso de tecnologias `COTS` cuando sean compatibles con objetivos de desempeno y mantenibilidad. |
| SR-SIM-025 | Energia de respaldo | El sistema contara con respaldo electrico mediante `UPS` para proteccion operacional y apagado controlado. |
| SR-SIM-026 | Coherencia con arquitectura NEWEN | El `SIM` sera coherente con la arquitectura integrada del sistema `NEWEN`, incluyendo su rol como subsistema periferico interoperable. |

### 4.4 SR de soporte, instalacion y mantenimiento
| ID | Categoria | Descripcion |
|---|---|---|
| SR-SIM-027 | Transportabilidad fisica | El sistema sera transportable mediante los elementos fisicos incorporados al diseno, incluyendo ruedas y anclajes. |
| SR-SIM-028 | Accesibilidad de mantenimiento | El diseno de cabina incluira accesos para inspeccion y mantenimiento Nivel 1 de componentes electronicos y panel electrico. |
| SR-SIM-029 | Mantenimiento Nivel 1 | El mantenimiento Nivel 1 podra ser ejecutado por usuario entrenado sin desmontajes estructurales mayores. |
| SR-SIM-030 | Condiciones de instalacion | La instalacion del `SIM` requerira condiciones de infraestructura electrica, espacio y seguridad definidas en la documentacion de instalacion. |

## 5. Trazabilidad UR -> SR
| UR | SR relacionados | Justificacion resumida |
|---|---|---|
| UR-SIM-001 | SR-SIM-001, SR-SIM-002, SR-SIM-005, SR-SIM-019 | La instruccion basica exige una cabina representativa, escenarios de instruccion y comportamiento de aeronave coherente. |
| UR-SIM-002 | SR-SIM-005, SR-SIM-006, SR-SIM-010, SR-SIM-011, SR-SIM-012, SR-SIM-014A, SR-SIM-016, SR-SIM-018, SR-SIM-019 | Las capacidades de entrenamiento se materializan en funciones del simulador y de la estacion instructor. |
| UR-SIM-003 | SR-SIM-004, SR-SIM-008, SR-SIM-009, SR-SIM-023, SR-SIM-025 | La alineacion a `FTD Nivel 6` impacta base fija, control loading, respuesta de mandos, latencia y respaldo operacional. |
| UR-SIM-004 | SR-SIM-002, SR-SIM-003, SR-SIM-021, SR-SIM-022, SR-SIM-022A | La definicion de cabina fisica y mundo exterior virtual baja a requisitos de plataforma y visualizacion. |
| UR-SIM-005 | SR-SIM-010, SR-SIM-011, SR-SIM-012, SR-SIM-013, SR-SIM-014, SR-SIM-014A | La estacion instructor queda cubierta por sus funciones minimas obligatorias. |
| UR-SIM-006 | SR-SIM-015, SR-SIM-016, SR-SIM-017 | La operacion de 3 estaciones requiere configuracion multiestacion y control maestro en formacion. |
| UR-SIM-007 | SR-SIM-027, SR-SIM-030 | La transportabilidad necesita elementos fisicos y condiciones de despliegue conocidas. |
| UR-SIM-008 | SR-SIM-028, SR-SIM-029 | La mantenibilidad de usuario se traduce en accesibilidad y tareas de Nivel 1. |
| UR-SIM-009 | SR-SIM-020, SR-SIM-026 | La integracion con `MPS` y `DBS` requiere interfaz futura y coherencia arquitectonica. |
| UR-SIM-010 | SR-SIM-001, SR-SIM-008, SR-SIM-009, SR-SIM-021, SR-SIM-022, SR-SIM-022A, SR-SIM-023 | El realismo e inmersion dependen del modelo de vuelo, mandos, visualizacion y desempeno visual. |

## 6. Tabla consolidada con fuente, verificacion y notas
| ID | Tipo | Categoria | Descripcion | Fuente principal | Metodo de verificacion sugerido | Notas |
|---|---|---|---|---|---|---|
| UR-SIM-001 | UR | Mision | Instruccion basica de vuelo para pilotos iniciales. | Definicion usuario + Contrato | Revision documental | Nuevo enfoque explicito. |
| UR-SIM-002 | UR | Capacidades | Normales, emergencia, instrumentos, formacion y acrobacia. | Definicion usuario + Contrato + CDR SIM | Revision documental | Se mantiene como requerimiento alto nivel. |
| UR-SIM-003 | UR | Marco de diseno | Diseno alineado a `FTD Nivel 6`. | Definicion usuario + CDR SIM | Revision documental | No implica certificacion formal. |
| UR-SIM-004 | UR | Configuracion | Cabina fisica y mundo exterior virtual. | Definicion usuario + Contrato + CDR SIM | Inspeccion | Reemplaza ambiguedad previa sobre MR. |
| UR-SIM-005 | UR | Operacion instructor | Reposicionamiento, clima, fallas, monitoreo, reinicio y practica de comunicacion tipo `ATC`. | Definicion usuario + Contrato + REQ Sistema | Demostracion | Conviene fijar lista minima como baseline. |
| UR-SIM-006 | UR | Multiestacion | Entrenamiento distribuido entre 3 estaciones. | Contrato + CDR SIM | Revision documental | Consistente con entregables. |
| UR-SIM-007 | UR | Transportabilidad | Sistema transportable en entorno operativo. | Definicion usuario + REQ Sistema | Inspeccion | Debe detallarse en documento de instalacion. |
| UR-SIM-008 | UR | Mantenibilidad | Mantenimiento Nivel 1 por usuario. | Definicion usuario | Inspeccion + demostracion | Nuevo, no explicitado con suficiente claridad en linea base. |
| UR-SIM-009 | UR | Integracion | Intercambio de informacion con `MPS` y `DBS`. | CDR SIM + REQ Software | Revision documental | Formato y protocolo quedan `TBD`. |
| UR-SIM-010 | UR | Realismo | Inmersion y realismo suficiente para transferencia. | CDR SIM + REQ Sistema | Analisis experto | Debe bajarse a SR verificables. |
| SR-SIM-001 | SR | Modelo de aeronave | Emulacion realista de cabina, instrumentacion y comportamiento general `T-40 NEWEN`. | CDR SIM + REQ Sistema + REQ Hardware | Analisis + demostracion | Normalizado a `NEWEN`. |
| SR-SIM-002 | SR | Cabina fisica | Cabina fisica con controles e instrumentos para instruccion basica. | Contrato + CDR SIM | Inspeccion | Basado en definicion de cabina del contrato. |
| SR-SIM-003 | SR | Mundo exterior | Entorno exterior generado virtualmente. | Definicion usuario + Contrato + CDR SIM | Demostracion | Debe detallarse tecnologia elegida. |
| SR-SIM-004 | SR | Base fija | Simulador de base fija. | CDR SIM + Contrato | Inspeccion | Alineado a concepto actual. |
| SR-SIM-005 | SR | Entrenamiento instrumental | Soporte a instruccion visual e instrumental. | Definicion usuario + CDR SIM | Demostracion | IFR queda como capacidad basica, no avanzada. |
| SR-SIM-006 | SR | Meteorologia | Simulacion de condiciones meteorologicas y visibilidad. | CDR SIM + REQ Sistema + Contrato | Demostracion | Reutiliza baseline existente. |
| SR-SIM-007 | SR | Combustible | Simulacion de combustible y efecto en vuelo. | CDR SIM + REQ Sistema + REQ Software | Demostracion | Mantener en baseline. |
| SR-SIM-008 | SR | Force feedback | `Force feedback` en baston y pedales. | Contrato + CDR SIM + REQ Hardware | Inspeccion + demostracion | Fuerte respaldo documental. |
| SR-SIM-009 | SR | Respuesta de mandos | Ajuste de esfuerzo de control en envelope de entrenamiento. | CDR SIM + REQ Sistema | Analisis + prueba | Ayuda a alinear con `FTD Nivel 6`. |
| SR-SIM-010 | SR | Reposicionamiento | Reposicionamiento por instructor. | Definicion usuario | Demostracion | Nuevo explicito. |
| SR-SIM-011 | SR | Clima | Cambio de clima y visibilidad por instructor. | Definicion usuario + Contrato + CDR SIM | Demostracion | Ya aparecia parcialmente. |
| SR-SIM-012 | SR | Fallas | Inyeccion de fallas durante la sesion. | Definicion usuario + Contrato + CDR SIM | Demostracion | Conviene definir catalogo minimo de fallas. |
| SR-SIM-013 | SR | Monitoreo | Monitoreo en tiempo real del alumno. | Definicion usuario + Contrato | Demostracion | Puede incluir mapa, panel e info de vuelo. |
| SR-SIM-014 | SR | Reinicio | Reinicio controlado de la simulacion. | Definicion usuario | Demostracion | Nuevo explicito. |
| SR-SIM-014A | SR | Comunicacion ATC | Rol `ATC` del instructor para practica de comunicaciones con el alumno. | Definicion usuario + REQ Sistema | Demostracion | Se incorpora formalmente al baseline. |
| SR-SIM-015 | SR | Multiestacion | 3 cabinas con estacion instructor asociada. | Contrato + CDR SIM + REQ Sistema | Inspeccion | Debe quedar fijo por alcance contractual. |
| SR-SIM-016 | SR | Formacion | Vuelo en formacion entre 3 estaciones. | Definicion usuario + CDR SIM + REQ Sistema | Demostracion | Ahora se eleva a obligatorio. |
| SR-SIM-017 | SR | Control maestro | Una sola estacion instructor controla formacion. | Contrato + CDR SIM + REQ Sistema | Demostracion | Coherente con baseline previa. |
| SR-SIM-018 | SR | Acrobacia | Entrenamiento en maniobras acrobaticas. | Definicion usuario + Contrato | Demostracion | Pasa de condicional a obligatorio. |
| SR-SIM-019 | SR | Escenarios | Escenarios normales, anormales y emergencia. | Contrato + CDR SIM | Demostracion | Refuerza objetivo de entrenamiento. |
| SR-SIM-020 | SR | Integracion externa | Intercambio de informacion con `MPS` y `DBS`. | CDR SIM + REQ Software | Revision documental + prueba | Formato/protocolo `TBD`. |
| SR-SIM-021 | SR | Visualizacion interior | Visualizacion interior suficiente para instruccion basica. | CDR SIM + REQ Sistema + REQ Hardware | Inspeccion + demostracion | Se recomienda traducir luego a criterio medible. |
| SR-SIM-022 | SR | Visualizacion exterior | Vision exterior virtual implementada sobre `Varjo XR-4 Secure Edition` dentro del concepto de entrenamiento adoptado. | Definicion usuario + CDR SIM + Contrato + REQ Hardware | Demostracion | El desempeno visual final queda acotado por la plataforma seleccionada. |
| SR-SIM-022A | SR | Plataforma visual | Plataforma visual de realidad mixta basada en `Varjo XR-4 Secure Edition` o equivalente secure aprobado. | Definicion usuario | Inspeccion + revision documental | Reduce ambiguedad de implementacion. |
| SR-SIM-023 | SR | Latencia | Latencia visual objetivo `<=150 ms`. | CDR SIM | Prueba | Uno de los SR mas verificables. |
| SR-SIM-024 | SR | COTS | Uso de tecnologias `COTS` cuando aplique. | CDR SIM + REQ Sistema + REQ Software + REQ Hardware | Revision documental | Mantener como restriccion de diseno. |
| SR-SIM-025 | SR | UPS | Respaldo electrico para proteccion y apagado controlado. | CDR SIM + Contrato | Inspeccion + prueba | Muy bien respaldado. |
| SR-SIM-026 | SR | Arquitectura NEWEN | Coherencia con arquitectura integrada `NEWEN`. | CDR General + CDR SIM | Revision documental | Importante por integracion futura. |
| SR-SIM-027 | SR | Transportabilidad | Transportabilidad mediante ruedas y anclajes. | Definicion usuario + REQ Sistema | Inspeccion | Sustituye redaccion antigua de racks/Pelican como unica solucion. |
| SR-SIM-028 | SR | Accesibilidad mantencion | Accesos de revision a electronica y panel electrico. | Definicion usuario | Inspeccion | Nuevo explicito. |
| SR-SIM-029 | SR | Mantencion nivel 1 | Mantencion Nivel 1 sin desmontajes estructurales mayores. | Definicion usuario | Demostracion | Requisito importante de operacion. |
| SR-SIM-030 | SR | Instalacion | Condiciones de instalacion e infraestructura definidas. | REQ Hardware + Contrato | Inspeccion | Puede consolidarse en documento de instalacion. |

## 7. Requisitos extra recomendados para evaluar incorporacion
Estos requisitos no son estrictamente obligatorios para emitir una primera actualizacion de baseline, pero si ayudan a cerrar vacios de verificacion y operacion.

| ID propuesto | Categoria | Descripcion | Motivo |
|---|---|---|---|
| SR-SIM-031 | Registro de sesion | El sistema debera registrar bitacora de eventos de sesion e intervenciones del instructor. | Mejora trazabilidad y analisis posterior. |
| SR-SIM-032 | Escenarios preconfigurados | El sistema debera permitir cargar y recuperar escenarios de entrenamiento preconfigurados. | Acelera instruccion basica y repetibilidad. |
| SR-SIM-033 | Estado del simulador | El sistema debera indicar fallas activas, estado operativo y readiness antes de iniciar sesion. | Facilita operacion y mantenimiento. |
| SR-SIM-034 | Recuperacion segura | El sistema debera permitir detencion segura y recuperacion controlada tras falla o reinicio. | Reduce riesgo operacional. |
| SR-SIM-035 | Comunicacion instructor-alumno | El sistema debera soportar comunicacion basica entre instructor y alumno durante la sesion. | Util para entrenamiento guiado. |
| SR-SIM-036 | Catalogo minimo de fallas | El sistema debera definir un conjunto minimo de fallas entrenables. | Hace verificable el alcance de fallas. |
| SR-SIM-037 | Criterios FAT/SAT | El sistema debera tener criterios medibles de aceptacion para `FAT` y `SAT`. | Facilita aceptacion contractual. |

## 8. Riesgos y vacios pendientes
- `MPS/DBS`: falta definir estructura de datos, protocolo, direccion del flujo y criterio de sincronizacion.
- Campo visual: ya no es un riesgo abierto de concepto, pero si requiere dejar explicitamente que la cobertura visual final dependera de la plataforma `Varjo XR-4 Secure Edition` y de su configuracion aprobada para el programa.
- `FTD Nivel 6`: si el objetivo es solo alineacion de diseno, debe evitarse lenguaje de certificacion obligatoria.
- Instructor: la funcion `ATC` ya debe considerarse parte del baseline y bajar luego a requisitos funcionales detallados de interfaz y comunicacion.
- Infraestructura de instalacion: faltan umbrales concretos de energia, espacio, red, temperatura y seguridad.

## 9. Recomendacion de siguiente paso
La siguiente iteracion recomendable es convertir esta propuesta en una version formal de requisitos con:
- tipo de requisito
- prioridad
- fuente exacta
- criterio de aceptacion
- metodo de verificacion
- responsable de cierre de `TBD`

El punto mas urgente a cerrar antes de congelar baseline es la definicion de interfaz con `MPS` y `DBS`.
