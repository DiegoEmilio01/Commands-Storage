# [Node Version Manager](https://github.com/nvm-sh/nvm)

Maneja las versiones de [Node.js](https://nodejs.org/es/) en tu computador. Se instala NVM y al instalar una versión de Node se instala NPM.

| Comando               | Descripción                             |
| -------------         | :-------------                          |
| `nvm list`            | Lista las versiones instaladas.         |
| `nvm install 12.18.3` | Instala la versión especificada.        |
| `nvm use 12.18.3`     | Establece usar dicha versión.           |
| `nvm current`         | Muestra qué versión se está utilizando. |
| `npm install -g yo`   | Usa node package manager para instalar globalmente Yeoman. |


# [Yarn](https://yarnpkg.com/) y [Sequelize](https://sequelize.org/)

Maneja paquetes.

| Comando                                    | Descripción                                  |
| -------------                              | :-------------                               |
| `yarn install`                             | Instala dependencias.                        |
| `yarn dev`                                 | Levanta la app.                              |
| `yarn sequelize db:migrate`                | Ejecuta las migraciones.                     |
| `yarn sequelize seed:create --name modelo` | Crea seed con nombre `modelo` (usar plural). |
| `yarn sequelize db:seed:all`               | Ejecuta todas las seeds.                     |
| `yarn sequelize db:migrate:undo:all`       | Deshacer las migraciones.                    |


# [Yeoman](https://yeoman.io/)

Generador de ecosistemas. Permite generar un proyecto a partir de una plantilla.


| Comando                           | Descripción                                       |
| -------------                     | :-------------                                    |
| `yo @iic2513/template nombre`     | Crea aplicación `nombre` utilizando la plantilla.  |
| `yo @iic2513/template:model nombre atr1:type,atr2:type --create` | Crea modelo `nombre` usando la plantilla. Ejecutar en la carpeta del proyecto. Tipos de datos: string, text, integer, boolean, etc. |


