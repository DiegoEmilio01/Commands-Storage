# [Ruby Version Manager](https://rvm.io/)

Maneja las versiones de [Ruby](https://www.ruby-lang.org/es/) en tu computador.

| Comando                   | Descripción                                     |
| -------------             | :-------------                                  |
| `rvm get stable`          | Actualiza RVM.                                  |
| `rvm list`                | Lista versiones instaladas.                     |
| `rvm list known`          | Lista todas las versiones de Ruby disponibles.  |
| `rvm install 2.6.5`       | Instala versión especificada.                   |
| `rvm use 2.6.5`           | Cambia versión usada por el sistema.            |
| `rvm --default use 2.6.5` | Cambia la versión default.                      |
| `rvm remove 2.6.5`        | Desinstala una versión.                         |


# [Rails](https://rubyonrails.org/)

Maneja paquetes. Escribir `gem 'pg'` en `Gemfile` para usar PostgreSQL en el proyecto. Esta guía está basada en la versión 5.2.4.2 de Rails.

| Comando                                         | Descripción                                          |
| -------------                                   | :-------------                                       |
| `gem install rails -v 5.2.4.2`                  | Instala version de Rails.                            |
| `rails -v`                                      | Imprime versión de Rails.                            |
| `bundle install`                                | Instala gemas del Gemfile.                           |
| `rails new nombre -d postgresql`                | Crea app `nombre` utilizando PostgreSQL como modelo. |
| `rails generate controller nombre accion1 ...`  | Genera el controlador `nombre` con acciones opcionales. |
| `rails generate model nombre atr_1:tipo ...`    | Crea la tabla `nombre` en la base de datos.          |
| `rails server`                                  | Levanta el server para correr la app.                |
| `rails db:migrate`                              | Realiza las migraciones en la base de datos.         |

