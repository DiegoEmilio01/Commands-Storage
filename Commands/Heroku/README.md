<style> code { font-family: monospace} </style>

# [Heroku](https://www.heroku.com/)

Ejecutar comandos dentro del repositorio de la app.

| Comando                         | Descripción           |
| -------------                   |:-------------         |
| `heroku login`                    | Iniciar sesión heroku.|
| `heroku create nombre-app`          | Crear app en heroku.  |
| `heroku logs --tail`              | Ve los logs recibidos por la app. |
| `git push heroku master`          | Pushear a heroku. |
| `heroku open`                     | Abre el link de la app en heroku. |
| `heroku local web`                | Corre la app localmente (análogo al server de rails). |
| `heroku git:remote -a nombre-app`   | Setear que la app está dentro de un repo de git. |
| `heroku pg:psql`	                | Entrar a la base de datos psql de la app en heroku. |
| `heroku pg:backups:capture --app nombre-app`  | Crea un backup. Se debe guardar el nombre del respaldo. |
| `heroku pg:backups --app nombre-app`          | Chequear los backups. |
| `heroku pg:backups:restore b101 DATABASE_URL --app nombre-app` | Restaurar un backup. |

## En Ruby on Rails y Rake

Resumen del procedimiento: Crear el Procfile (web:bundle exec puma -C config/puma.rb), loguearse a heroku, crear app heroku, setear lenguaje, pushear a heroku, migrar la bbdd, abrir la app.

| Comando                         | Descripción           |
| -------------                   |:-------------         |
| `heroku buildpacks:set -a nombre-app heroku/ruby`         | Setea el lenguaje de la app. |
| `heroku run rake db:migrate`      | Migra la base de datos a heroku (uso similar a rake).|
| `heroku run rake db:seed`         | Migra la seed a heroku. |

## En Node.js y Sequelize

El procedimiento es similar (ver documentación).

| Comando                         | Descripción           |
| -------------                   |:-------------         |
| `heroku buildpacks:set -a nombre-app heroku/nodejs`   | Setea el lenguaje de la app. |
| `git subtree push --prefix path heroku master`  | Para correr un subdirectorio en Node.js ([info original](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f))|
| `heroku run sequelize db:migrate`         | Migra la base de datos a heroku (uso similar a sequelize). |