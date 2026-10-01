# Primer examen parcial — PR con aseguramiento de calidad

**Unidad de aprendizaje:** Desarrollo de aplicaciones móviles nativas · **Grupo:** 7CV4 · **Periodo:** 2027-1

## Equipo
| Integrante | Usuario de GitHub | PR |
|---|---|---|
| Lupita Alvirde | @<usuario> | gabrielhuav/PolitecnicoOpenWorld#<NUM_PR> |
| <integrante 2> | @<usuario> | <PR> |

## Objetivo y alcance
Agregar al modo **Titulación por Combate** un peleador nuevo, **"Estudiante IPN"**, reutilizando los sprites existentes del NPC de interiores `Ipn3`, seleccionable solo con Developer Mode.
**Fuera de alcance:** arcade y desbloqueos, arte nuevo, voces, IA propia.

## Referencias del cambio
| Concepto | Valor |
|---|---|
| Issue | gabrielhuav/PolitecnicoOpenWorld#163 |
| Pull Request | gabrielhuav/PolitecnicoOpenWorld#<NUM_PR> |
| Rama | `feature/sf-estudiante-ipn-fighter` |
| SHA base | `7ed325393f82872c2be94ff2ada46948efa19152` |
| SHA final entregado | `1cb007d5<completo>` |

## Matriz de pruebas y evidencias
- [Plan, riesgos, casos y hallazgos](docs/pruebas.md)
- [Evidencias](evidencias/)

## Checks (CI)
| Check | Estado | SHA / ejecución | Registro |
|---|---|---|---|
| PR Quality Gate — unit-tests | <✅/❌/bloqueado> | `1cb007d5` | <liga> |
| PR Quality Gate — detekt | <✅/❌/bloqueado> | `1cb007d5` | <liga> |

**Qué comprueban:** build debug de Android, pruebas unitarias de `app` y `shared`, nombres de prueba compatibles con Kotlin/Native y análisis estático con detekt.
**Qué queda fuera:** CI usa `MAPS_API_KEY` vacío y no tiene `google-services.json` (mapas y Firebase no se prueban); no ejecuta la app ni pruebas de UI, por eso se hizo QA manual.

## Revisión técnica
- Revisión recibida de: <compañero> — <liga al comentario>
- Revisión hecha por mí al PR de: <compañero> — <liga al comentario>

## Conclusiones
<2-4 líneas: qué se logró, el defecto D1 encontrado y corregido, recomendación final>

## Bitácora
- [Bitácora de Lupita Alvirde](docs/bitacora-lupita.md)

## Referencias
- README de POW y `.github/workflows/pr-quality-gate.yml` del repositorio original (revisados el 2026-09-28).
- Material del curso: prácticas 1 a 3, Entrega 1 del Proyecto.
