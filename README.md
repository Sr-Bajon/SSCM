# SSCM

Simple Software Configuration Management with GIT

- Una sola rama, MASTER
- Multiples ramas de trabajo
- Uso de TAGS en MASTER para marcar releases u otros hitos.
- REBASE todos los días la rama MASTER en tu feature para que no se quede muy retrasada y la integración final sea mas facil.
- La integración con MASTER se hace mediante merge-request, o si no es necesario mediante merge no-ff para no dejar commit de merge.
- Antes de integrar se debe dejar un solo commit en la feature mediante REBASE que explique detalladamente la feature o bugfix, de forma que el historial de commits de MASTER sea plano y pueda servir a modo de changelog.

# Flujo de trabajo

## Crear ramas de trabajo
- Crear repositorio, proteger MASTER si se quiere que los merges se hagan por merge-request

`git checkout -b nombreFeature`

La convención de nombre de ramas habrá que definirla, si por ejemplo tenemos una herramienta de ticketing podriamos usar un identificador ademas del nombre.

`git checkout -b nombreFeature-#142`

## Trabajando en nuestra rama
- Trabajamos en nuestra rama, aplicamos buenas practicas a la hora de hacer commits, commitear a menudo y por unidades de trabajo completas.

- Hacemos git rebase sobre la rama MASTER a menudo para no quedarnos desfasados y que la integración final sea mas facil.

`git checkout MASTER`
`git pull`
`git checkout myBranch`
`git rebase MASTER`

## Integrar con master
- Una vez hemos acabado nuestra feature la integramos con MASTER, el proceso es igual que el anterior pero esta vez haremos rebase interactivo para mejorar nuestro historial de commits.

`git checkout MASTER`
`git pull`
`git checkout myBranch`
`git rebase -i MASTER`

En la ventana interactiva aparecerán sólo mis commits, el objetivo es unir todos los commits en uno que explique claramente la feature, de forma que al integrarla en master tengamos un historial claro de commits, en el que cada uno será una feature, hotfix, bugfix, etc.

Ver anexo, como escribir el commit de feature.

> si queremos subir nuestra rama nos dará error pues hemos cambiado el historial de commits, si queremos podemos subirla con
> `git push -u origin miRama --force-with-lease`

Ahora tenemos dos opciones:
- Si trabajamos con pull-request, lo creamos y será aceptado o no por el administrador, si es aceptado podemos borrar nuestra rama feature local y actualizarnos master con los ultimos cambios ya integrados.
- Si trabajamos con merge, haremos un merge no fast fordward en master para integrar nuestra feature sin crear un commit de merge.

`git checkout master`
`git pull`
`git merge miRama --no-commit --no-ff`

Y si todo ha ido bien.

`git push origin master`

## Release

Una release será una foto del estado actual de master, para ello haremos uso de TAGS.

Los TAGS los nombraremos siguiendo la nomenclatura SEMSERVER. X.Y.Z, mayor, minnor, patch.

`git tag -a v0.1.0 -m "release inicial"`
`git push origin --tags`


## Commit de feature.
https://wiki.openstack.org/wiki/GitCommitMessages
