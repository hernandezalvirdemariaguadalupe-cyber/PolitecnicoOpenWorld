# Plan y matriz de pruebas — Estudiante IPN (Titulación por Combate)

- **Issue:** gabrielhuav/PolitecnicoOpenWorld#163
- **PR:** gabrielhuav/PolitecnicoOpenWorld#<NUM_PR>
- **SHA base:** `7ed32539` · **SHA con defecto:** `5e3504d1` · **SHA probado/final:** `1cb007d5`
- **Entorno principal:** Windows 11, Android Studio Quail 4 Patch 1, JDK 21, emulador Pixel 8 API 34 (2 GB RAM → gama baja)
- **Antes (base `7ed32539`):** [video del selector sin el personaje](../evidencias/personajes1.mp4)
- **Datos de prueba:** partida local, sin cuenta; Developer Mode activado/desactivado desde Ajustes. No se usaron datos personales.

## 1. Criterios de aceptación

| ID | Criterio |
|---|---|
| CA1 | Con Developer Mode activo, "Estudiante IPN" aparece en el selector, se puede elegir y la pelea inicia en ESCOM con sus sprites. |
| CA2 | Con Developer Mode apagado, no aparece en el selector (ni con candado). |
| CA3 | Los demás peleadores y el arcade se comportan igual; las pruebas unitarias pasan. |

## 2. Riesgos

| ID | Riesgo | Impacto | Casos que lo cubren |
|---|---|---|---|
| R1 | Los sprites compartidos (Ipn3) se dibujan con tamaño/orientación incorrectos en pelea. | Alto: personaje no jugable. | C01, C04, C06 |
| R2 | Agregar un valor a `SfFighterId` rompe `when` exhaustivos, la campaña arcade o el selector de otros peleadores. | Alto: compilación o regresión. | C03, PU |
| R3 | El personaje se filtra a jugadores normales (aparece con candado imposible de desbloquear). | Medio: confusión del usuario. | C02 |
| R4 | Ciclo de vida: al salir/volver a la app durante la pelea se pierde la hoja compartida o se ve vacía. | Medio. | C04 |

## 3. Casos

> Estado: Aprobado / Fallido / Bloqueado / No aplica. Las evidencias están en `../evidencias/`.

### C01 — Ruta feliz (CA1, R1)
- **Autor / fecha:** Lupita Alvirde / 2026-10-01
- **SHA / versión:** `1cb007d5` / 1.0.0.18 debug
- **Dispositivo:** Pixel 8 API 34 (emulador)
- **Precondiciones:** Developer Mode ON.
- **Pasos:** 1) Abrir Titulación por Combate. 2) Abrir selector. 3) Elegir "Estudiante IPN", un rival y dificultad. 4) Iniciar pelea. 5) Caminar, saltar y atacar.
- **Esperado:** aparece en el selector; la pelea inicia en ESCOM; sprites a tamaño normal.
- **Real:** <llenar>
- **Estado:** <llenar>
- **Evidencia:** [selector](../evidencias/despues_selector.png) · [inicio](../evidencias/pelea_inicio.png) · [ataque](../evidencias/despues_ataque.png) <!-- pendiente: agregar captura -->
- **Defecto / decisión:** En `5e3504d1` se observó D1; tras `1cb007d5` <llenar>.

### C02 — Condición alterna/límite: Developer Mode OFF (CA2, R3)
- **Autor / fecha:** Lupita Alvirde / 2026-10-01 · **SHA:** `1cb007d5` · **Dispositivo:** Pixel 8 API 34
- **Pasos:** 1) Ajustes → Developer Mode OFF. 2) Abrir selector de Titulación por Combate.
- **Esperado:** "Estudiante IPN" no aparece, ni con candado.
- **Real:** <llenar> · **Estado:** <llenar>
- **Evidencia:** [ajuste apagado](../evidencias/no_developer_mode.png) · [selector sin el personaje](../evidencias/sin_devmod.png) · [selector sin el personaje 2](../evidencias/sin_devmod2.png)

### C03 — Regresión: otro peleador y pruebas unitarias (CA3, R2)
- **Autor / fecha:** Lupita Alvirde / 2026-10-01 · **SHA:** `1cb007d5` · **Dispositivo:** Pixel 8 API 34
- **Pasos:** 1) Jugar una pelea con Escomboy (u otro peleador existente). 2) Ejecutar `:app:testDebugUnitTest` desde el panel Gradle de Android Studio.
- **Esperado:** la pelea funciona igual que en `7ed32539`; todas las pruebas pasan.
- **Real:** pruebas 132/132 aprobadas (129 previas + 3 nuevas); pelea <llenar>.
- **Estado:** <llenar>
- **Evidencia:** [otro personaje](../evidencias/otro_personaje.png) · [pruebas app](../evidencias/pruebas.png) · [pruebas Estudiante IPN](../evidencias/pruebas_estudiante.png) · [pruebas shared](../evidencias/pruebas_shared.png)

### C04 — Navegación y estado (R4)
- **Autor / fecha:** Lupita Alvirde / <fecha> · **SHA:** `1cb007d5` · **Dispositivo:** Pixel 8 API 34
- **Pasos:** 1) Iniciar pelea con Estudiante IPN. 2) Botón Home, esperar 5 s, volver a la app. 3) Presionar Atrás / ✕ para salir al menú. 4) Volver a entrar y elegirlo de nuevo.
- **Esperado:** el personaje se sigue viendo correctamente; salir y volver no deja la pantalla vacía ni cierra la app. (La orientación es fija en horizontal: se registra como tal.)
- **Real:** <llenar> · **Estado:** <llenar>
- **Evidencia:** [navegación](../evidencias/nav_atras_regreso.png)

### C05 — Accesibilidad: texto ampliado / TalkBack
- **Autor / fecha:** Lupita Alvirde / <fecha> · **SHA:** `1cb007d5` · **Dispositivo:** Pixel 8 API 34
- **Pasos:** 1) Ajustes del sistema → Display size and text → Font size al máximo. 2) Abrir el selector y ubicar "Estudiante IPN".
- **Esperado:** el nombre se lee y no se corta ni se encima.
- **Real:** <llenar> · **Estado:** <llenar>
- **Limitación:** el emulador no incluye TalkBack (no aparece en Accessibility); no se pudo validar con lector de pantalla. Los botones de pelea solo exponen su letra (observación fuera de alcance).
- **Evidencia:** [texto grande](../evidencias/a11y_texto_grande.png)

### C06 — Compatibilidad / entorno: gama baja vs. gama media (R1)
- **Autor / fecha:** Lupita Alvirde / <fecha> · **SHA:** `1cb007d5`
- **Dispositivo:** <Medium Phone API 36.1 u otro AVD con >2.2 GB de RAM>
- **Pasos:** repetir C01 en un dispositivo que NO sea gama baja.
- **Esperado:** mismo tamaño de personaje que en Pixel 8 (2 GB).
- **Real:** <llenar> · **Estado:** <llenar>
- **Evidencia:** [compatibilidad](../evidencias/compat_api36.png)

### PU — Pruebas unitarias automatizadas
| Prueba | Qué verifica | Resultado en `1cb007d5` |
|---|---|---|
| `SfEstudianteIpnFighterTest` (4) | plantilla compartida y sin flip; cuadros en Idle/Walk/Run/Special; escenario ESCOM; solo en `DEV_ONLY_FIGHTERS` | Aprobadas |
| `SfSharedSheetsScaleTest` (3) | escala de recorte 1 para hojas compartidas; atlas dedicados conservan 0.5; sin cambio en gama media/alta | Aprobadas |
| `SfArcadeCampaignAuditTest` | campaña arcade completa sigue íntegra | Aprobada |
| Suite `:app:testDebugUnitTest` | total | 132/132 |

## 4. Hallazgos

### D1 — Peleador compartido se dibuja gigante/cortado en gama baja
- **Pasos:** Pixel 8 API 34 (2 GB RAM) → Developer Mode ON → elegir Estudiante IPN → iniciar pelea.
- **Esperado:** mismo tamaño que los demás. **Observado:** gigante, cortado o invisible.
- **Severidad:** Alta — el personaje no es jugable en dispositivos de gama baja.
- **Causa:** en gama baja el renderer recorta con `sheetScale = 0.5`, pero las hojas compartidas nunca se submuestrean (`SfSharedSheets.sheetFor`), así que se recortaba un cuarto de la celda.
- **Estado:** Corregido en `1cb007d5` (`SfSharedSheets.sheetScaleFor`). Preexistente para Lázaro/Granadero/Paramédico (no seleccionables).
- **Evidencia:** [antes, `5e3504d1`](../evidencias/hallazgo_ipn_gigante.png) → [después, `1cb007d5`](../evidencias/despues_fix_tamano.png) <!-- pendiente: agregar captura -->

### D2 — `./gradlew` no ejecuta en un clon limpio (preexistente)
- **Observado:** `ClassNotFoundException: org.gradle.wrapper.GradleWrapperMain`.
- **Causa:** `gradle-wrapper.jar` excluido en `PolitecnicoOpenWorld/.gitignore` (línea 76).
- **Severidad:** Baja (CI usa su propio Gradle). **Estado:** Preexistente, no se corrige en este PR; pruebas ejecutadas con el Gradle de Android Studio.

### D3 — Entorno: Android Studio previo no soportaba AGP 9.3
- Se actualizó Android Studio a Quail 4 Patch 1 sin modificar el proyecto.

## 5. Cierre del QA
- **Recomendación:** <Recomiendo / No recomiendo> integrar el cambio.
- **Evidencia que lo respalda:** C01–C06, 132/132 pruebas unitarias, checks del PR <estado>.
- **Riesgos que permanecen:** poses alpha aproximadas (Idle de 1 cuadro); sin voz propia; en línea un rival con versión anterior lo ve como Prankedy; posible conflicto trivial con #162; TalkBack no validado.
