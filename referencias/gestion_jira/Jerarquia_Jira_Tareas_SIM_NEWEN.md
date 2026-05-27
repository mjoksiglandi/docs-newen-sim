# Jerarquía Jira de Tareas - SIM NEWEN

Este documento traduce la línea base UR/SR, historias de usuario y DoD del componente SIM NEWEN a una estructura operable en Jira. La jerarquía propuesta baja desde iniciativa/proyecto hasta épicas, features, historias, tareas y subtareas por área técnica.

## 1. Convención de Jerarquía

| Nivel Jira | Uso propuesto | Ejemplo |
|---|---|---|
| Iniciativa / Proyecto | Contenedor mayor del trabajo SIM NEWEN | `SIM NEWEN - Simulador de Vuelo` |
| Epic | Capacidad mayor verificable por dominio o flujo | `EPIC-SW-01 - Núcleo de simulación y escenarios` |
| Feature | Entregable funcional o técnico dentro de una épica | `FEAT-SW-01.2 - Escenarios normales/emergencia` |
| Story | Valor observable para piloto, instructor, mantenedor, integrador o QA | `US-SIM-201 - Inyección de fallas y clima` |
| Task | Trabajo ejecutable por una disciplina | `Implementar carga de escenarios` |
| Sub-task | Paso técnico específico o evidencia requerida | `Crear casos de prueba FAT para escenario emergencia` |

## 2. Componentes Jira Recomendados

| Componente | Área responsable | Uso |
|---|---|---|
| `software` | Software SIM | Motor de simulación, HMI instructor, red, MPS/DBS, telemetría, escenarios. |
| `electronica` | Electrónica | Energía, UPS, cableado, sensores, actuadores, panel eléctrico, force feedback. |
| `firmware` | Firmware | Controladores de módulos, comunicación host, watchdog, diagnóstico, loops de control. |
| `mecanica` | Mecánica | Cabina física, base fija, paneles, soportes, transportabilidad, accesos de mantenimiento. |
| `qa-sistemas` | QA / Sistemas | Trazabilidad, FAT/SAT, evidencia, catálogo de fallas, matriz UR/SR/US/DoD. |
| `integracion` | Integración | Ensamble entre áreas, multiestación, Varjo, MPS/DBS, pruebas end-to-end. |

## 3. Épicas Jira

| Epic | Nombre | Área líder | Objetivo | Trazabilidad principal |
|---|---|---|---|---|
| `EPIC-SW-01` | Núcleo de simulación y escenarios | Software | Motor de sesión, escenarios, clima, combustible, emergencias y acrobacia. | `SR-SIM-003`, `SR-SIM-005`, `SR-SIM-006`, `SR-SIM-007`, `SR-SIM-019`, `SR-SIM-032` |
| `EPIC-SW-02` | Estación instructor y ATC | Software | HMI de instructor, fallas, reposicionamiento, monitoreo, reinicio, comunicación ATC y bitácora. | `SR-SIM-010` a `SR-SIM-015`, `SR-SIM-031`, `SR-SIM-035` |
| `EPIC-SW-03` | Multiestación e interoperabilidad | Software / Integración | Red de tres simuladores, control maestro, integración MPS/DBS e ICD. | `SR-SIM-016`, `SR-SIM-017`, `SR-SIM-018`, `SR-SIM-020`, `SR-SIM-026` |
| `EPIC-EL-01` | Arquitectura eléctrica y energía | Electrónica | Distribución eléctrica, UPS, protecciones, panel eléctrico, cableado y readiness eléctrico. | `SR-SIM-025`, `SR-SIM-028`, `SR-SIM-033`, `SR-SIM-034` |
| `EPIC-EL-02` | Mandos, sensores y actuadores | Electrónica | Bastón, pedales, sensores, force feedback, actuadores de fallas e interfaces físicas. | `SR-SIM-008`, `SR-SIM-009`, `SR-SIM-012`, `SR-SIM-022` |
| `EPIC-FW-01` | Firmware de módulos de cabina | Firmware | Controladores, buses, diagnóstico, watchdog, comandos de actuadores y telemetría local. | `SR-SIM-008`, `SR-SIM-009`, `SR-SIM-012`, `SR-SIM-033`, `SR-SIM-034` |
| `EPIC-MEC-01` | Estructura cabina y ergonomía | Mecánica | Cabina física, base fija, soportes, paneles, accesos y ergonomía de entrenamiento. | `SR-SIM-002`, `SR-SIM-004`, `SR-SIM-027`, `SR-SIM-028`, `SR-SIM-029` |
| `EPIC-MEC-02` | Integración física y transportabilidad | Mecánica | Ruedas/anclajes, layout de montaje, mantenibilidad Nivel 1 y condiciones de instalación. | `SR-SIM-027`, `SR-SIM-029`, `SR-SIM-030` |
| `EPIC-QA-01` | Verificación y aceptación | QA / Sistemas | Matriz UR-SR-US, FAT/SAT, evidencias, criterios de latencia, catálogo de fallas y manuales. | `SR-SIM-023`, `SR-SIM-036`, `SR-SIM-037` |

## 4. Backlog Jerárquico

### 4.1 `EPIC-SW-01` - Núcleo de Simulación y Escenarios

#### `FEAT-SW-01.1` - Modelo de Sesión

**Historia asociada:** como instructor quiero iniciar, pausar, reiniciar y cerrar sesiones controladas para repetir condiciones de entrenamiento con trazabilidad.

**Tareas:**
- Definir máquina de estados de sesión: preparada, en curso, pausada, reiniciando, finalizada, falla.
- Implementar comandos de sesión: start, pause, resume, reset, stop.
- Persistir configuración base de la sesión.
- Registrar eventos mínimos de sesión para debriefing.

**Subtareas / evidencia:**
- Documento corto de estados y transiciones.
- Prueba de reinicio controlado.
- Log de eventos exportable.
- DoD: la sesión puede repetirse con la misma configuración y sus eventos quedan registrados.

#### `FEAT-SW-01.2` - Escenarios Normales, Anormales y Emergencia

**Historia asociada:** como instructor quiero cargar escenarios preconfigurados para entrenar procedimientos normales, anormales y de emergencia.

**Tareas:**
- Definir catálogo inicial de escenarios.
- Implementar carga de escenario desde HMI instructor.
- Validar transición entre escenario normal, anormal y emergencia.
- Asociar cada escenario a UR/SR y criterio de aceptación.

**Subtareas / evidencia:**
- Catálogo v0 de escenarios.
- Dataset de prueba por tipo de escenario.
- Evidencia de carga sin reinicio completo cuando aplique.
- DoD: cada escenario definido puede cargarse, ejecutarse y cerrarse con resultado verificable.

#### `FEAT-SW-01.3` - Clima y Visibilidad

**Historia asociada:** como instructor quiero modificar clima y visibilidad durante la sesión para evaluar adaptación del alumno.

**Tareas:**
- Definir variables mínimas: viento, visibilidad, nubosidad, precipitación si aplica.
- Exponer controles en la estación instructor.
- Aplicar cambios al motor de simulación.
- Registrar cambios en bitácora.

**Subtareas / evidencia:**
- Matriz de variables climáticas soportadas.
- Prueba de cambio en tiempo de sesión.
- Captura o registro del efecto observable.
- DoD: los cambios son visibles para el alumno y quedan trazados.

#### `FEAT-SW-01.4` - Combustible y Performance

**Historia asociada:** como piloto alumno quiero que el combustible afecte el rendimiento para entrenar gestión básica de vuelo.

**Tareas:**
- Modelar consumo y estado de combustible.
- Conectar el estado al modelo de performance.
- Mostrar o exponer variables relevantes a instructor/telemetría.
- Crear pruebas de variación de combustible.

**Subtareas / evidencia:**
- Parámetros iniciales de consumo.
- Prueba de efecto sobre rendimiento.
- Registro de telemetría.
- DoD: la variación de combustible afecta parámetros definidos del vuelo.

### 4.2 `EPIC-SW-02` - Estación Instructor y ATC

#### `FEAT-SW-02.1` - HMI Instructor

**Historia asociada:** como instructor quiero operar fallas, clima, reposicionamiento y reinicio desde una sola estación.

**Tareas:**
- Diseñar flujo operativo de HMI.
- Implementar paneles de clima, fallas, reposicionamiento y reinicio.
- Definir perfiles o permisos mínimos.
- Validar usabilidad con flujo de sesión real.

**Subtareas / evidencia:**
- Wireframe operativo.
- Lista de comandos disponibles.
- Prueba de ejecución por instructor.
- DoD: el instructor opera funciones mínimas sin intervención técnica externa.

#### `FEAT-SW-02.2` - Monitoreo del Alumno

**Historia asociada:** como instructor quiero monitorear el estado de vuelo y desempeño del alumno en tiempo real.

**Tareas:**
- Definir telemetría mínima.
- Implementar panel de estado.
- Agregar eventos o alertas relevantes.
- Validar que el monitoreo no degrade la simulación.

**Subtareas / evidencia:**
- Lista de variables monitoreadas.
- Prueba de actualización en tiempo real.
- Registro de impacto de performance.
- DoD: el instructor visualiza estado de vuelo durante la sesión.

#### `FEAT-SW-02.3` - ATC y Comunicaciones Instructor-Alumno

**Historia asociada:** como instructor quiero actuar como ATC para practicar comunicaciones con el alumno.

**Tareas:**
- Definir flujo de comunicación instructor-alumno.
- Integrar canal de voz/intercom o interfaz equivalente.
- Registrar eventos relevantes de comunicación.
- Validar operación durante sesión activa.

**Subtareas / evidencia:**
- Diagrama de flujo de comunicación.
- Prueba de canal activo durante sesión.
- Registro de evento de comunicación.
- DoD: la comunicación opera sin bloquear telemetría ni controles principales.

### 4.3 `EPIC-SW-03` - Multiestación e Interoperabilidad

#### `FEAT-SW-03.1` - Sesión de Tres Estaciones

**Historia asociada:** como instructor líder quiero conectar tres simuladores para dirigir entrenamiento de vuelo en formación.

**Tareas:**
- Definir sincronización mínima entre estaciones.
- Implementar configuración o descubrimiento de nodos.
- Sincronizar estado básico de formación.
- Probar sesión con tres estaciones o simuladores de nodo.

**Subtareas / evidencia:**
- Especificación de sincronización mínima.
- Prueba de tres nodos.
- Registro de latencia o desfase.
- DoD: las tres estaciones comparten estado operativo de formación.

#### `FEAT-SW-03.2` - Control Maestro de Instructor

**Historia asociada:** como instructor líder quiero que solo una estación tenga control maestro durante formación.

**Tareas:**
- Definir mecanismo de arbitraje.
- Bloquear controles globales en estaciones secundarias.
- Gestionar pérdida o transferencia de líder.
- Registrar cambios de control maestro.

**Subtareas / evidencia:**
- Matriz de permisos por rol.
- Prueba de bloqueo de controles secundarios.
- Prueba de pérdida de líder.
- DoD: solo una estación puede controlar escenario global.

#### `FEAT-SW-03.3` - ICD MPS/DBS

**Historia asociada:** como integrador quiero una interfaz definida con MPS y DBS para cerrar el flujo planificación-simulación-debriefing.

**Tareas:**
- Definir datos requeridos desde MPS.
- Definir datos exportados hacia DBS.
- Definir formato, versionado, errores y responsabilidad de cada sistema.
- Crear simuladores o fixtures de prueba.

**Subtareas / evidencia:**
- ICD v0.1 revisado.
- Ejemplos de payload o archivo.
- Casos de error.
- DoD: la interfaz deja de estar `TBD` para el primer flujo aprobado.

#### `FEAT-SW-03.4` - Importación y Exportación Operacional

**Historia asociada:** como integrador quiero importar planes desde MPS y exportar telemetría a DBS.

**Tareas:**
- Implementar importación de plan de misión/vuelo.
- Implementar exportación de telemetría y eventos.
- Validar versionado de datos.
- Probar errores de formato, ausencia de datos y recuperación.

**Subtareas / evidencia:**
- Dataset de referencia MPS.
- Dataset de referencia DBS.
- Resultado de prueba end-to-end.
- DoD: el flujo MPS-SIM-DBS corre con datos de referencia y manejo de errores.

### 4.4 `EPIC-EL-01` - Arquitectura Eléctrica y Energía

#### `FEAT-EL-01.1` - Distribución Eléctrica

**Historia asociada:** como integrador de electrónica quiero una arquitectura eléctrica documentada para montar y mantener la cabina de forma segura.

**Tareas:**
- Crear diagrama unifilar.
- Seleccionar protecciones, conectores y rutas de cableado.
- Definir separación de potencia, señales y comunicaciones.
- Revisar compatibilidad con accesos de mantenimiento.

**Subtareas / evidencia:**
- Diagrama eléctrico v0.
- BOM preliminar.
- Revisión de seguridad.
- DoD: el diseño queda listo para prototipo controlado.

#### `FEAT-EL-01.2` - UPS y Apagado Controlado

**Historia asociada:** como operador quiero respaldo eléctrico para proteger el sistema ante fallas de energía.

**Tareas:**
- Dimensionar UPS por unidad de computación y cargas críticas.
- Definir señalización de estado de UPS.
- Implementar secuencia de apagado controlado.
- Probar corte de energía.

**Subtareas / evidencia:**
- Cálculo de autonomía mínima.
- Prueba de corte.
- Registro de apagado controlado.
- DoD: el sistema apaga sin pérdida crítica de estado.

#### `FEAT-EL-01.3` - Readiness Eléctrico

**Historia asociada:** como instructor o mantenedor quiero saber si la cabina está lista antes de iniciar sesión.

**Tareas:**
- Definir estados eléctricos monitoreables.
- Sensar protecciones o señales críticas.
- Reportar estado a HMI o panel de readiness.
- Definir códigos de falla.

**Subtareas / evidencia:**
- Lista de señales readiness.
- Prueba de falla activa.
- Visualización de estado.
- DoD: el preflight muestra energía, protecciones y fallas relevantes.

### 4.5 `EPIC-EL-02` - Mandos, Sensores y Actuadores

#### `FEAT-EL-02.1` - Force Feedback en Bastón y Pedales

**Historia asociada:** como piloto alumno quiero sentir resistencia física variable en mandos primarios.

**Tareas:**
- Seleccionar actuadores y drivers.
- Construir banco de cargas.
- Definir curvas de esfuerzo.
- Integrar comandos desde software/firmware.

**Subtareas / evidencia:**
- Banco de prueba operativo.
- Curvas esfuerzo-envelope.
- Prueba de límites seguros.
- DoD: bastón y pedales responden a comandos medidos dentro de tolerancia acordada.

#### `FEAT-EL-02.2` - Paneles y Sensores

**Historia asociada:** como sistema SIM quiero leer entradas físicas de cabina de forma estable.

**Tareas:**
- Mapear entradas y salidas por panel.
- Prototipar panel frontal, consola izquierda y consola derecha según alcance.
- Validar rebote, calibración y estabilidad.
- Documentar conectores y señales.

**Subtareas / evidencia:**
- Mapa I/O.
- Prueba de lectura estable.
- Registro de calibración.
- DoD: las entradas físicas se leen con estabilidad definida.

#### `FEAT-EL-02.3` - Actuación de Fallas

**Historia asociada:** como instructor quiero inyectar fallas con efecto físico o funcional observable.

**Tareas:**
- Definir fallas con actuación física y fallas solo software.
- Diseñar circuito seguro para actuadores.
- Probar actuador de disyuntor o señal equivalente.
- Implementar estado seguro ante falla eléctrica.

**Subtareas / evidencia:**
- Lista de fallas actuadas.
- Prueba de fail-safe.
- Registro de efecto observable.
- DoD: la falla simulada no introduce riesgo para usuario ni equipo.

### 4.6 `EPIC-FW-01` - Firmware de Módulos de Cabina

#### `FEAT-FW-01.1` - Comunicación Módulo-Host

**Historia asociada:** como software SIM quiero comunicarme con módulos de cabina de forma robusta.

**Tareas:**
- Definir protocolo módulo-host.
- Implementar parser y serialización.
- Agregar reconexión y manejo de pérdida temporal.
- Medir latencia de comunicación.

**Subtareas / evidencia:**
- Especificación de protocolo.
- Prueba de reconexión.
- Log de latencia.
- DoD: el módulo se recupera ante pérdida temporal de enlace.

#### `FEAT-FW-01.2` - Control de Force Feedback

**Historia asociada:** como piloto alumno quiero que la fuerza de mandos sea segura y coherente con el vuelo simulado.

**Tareas:**
- Implementar loop de control.
- Definir límites, rampas y saturación.
- Enviar telemetría de esfuerzo.
- Validar estado seguro ante comandos fuera de rango.

**Subtareas / evidencia:**
- Prueba de límites.
- Prueba de saturación.
- Telemetría registrada.
- DoD: el control opera dentro de límites seguros.

#### `FEAT-FW-01.3` - Diagnóstico y Watchdog

**Historia asociada:** como mantenedor quiero detectar fallas de módulo antes o durante la sesión.

**Tareas:**
- Implementar autotest.
- Definir códigos de error.
- Implementar watchdog.
- Reportar estado seguro al host.

**Subtareas / evidencia:**
- Tabla de códigos de error.
- Prueba de watchdog.
- Evento de falla reportado.
- DoD: una falla de firmware lleva a estado seguro y queda reportada.

### 4.7 `EPIC-MEC-01` - Estructura Cabina y Ergonomía

#### `FEAT-MEC-01.1` - Arquitectura de Cabina

**Historia asociada:** como piloto alumno quiero una cabina física representativa y cómoda para instrucción básica.

**Tareas:**
- Definir layout ergonómico.
- Revisar antropometría y accesos.
- Definir interfaces con visual, mandos y paneles.
- Validar interferencias físicas.

**Subtareas / evidencia:**
- Layout de cabina.
- Revisión de ergonomía.
- Lista de interferencias/resoluciones.
- DoD: el piloto accede controles principales sin interferencias.

#### `FEAT-MEC-01.2` - Base Fija y Soportes

**Historia asociada:** como sistema SIM quiero una estructura estable de base fija para uso repetido.

**Tareas:**
- Predimensionar estructura base.
- Diseñar soportes de cabina, visor y controles.
- Revisar rigidez y vibración.
- Validar montaje de equipos.

**Subtareas / evidencia:**
- Modelo o plano preliminar.
- Revisión de rigidez.
- Inspección de montaje.
- DoD: la estructura se mantiene estable durante operación prevista.

#### `FEAT-MEC-01.3` - Paneles Modulares y Accesos

**Historia asociada:** como mantenedor quiero acceder a electrónica y panel eléctrico sin desmontajes mayores.

**Tareas:**
- Definir módulos desmontables.
- Diseñar puntos de fijación.
- Definir accesos de revisión.
- Validar tiempo y herramientas de desmontaje Nivel 1.

**Subtareas / evidencia:**
- Lista de módulos.
- Procedimiento de acceso.
- Prueba de desmontaje.
- DoD: un módulo puede retirarse para mantenimiento Nivel 1 sin desmontaje estructural mayor.

### 4.8 `EPIC-MEC-02` - Integración Física y Transportabilidad

#### `FEAT-MEC-02.1` - Ruedas, Anclajes y Nivelación

**Historia asociada:** como operador quiero trasladar y fijar el simulador de forma segura dentro del entorno operativo.

**Tareas:**
- Seleccionar ruedas, frenos, anclajes y niveladores.
- Diseñar puntos de izaje o traslado si aplican.
- Probar traslado corto.
- Probar bloqueo y nivelación.

**Subtareas / evidencia:**
- Selección de componentes.
- Prueba de traslado.
- Checklist de fijación.
- DoD: la cabina se traslada y fija sin comprometer estabilidad.

#### `FEAT-MEC-02.2` - Condiciones de Instalación

**Historia asociada:** como integrador quiero saber si el sitio está listo antes de instalar el SIM.

**Tareas:**
- Definir espacio mínimo y accesos.
- Definir puntos de energía y red.
- Definir condiciones de temperatura, seguridad y operación.
- Crear checklist de instalación.

**Subtareas / evidencia:**
- Checklist de sitio.
- Matriz de condiciones mínimas.
- Registro de aprobación de sitio.
- DoD: el sitio puede aprobarse antes del despliegue.

#### `FEAT-MEC-02.3` - Mantenibilidad Nivel 1

**Historia asociada:** como usuario entrenado quiero ejecutar inspecciones básicas sin soporte especializado.

**Tareas:**
- Definir tareas de mantenimiento Nivel 1.
- Etiquetar accesos, módulos y puntos de revisión.
- Crear checklist de inspección.
- Validar procedimiento con usuario/mantenedor.

**Subtareas / evidencia:**
- Checklist Nivel 1.
- Evidencia de acceso a panel eléctrico/electrónica.
- Registro de validación.
- DoD: el usuario entrenado ejecuta inspección básica con procedimiento definido.

### 4.9 `EPIC-QA-01` - Verificación y Aceptación

#### `FEAT-QA-01.1` - Matriz de Trazabilidad

**Historia asociada:** como QA quiero mapear UR, SR, historias y DoD para verificar cobertura completa.

**Tareas:**
- Mapear UR-SR-US-DoD.
- Asignar método de verificación por requisito.
- Definir evidencia esperada.
- Identificar requisitos sin cobertura.

**Subtareas / evidencia:**
- Matriz de trazabilidad v0.
- Lista de brechas.
- Responsable por brecha.
- DoD: 100% de UR/SR tienen evidencia esperada o brecha explícita.

#### `FEAT-QA-01.2` - Plan FAT

**Historia asociada:** como cliente/QA quiero ejecutar FAT con criterios pass/fail objetivos.

**Tareas:**
- Definir casos de prueba FAT.
- Asociar cada caso a SR.
- Definir evidencia y formato de registro.
- Crear flujo de no conformidades.

**Subtareas / evidencia:**
- Plan FAT.
- Plantilla de resultado.
- Registro de incidencias.
- DoD: FAT puede ejecutarse con datos, responsables y criterios claros.

#### `FEAT-QA-01.3` - Plan SAT

**Historia asociada:** como cliente/QA quiero verificar el sistema instalado en el entorno final.

**Tareas:**
- Definir checklist de instalación.
- Definir pruebas en sitio.
- Definir criterios de cierre de pendientes.
- Validar operación integrada.

**Subtareas / evidencia:**
- Plan SAT.
- Checklist de instalación.
- Registro de pruebas en sitio.
- DoD: SAT demuestra operación en entorno final.

#### `FEAT-QA-01.4` - Catálogo de Fallas

**Historia asociada:** como instructor y QA quiero un conjunto mínimo de fallas entrenables con efectos verificables.

**Tareas:**
- Definir lista mínima de fallas.
- Clasificar fallas por tipo: software, electrónica, panel, motor de simulación, comunicaciones.
- Definir efecto esperado por falla.
- Crear prueba de aceptación por falla.

**Subtareas / evidencia:**
- Catálogo de fallas v0.
- Matriz falla-efecto.
- Pruebas por falla.
- DoD: las fallas entrenables quedan verificadas y documentadas.

## 5. Historias Transversales Prioritarias

| Historia | Actor | Valor | Épicas relacionadas | Prioridad |
|---|---|---|---|---|
| `US-SIM-101` | Piloto alumno | Sentir resistencia física variable en bastón y pedales. | `EPIC-EL-02`, `EPIC-FW-01`, `EPIC-QA-01` | Alta |
| `US-SIM-102` | Piloto alumno | Usar realidad mixta con cabina física y exterior virtual. | `EPIC-SW-01`, `EPIC-MEC-01`, `EPIC-QA-01` | Alta |
| `US-SIM-201` | Instructor | Inyectar fallas, clima y reposicionamientos. | `EPIC-SW-02`, `EPIC-EL-02`, `EPIC-FW-01` | Alta |
| `US-SIM-202` | Instructor líder | Conectar tres simuladores con control maestro. | `EPIC-SW-03`, `EPIC-QA-01` | Alta |
| `US-SIM-203` | Instructor | Actuar como ATC y comunicarse con el alumno. | `EPIC-SW-02` | Media |
| `US-SIM-301` | Mantenedor | Acceder a electrónica y panel eléctrico por módulos. | `EPIC-EL-01`, `EPIC-MEC-01`, `EPIC-MEC-02` | Alta |
| `US-SIM-401` | Integrador | Intercambiar planes, eventos y telemetría con MPS/DBS. | `EPIC-SW-03`, `EPIC-QA-01` | Alta |
| `US-SIM-501` | QA / Cliente | Ejecutar FAT/SAT con evidencia objetiva. | `EPIC-QA-01` | Alta |

## 6. Propuesta de Sprints Iniciales

| Sprint | Foco | Épicas / Features | Resultado esperado |
|---|---|---|---|
| Sprint 0 | Preparación Jira y baseline | Todas | Proyecto Jira configurado, componentes creados, épicas cargadas, matriz inicial UR/SR/US. |
| Sprint 1 | Arquitectura base y prototipos críticos | `FEAT-SW-01.1`, `FEAT-EL-01.1`, `FEAT-FW-01.1`, `FEAT-MEC-01.1` | Base de sesión, arquitectura eléctrica, protocolo módulo-host y layout inicial. |
| Sprint 2 | Instructor y controles físicos | `FEAT-SW-02.1`, `FEAT-EL-02.1`, `FEAT-FW-01.2`, `FEAT-MEC-01.2` | HMI instructor inicial, banco force feedback y estructura estable. |
| Sprint 3 | Escenarios, fallas y readiness | `FEAT-SW-01.2`, `FEAT-SW-02.2`, `FEAT-EL-01.3`, `FEAT-FW-01.3`, `FEAT-QA-01.4` | Escenarios/fallas iniciales, monitoreo, diagnóstico y catálogo de fallas. |
| Sprint 4 | Multiestación e interfaces | `FEAT-SW-03.1`, `FEAT-SW-03.2`, `FEAT-SW-03.3` | Tres nodos/simuladores conectados, control maestro e ICD MPS/DBS v0.1. |
| Sprint 5 | Integración y aceptación | `FEAT-SW-03.4`, `FEAT-QA-01.1`, `FEAT-QA-01.2`, `FEAT-QA-01.3` | Flujo MPS-SIM-DBS de referencia y planes FAT/SAT listos. |

## 7. Campos Jira Recomendados por Ticket

| Campo | Recomendación |
|---|---|
| Summary | `Área - verbo + entregable`, por ejemplo `Software - implementar carga de escenarios de emergencia`. |
| Description | Incluir objetivo, trazabilidad UR/SR, alcance, fuera de alcance y evidencia esperada. |
| Component/s | Usar uno o más componentes definidos en este documento. |
| Labels | `newen`, `sim`, `ur-sr`, `fat-sat`, `mps-dbs`, `force-feedback`, según aplique. |
| Acceptance Criteria | Usar DoD medible: revisión, inspección, demostración, prueba o análisis. |
| Links | Enlazar al UR/SR, historia relacionada, documento de referencia y dependencia técnica. |
| Definition of Done | Evidencia cargada, revisión aprobada, prueba ejecutada, trazabilidad actualizada. |

## 8. Dependencias Críticas

| Dependencia | Bloquea | Decisión requerida |
|---|---|---|
| ICD MPS/DBS | `FEAT-SW-03.4`, pruebas end-to-end, DBS | Formato, protocolo, versionado, errores y responsables. |
| Presupuesto de latencia visual | `US-SIM-102`, FAT visual | Condición de prueba, método de medición, presupuesto por componente. |
| Catálogo mínimo de fallas | `FEAT-SW-02.1`, `FEAT-EL-02.3`, `FEAT-QA-01.4` | Lista mínima, efecto esperado, tipo de actuación y criticidad. |
| Protocolo módulo-host | `FEAT-FW-01.1`, `FEAT-EL-02.2`, readiness | Mensajes, frecuencia, reconexión, errores y versionado. |
| Diseño mecánico de accesos | `FEAT-MEC-01.3`, `FEAT-MEC-02.3` | Módulos, herramientas permitidas, tiempos de acceso y checklist Nivel 1. |

## 9. Plantilla de Ticket Jira

```markdown
## Objetivo
Describir el resultado verificable del ticket.

## Trazabilidad
- UR:
- SR:
- Historia:
- Épica:
- Feature:

## Alcance
- 

## Fuera de alcance
- 

## Criterios de aceptación / DoD
- [ ] Evidencia documental o técnica generada.
- [ ] Prueba, inspección, demostración o análisis ejecutado.
- [ ] Resultado trazado contra UR/SR.
- [ ] Dependencias o riesgos actualizados.

## Evidencia esperada
- 

## Dependencias
- 
```

## 10. Nota de Workflow Git/Jira

Para cambios en el repositorio, se recomienda usar ramas y commits trazables a Jira:

- Rama: `feature/JIRA-ID-descripcion-corta`
- Commit docs: `📚 JIRA-ID: documentar jerarquia jira sim`
- PR: incluir ticket Jira, resumen, archivos cambiados, riesgos y validación.

La clave Jira real debe definirse antes de hacer commit/push de cambios nuevos asociados a esta jerarquía.
