# [MongoDB](https://www.mongodb.com/)

Clickea para una guía de instalación para [Debian](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/) o [Ubuntu](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/). Los comandos sobre levantar procesos pueden variar, estos fueros pensados para [Debian Buster](https://www.debian.org/releases/buster/index.es.html) y [systemd](https://wiki.debian.org/systemd).

## Comandos sobre procesos y administración

| Comando                         | Descripción                     |
| -------------                   | :-------------                  |
| `sudo systemctl start mongod`   | Iniciar el proceso de MongoDB.  |
| `sudo systemctl status mongod`  | Ver el estado del proceso.      |
| `sudo systemctl stop mongod`    | Detener el proceso.             |
| `sudo systemctl restart mongod` | Reiniciar el proceso.           |
| `mongo`                         | Iniciar la consola de MongoDB mientras se corre el proceso. |
| `show dbs`                      | Imprime las bbdd disponibles.             |
| `db`                            | Imprime la base de datos en uso.          |
| `use bd`                        | Se cambia a la base de datos llamada `bd`. Si no existe, la crea al generar la primera colección. |
| `show collections`              | Dentro de la bd para ver las colecciones. |
| `mongoimport --db bd --collection col --drop --file col.json --jsonArray` | Importa un `col.json` en la db llamada `bd` como colección `col`. |

## Operaciones sobre colecciones

Sea `coll` el nombre de una colección en la base de datos utilizada.

| Comando                       | Descripción                       |
| -------------                 |:-------------                     |
| `db.coll.insert(datos)`         | Inserta los datos en la colección `coll` de la base de datos en uso (datos es un objeto llave-valor).  |
| `db.coll.find({atr_1:input}, {atr_2:1, atr_3:0})` | Evalúa un match en el `atr_1` y proyecciones en `atr_2` y `atr_3` (recomendado omitir los `_id`).  |
| `db.coll.find({atr_1: [input_1, ...]})`       | Imprime los elementos cuyo atributo haga match con alguno de la lista. |
| `comando.pretty()`	            | Imprime el resultado más legible para humanos. |
| `comando.sort({atr: 1})`        | Ordena por atributo.              |
| `db.coll.find({atr:{$regex:"input"}})` | Busca que `atr` contenga el regex `input` (los strings van entre comillas). |
| `$gt: input` | Mayor que `input` (`$gte` mayor o igual). |
| `$lt: input` | Menor que `input` (`$lte` menor o igual). |
| `$ne: input` | Distinto a `input`. |
| `$and: [condición_1, ...]`  | Revisa que se cumplan todas las condiciones. |
| `$or: [condición_1, ...]`   | Revisa que se cumplan las condiciones por un OR. |
| `$all: [input_1, ...]`      | Verifica que en una lista deben estar todos los valores dados. |
| `$in: [input_1, ...]`				| Verifica que en una lista debe estar al menos uno de los valores dados. |
| `$nin: [input_1, ...]`			| Verifica que en una lista no debe haber ninguno de los valores dados. |
| `db.coll.aggregate([{$group: {_id: null, total: {$sum: "$atr"}}}])`	| Agrega y suma por el atributo. (También se puede usar `$avg`). |
| `{$group: {_id: "$atr_1", total: {$sum: "$atr_2"}` | Agrupa por `atr_1` y suma los `atr_2`.
| `{$group: {_id: "$atr_1", total: {$sum: {$sum: "$atr_2"}}` | Agrupa por `atr_1` y suma los valores de `atr_2` si `atr_"` es una lista. |
| `{$match: {atr: input}}`                    | Al agregar en una lista, revisa match por cada elemento. |
| `db.getCollectionInfos({name:"coll"})`      | Imprime información de la colección.  |
| `db.changeUserPassword("usuario", "contraseña")` | Cambiar la contraseña de la bd.  |
| `db.coll.getIndexes()`                      | Imprime los índices de la colección.  |
| `db.coll.createIndex({atr:1})`              | Crea un índice por dicho atributo.    |
| `db.coll.createIndex({atr:"text"})`	 | Crea un índice de texto del tipo TF-IDF por dicho atributo. |
| `db.coll.dropIndex("index")`                | Borra del índice indicado. |
| `db.coll.find({$text: {$search: "input"}})` | Utiliza el índice de texto para buscar eficietemente. |
| `"input_1 input_2 ..."`       | Busca mediante OR los diferentes inputs (stemming: case insensitive y completa el input si al menos una palabra entera es encontrada). |
| `" \"input textual\"  "`      | Busca textual el input (los "\" son para escapar las comillas). |
| `" \"input_1\" \"input_2\" "` | Busca `input_1` o `input_2` ambos textuales (stemming). |
| `"input_1 -\"input_2\" "` 		| Busca al menos un `input_1` para descartar `input_2` (también `"input_1 -input_2"`). |
| `db.coll.find({$text: {$search: ""}}).sort({score: {$meta: "text"}})`	| Ordena el resultado de una consulta por índice. |
| `db.coll.update({}, {$set: {atr: valor}}, false, true)`	| Actualiza `atr` de todo elemento al valor `valor`. `false` por upsert, es decir, que no inserte nuevo valor al no hacer match. `true` para modificar múltiples elementos. |
