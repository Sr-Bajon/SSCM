# SSCM

Simple Software Configuration Management with GIT

- Una sola rama, DEVELOPMENT
- Multiples ramas de trabajo
  - FEATURE-nombre
  - BUGFIX-nombre
- Uso de TAGS en DEVELOPMENT para marcar releases u otros hitos.
- REBASE todos los días la rama DEVELOPMENT en tu feature para que no se quede muy retrasada y la integración final sea mas facil.
- La integración con DEVELOPMENT se hace mediante merge-request, o si no es necesario mediante merge no-ff para no dejar commit de merge.
- Antes de integrar se debe dejar un solo commit en la feature mediante REBASE que explique detalladamente la feature o bugfix, de forma que el historial de commits de development sea plano y pueda servir a modo de changelog.
