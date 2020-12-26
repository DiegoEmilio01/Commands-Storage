# [Heroku](https://www.heroku.com/)

Excute commands inside the folder of the repository.

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

## Using [Ruby on Rails](../RVM_Rails) & [Rake](https://github.com/ruby/rake)

Steps:
- Create a `Procfile` with `web:bundle exec puma -C config/puma.rb` within it.
- Log in Heroku.
- Create Heroku app.
- Set language.
- Push to Heroku.
- Migrate database.
- Open the app.

| Command                         | Description                           |
| -------------                   |:-------------                         |
| `heroku buildpacks:set -a name heroku/ruby` | Set `name` app language.  |
| `heroku run rake db:migrate`    | Run migrations in Heroku.             |
| `heroku run rake db:seed`       | Run app seed in Heroku.               |
| `heroku git:remote -a name`     | Set the app inside a Git repository.  |

## Using [Node.js](../NVM_Yarn_Yeoman) & [Sequelize](../NVM_Yarn_Yeoman)

Similar steps (see Heroku documentation).

| Command                                         | Description               |
| -------------                                   |:-------------             |
| `heroku buildpacks:set -a name heroku/nodejs`   | Set `name` app language.  |
| `git subtree push --prefix path heroku master`  | To deploy a subdirectory with a Node.js app ([original info](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f)). `path` is the route to the app folder. |
| `heroku run sequelize db:migrate`         | Run migrations in Heroku (similar use to Sequelize). |