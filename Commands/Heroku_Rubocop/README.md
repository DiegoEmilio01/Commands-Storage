# [Heroku](https://www.heroku.com/)

Ejecutar comandos dentro del repositorio de la app.

Resumen del procedimiento: Crear el Procfile (web:bundle exec puma -C config/puma.rb), loguearse a heroku, crear app heroku, setear lenguaje, pushear a heroku, migrar la bbdd, abrir la app.

| Comando                         | Descripción           |
| -------------                   |:-------------         |
| heroku login                    | Iniciar sesión heroku.|
| heroku create app-name          | Crear app en heroku.  |
| heroku logs --tail              | Ve los logs recibidos por la app. |
| heroku buildpacks:set -a app-name heroku/ruby         | Setea el lenguaje de la app. |
| git push heroku master          | Pushear a heroku. |
| heroku run rake db:migrate      | Migra la base de datos a heroku. |
| heroku run rake db:seed         | Migra la seed a heroku. |
| heroku open                     | Abre el link de la app en heroku. |
| heroku local web                | Corre la app localmente (análogo al server de rails). |
| heroku git:remote -a app-name   | Setear que la app está dentro de un repo de git. |
| heroku pg:psql	                | Entrar a la base de datos psql de la app en heroku. |
| heroku pg:backups:capture --app app-name  | Crea un backup. Se debe guardar el nombre del respaldo. |
| heroku pg:backups --app app-name          | Chequear los backups. |
| heroku pg:backups:restore b101 DATABASE_URL --app app-name | Restaurar un backup. |


# [RuboCop](https://github.com/rubocop-hq/rubocop)

| Comando           | Descripción                                    |
| -------------     |:-------------                                  |
| rubocop           | Ver ofensas a las restricciones.               |
| rubocop -a        | Intentar arreglar automáticamente las ofensas. |