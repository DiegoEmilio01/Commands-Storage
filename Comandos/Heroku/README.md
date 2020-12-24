# [Heroku](https://www.heroku.com/)

Ejecutar comandos dentro del repositorio de la app.

| Comando                                   | Descripción                           |
| -------------                             | :-------------                        |
| `heroku login`                            | Iniciar sesión Heroku.                |
| `heroku create nombre`                    | Crear app `nombre` en Heroku.         |
| `heroku logs --tail`                      | Ve los logs recibidos por la app.     |
| `git push heroku master`                  | Pushear a Heroku.                     |
| `heroku open`                             | Abre el link de la app en Heroku.     |
| `heroku local web`                        | Corre la app localmente.              |
| `heroku pg:psql`	                        | Entrar a la base de datos PSQL de la app en Heroku.     |
| `heroku pg:backups:capture --app nombre`  | Crea un backup. Se debe guardar el nombre del respaldo. |
| `heroku pg:backups --app nombre`          | Imprime los backups.                  |
| `heroku pg:backups:restore b101 DATABASE_URL --app nombre` | Restaurar un backup. |

## Usando [Ruby on Rails](../RVM_Rails) y [Rake](https://github.com/ruby/rake)

Resumen del procedimiento:

- Crear el `Procfile` con `web:bundle exec puma -C config/puma.rb` dentro de ella.
- Loguearse a Heroku.
- Crear app Heroku
- Setear lenguaje.
- Pushear a Heroku.
- Migrar la base de datos.
- Abrir la app.

| Comando                       | Descripción                                             |
| -------------                 | :-------------                                          |
| `heroku buildpacks:set -a nombre heroku/ruby` | Setea el lenguaje de la app `nombre`.   |
| `heroku run rake db:migrate`  | Corre las migraciones en la base de datos de Heroku.    |
| `heroku run rake db:seed`     | Corre la seed en Heroku.                                |
| `heroku git:remote -a nombre` | Setear que la app está dentro de un repositorio de Git. |

## Usando [Node.js](../NVM_Yarn_Yeoman) y [Sequelize](../NVM_Yarn_Yeoman)

El procedimiento es similar (ver documentación en Heroku).

| Comando                                         | Descripción                           |
| -------------                                   | :-------------                        |
| `heroku buildpacks:set -a nombre heroku/nodejs` | Setea el lenguaje de la app `nombre`. |
| `git subtree push --prefix path heroku master`  | Para hacer deploy de un subdirectorio en Node.js ([info original](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f)). `path` es la ruta hasta la carpeta de la app. |
| `heroku run sequelize db:migrate`         | Corre las migraciones en la base de datos de Heroku. (uso similar a Sequelize). |