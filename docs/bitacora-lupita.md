# Bitácora — Lupita Alvirde (@hernandezalvirdemariaguadalupe-cyber)

## Commits
| SHA | Mensaje | Tipo |
|---|---|---|
| `1cb007d5` | feat: add Estudiante IPN as dev-only shared fighter | Implementación + pruebas |
| `5e3504d1` | fix: don't apply low-end sheet scale to shared fighter sheets | Corrección de D1 + prueba |

## Registro
| Fecha | Actividad | Resultado |
|---|---|---|
| 2026-09-30 | Fork, clon y SHA base `7ed32539`. | OK |
| 2026-09-30 | Android Studio no soportaba AGP 9.3; se actualizó a Quail 4 Patch 1. | Sync exitoso sin modificar el proyecto |
| 2026-09-30 | Ejecución de la versión base en Pixel 8 API 34. | App funcional |
| 2026-09-30 | Se evaluaron otras propuestas (accesibilidad de botones con TalkBack, validación de IP LAN) y se descartaron por falta de TalkBack en el emulador y por preferencia del alcance. | Se eligió el peleador Estudiante IPN |
| 2026-10-01 | Revisión de issues duplicados (#150, #162 relacionados, no duplicados). Issue #163. | OK |
| 2026-10-01 | Rama `feature/sf-estudiante-ipn-fighter`; `./gradlew` falla (D2); pruebas con Gradle de Android Studio: 129/129. | OK |
| 2026-10-01 | QA manual en `1cb007d5`: el personaje se ve gigante (D1). | Defecto registrado |
| 2026-10-01 | Corrección en `5e3504d1`; pruebas 132/132; reprueba de C01. | Corregido |
| 2026-10-01 | Draft PR #164; PR Quality Gate run #154 en *Action required* (aprobación del mantenedor). | Bloqueo externo documentado |
| 2026-10-01 | Casos C01–C05 en `5e3504d1`. | Aprobados |
| 2026-10-01 | C06: Medium Phone API 36.1 no arrancó (proceso colgado); se repitió C01 con el sistema en español. | Aprobado |
| <fecha> | Revisión al PR de <compañero>: <caso reproducido>. | <liga> |

## Casos ejecutados
C01, C02, C03, C04, C05, C06 (ver [pruebas.md](pruebas.md)).

## Uso de herramientas de IA
- **Claude (Anthropic):** análisis del enunciado, revisión del código del repositorio para proponer el cambio, diagnóstico de errores de entorno, borradores de los parches, de las pruebas unitarias y de la documentación.
- **Revisión propia:** apliqué, compilé y revisé cada cambio; ejecuté las pruebas y todos los casos manuales en mi entorno; las evidencias son capturas reales de mis ejecuciones.
