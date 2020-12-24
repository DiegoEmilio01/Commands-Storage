# [Git](https://git-scm.com/)

## Subir cambios

| Comando                   | Descripción                                                         |
| -------------             | :-------------                                                      |
| `git status`              | Verificar el estado del repositorio local (compara).                |
| `git add --all`           | Agregar todos los nuevos cambios a 'por cambiar'.                   |
| `git commit -m "mensaje"` | Generar un commit. Confirma los cambios con su respectivo mensaje.  |
| `git push`                | Enviar los cambios al repositorio en [GitHub](https://github.com/).                        |
| `git revert hash_commit`  | Revertir un commit.                                                 |

## Manejo de branches (ramas de trabajo)

| Comando                       | Descripción                                                           |
| -------------                 |:-------------                                                         |
| `git checkout -b nombre`      | Crea nueva branch `nombre`.                                           |
| `git checkout nombre`         | Cambiarse a branch `nombre`.                                          |
| `git branch`                  | Ver todas las branches.                                               |
| `git branch -d nombre`        | Eliminar branch `nombre`.                                             |
| `git push origin nombre`      | Análogo a `git push` (luego hay que hacer el pull request y el merge).  |

## Borrar información sensible de todas las versiones

[Documentación oficial de Github](https://docs.github.com/es/free-pro-team@latest/github/authenticating-to-github/removing-sensitive-data-from-a-repository)