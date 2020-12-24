# [Git](https://git-scm.com/)

## Subir cambios

| Comando                 | Descripción           |
| -------------           |:-------------         |
| `git status`              | Verificar el estado del repositorio local (compara). |
| `git add --all`           | Agregar todos los nuevos cambios a 'por cambiar'. |
| `git commit -m "mensaje"` | Generar un commit. Confirma los cambios con su respectivo mensaje. |
| `git push`                | Enviar los cambios al repositorio en GitHub. |
| `git revert hash_commit` | Revertir un commit. |

## Manejo de branches (ramas de trabajo)

| Comando                     | Descripción           |
| -------------               |:-------------         |
| `git checkout -b new_branch`  | Crea nueva branch. |
| `git checkout branch`         | Cambiarse de branch. |
| `git branch`                  | Ver todas las branches. |
| `git branch -d branch`        | Eliminar branch |
| `git push origin branch`      | Análogo a git push. En github hay que hacer el pull request y el merge. |

## Borrar información sensible de todas las versiones

[Documentación oficial de Github](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/removing-sensitive-data-from-a-repository)