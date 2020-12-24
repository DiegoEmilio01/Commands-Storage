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

## En [Ruby on Rails](../RVM_Rails) y Rake

Resumen del procedimiento: Crear el Procfile (web:bundle exec puma -C config/puma.rb), loguearse a Heroku, crear app Heroku, setear lenguaje, pushear a Heroku, migrar la bbdd, abrir la app.

| Comando                       | Descripción                                           |
| -------------                 | :-------------                                        |
| `heroku buildpacks:set -a nombre heroku/ruby` | Setea el lenguaje de la app.          |
| `heroku run rake db:migrate`  | Migra la base de datos a Heroku (uso similar a Rake). |
| `heroku run rake db:seed`     | Migra la seed a Heroku.                               |
| `heroku git:remote -a nombre` | Setear que la app está dentro de un repo de Git.      |

## En Node.js y Sequelize

El procedimiento es similar (ver documentación).

| Comando                                         | Descripción                   |
| -------------                                   | :-------------                |
| `heroku buildpacks:set -a nombre heroku/nodejs` | Setea el lenguaje de la app.  |
| `git subtree push --prefix path heroku master`  | Para correr un subdirectorio en Node.js ([info original](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f)). |
| `heroku run sequelize db:migrate`         | Migra la base de datos a Heroku (uso similar a Sequelize). |