# [Node Version Manager](https://github.com/nvm-sh/nvm)

Manage the [Node.js](https://nodejs.org/es/) versions in your computer. When you install a Node version, Node Package Manager comes with it.

| Command               | Description                                   |
| -------------         | :-------------                                |
| `nvm list`            | Print installed versions.                     |
| `nvm install 12.18.3` | Install the specified version.                |
| `nvm use 12.18.3`     | Set the specified version as current version. |
| `nvm current`         | Print current version.                        |
| `npm install -g yo`   | Use NPM to install Yeoman globally.           |


# [Yarn](https://yarnpkg.com/) & [Sequelize](https://sequelize.org/)

Yarn is a package manager and Sequelize is a promise-based Node.js ORM.

| Command                                    | Description                                  |
| -------------                              | :-------------                               |
| `yarn install`                             | Install dependencies.                        |
| `yarn dev`                                 | Run the application.                         |
| `yarn sequelize db:migrate`                | Execute the migrations.                      |
| `yarn sequelize seed:create --name model`  | Create `model` seed (use plural).            |
| `yarn sequelize db:seed:all`               | Execute all seeds.                           |
| `yarn sequelize db:migrate:undo:all`       | Undo all migrations.                         |


# [Yeoman](https://yeoman.io/)

Ecosystem generator. Useful to generate a project using a template.


| Command                           | Description                                       |
| -------------                     | :-------------                                    |
| `yo @iic2513/template name`       | Create `name` app using the template.  |
| `yo @iic2513/template:model name attr1:type,attr2:type --create` | Create `name` model using the template. Use inside the project folder. Datatypes: string, text, integer, boolean, etc. |


