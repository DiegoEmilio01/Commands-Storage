# [MongoDB](https://www.mongodb.com/)

Click to go to an installation guide for [Debian](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/) or [Ubuntu](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/). The commands that involves processes may not be the same, this guide was made assuming [Debian Buster](https://www.debian.org/releases/buster/index.es.html) operating system and [systemd](https://wiki.debian.org/systemd) as system and service manager.

## Processes and administration commands

| Command                         | Description                     |
| -------------                   | :-------------                  |
| `sudo systemctl start mongod`   | Initiates MongoDB process.      |
| `sudo systemctl status mongod`  | Check process status.           |
| `sudo systemctl stop mongod`    | Stop the process.               |
| `sudo systemctl restart mongod` | Restart the process.            |
| `mongo`                         | Initiates MongoDb console while running the process. |
| `show dbs`                      | Print available databases.      |
| `db`                            | Print the db in use.            |
| `use db`                        | Change to `db` database. If it doesn't exist, it creates it when the fisrt collection is generated. |
| `show collections`              | Inside the db to print all collection names. |
| `mongoimport --db db --collection col --drop --file col.json --jsonArray` | Import `col.json` in `db` database as `col` collection. |

## Operations on coleccions

Let `coll` be the name of a collection in the db in use.

| Command                       | Description                       |
| -------------                 |:-------------                     |
| `db.coll.insert(data)`        | Insert data in `coll` (data is a key-value object).  |
| `db.coll.find({attr_1:input}, {attr_2:1, attr_3:0})` | Evaluate if `attr_1` matches `input` and proyect  `attr_2` but no `attr_3` (hiding `_id` is recommended).  |
| `db.coll.find({attr_1: [input_1, ...]})`       | Print elements which makes a match with some element of the list. |
| `command.pretty()`	            | Print the result more human friendly. |
| `command.sort({attr: 1})`        | Order by attribute.              |
| `db.coll.find({attr:{$regex:"input"}})` | Evaluate if `attr` matches `input` regex (strings go between quotation marks). |
| `$gt: input` | Great than `input` (`$gte` great than o equal). |
| `$lt: input` | Less than `input` (`$lte` less than or equal). |
| `$ne: input` | Not equal to `input`. |
| `$and: [condición_1, ...]`  | Match if all conditions are satisfied. |
| `$or: [condición_1, ...]`   | Match if at least one condition is satisfied. |
| `$all: [input_1, ...]`      | Check if a list contains all given inputs. |
| `$in: [input_1, ...]`				| Check if a list contains at least one of the given inputs. |
| `$nin: [input_1, ...]`			| Check if a list doesn't contain any of the given inputs. |
| `db.coll.aggregate([{$group: {_id: null, total: {$sum: "$attr"}}}])`	| Aggregate and sum `attr` values. (`$avg` can also be used). |
| `{$group: {_id: "$attr_1", total: {$sum: "$attr_2"}` | Gruoup by `attr_1` and sum `attr_2` values.
| `{$group: {_id: "$attr_1", total: {$sum: {$sum: "$attr_2"}}` | Group by `attr_1` and sum `attr_2` values if `attr_2` is a list. |
| `{$match: {attr: input}}` | When the result is grouped in a list, check a match for every element of it. |
| `db.getCollectionInfos({name:"coll"})`      | Print collection information. |
| `db.changeUserPassword("user", "password")` | Change db password for a given user. |
| `db.coll.getIndexes()`                      | Print indexes of a collection. |
| `db.coll.createIndex({attr:1})`              | Create an index on the attributes indicated. |
| `db.coll.createIndex({attr:"text"})`	        | Create a TF-IDF index (text index) on that attribute. |
| `db.coll.dropIndex("index")`                | Drop an index. |
| `db.coll.find({$text: {$search: "input"}})` | Use the text index to search efficiently. |
| `"input_1 input_2 ..."`       | Search inputs by OR operator (stemming: case insensitive and completes the input if at least one word is found). |
| `" \"input\"  "`      | Search a perfect match of the input ("\" is used to escape the quotation marks). |
| `" \"input_1\" \"input_2\" "` | Search a perfect match of `input_1` or `input_2` (stemming). |
| `"input_1 -\"input_2\" "` 		| Search at least one match of `input_1` and then discard matches with `input_2` (also `"input_1 -input_2"` works). |
| `db.coll.find({$text: {$search: ""}}).sort({score: {$meta: "text"}})`	| Order the result of a query by index. |
| `db.coll.update({}, {$set: {attr: value}}, false, true)`	| Update `attr` of every element with `value`. `upsert` set to `false` so it won't insert a new element when there insn't a match. And `multi` set to `true` so the query can modify multiple elements. |
