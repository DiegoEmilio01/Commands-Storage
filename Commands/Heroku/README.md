# [Heroku](https://www.heroku.com/)

Ejecutar comandos dentro del repositorio de la app.

| Command                                 | Description                         |
| -------------                           | :-------------                      |
| `heroku login`                          | Log in Heroku.                      |
| `heroku create name`                    | Create app en heroku.               |
| `heroku logs --tail`                    | Print app logs.                     |
| `git push heroku master`                | Push app to Heroku.                 |
| `heroku open`                           | Open the app in the browser.        |
| `heroku local web`                      | Run app locally.                    |
| `heroku pg:psql`	                      | Enter to PosgreSQL in Heroku.       |
| `heroku pg:backups:capture --app name`  | Create a db backup.                 |
| `heroku pg:backups --app name`          | Print all app backups.              |
| `heroku pg:backups:restore b101 DATABASE_URL --app name` | Restore a backup.  |

## In Ruby on Rails & Rake

Resumen del procedimiento: Crear el Procfile (web:bundle exec puma -C config/puma.rb), loguearse a heroku, crear app heroku, setear lenguaje, pushear a heroku, migrar la bbdd, abrir la app.

| Command                         | Description           |
| -------------                   |:-------------         |
| `heroku buildpacks:set -a nombre-app heroku/ruby`         | Setea el lenguaje de la app. |
| `heroku run rake db:migrate`      | Migra la base de datos a heroku (uso similar a rake).|
| `heroku run rake db:seed`         | Migra la seed a heroku. |
| `heroku git:remote -a nombre-app` | Setear que la app está dentro de un repo de git. |

## En Node.js y Sequelize

El procedimiento es similar (ver documentación).

| Command                         | Description           |
| -------------                   |:-------------         |
| `heroku buildpacks:set -a nombre-app heroku/nodejs`   | Setea el lenguaje de la app. |
| `git subtree push --prefix path heroku master`  | Para correr un subdirectorio en Node.js ([info original](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f)). |
| `heroku run sequelize db:migrate`         | Migra la base de datos a heroku (uso similar a sequelize). |