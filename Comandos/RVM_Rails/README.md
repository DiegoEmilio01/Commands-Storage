# [Ruby Version Manager](https://rvm.io/)

Manage the [Ruby](https://www.ruby-lang.org/en/) versions in your computer.

| Command                   | Description                                   |
| -------------             | :-------------                                |
| `rvm get stable`          | Update RVM.                                   |
| `rvm list`                | Print installed versions.                     |
| `rvm list known`          | Print all available versions.                 |
| `rvm install 2.6.5`       | Install the specified version of Ruby.        |
| `rvm use 2.6.5`           | Set the specified version as current version. |
| `rvm --default use 2.6.5` | Change default version.                       |
| `rvm remove 2.6.5`        | Uninstall the specified version.              |


# [Rails](https://rubyonrails.org/)

Package manager. Write `gem 'pg'` in `Gemfile` to use PostgreSQL in your project. This guide is compatible with the 5.2.4.2 version of Rails.

| Command                                       | Description                                       |
| -------------                                 | :-------------                                    |
| `gem install rails -v 5.2.4.2`                | Install the specified version of Rails.           |
| `rails -v`                                    | Print Rails version.                              |
| `bundle install`                              | Install Gemfile gems.                             |
| `rails new name -d postgresql`                | Create `name` app using PostgreSQL as model.      |
| `rails generate controller name action1 ...`  | Generate `name` controller with opcional actions. |
| `rails generate model name attr_1:tipo ...`   | Create `name` table in the database.              |
| `rails server`                                | Start the app server.                             |
| `rails db:migrate`                            | Run the migrations in the app database.           |

