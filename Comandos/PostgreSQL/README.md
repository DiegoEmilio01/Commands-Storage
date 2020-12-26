# [PostgreSQL](https://www.postgresql.org/)

Clickea para una [guía de instalación](https://www.postgresql.org/download/) en distintos sistemas operativos. `PSQL` se usará como abreviatura para PostgreSQL. Esta guía está pensada para la versión 12.2.

## Comandos sobre administración

| Comando                     | Descripción                                                     |
| -------------               | :-------------                                                  |
| `sudo su - postgres`        | Entra al servidor de PSQL.                                      |
| `sudo -u nombre psql bd`    | Entra directo a la base de datos `bd` logueado como `nombre`.   |
| `psql`                      | Entrar a PSQL desde el servidor.                                |
| `create user nombre with password 'contraseña';` | Crea el usuario `nombre` con contraseña `contraseña` en PSQL |
| `alter user nombre with superuser;`  | Le da a `nombre` permisos de super user.       |
| `createdb bd` | Crea base de datos de nombre `bd`                                     |
| `psql bd`     | Para usar la base de datos `bd`.                                      |
| `\l`          | En PSQL para imprimir los nombres de las bbdd.                        |
| `\d`          | En PSQL para imprimir los nombres de las tablas.                      |
| `\du`         | En PSQL para imprimir los nombres de los usuarios.                    |
| `\df`         | En PSQL para imprimir los nombres de los procedimientos almacenados.  |
| `\COPY entidad(atr_1, atr_2) from 'entidad.csv' DELIMITER ',' CSV HEADER`  | Con la tabla creada, la pobla de datos desde un `.csv`. Poner los atributos en el orden del csv (se conserva el orden de creación). |
| `\c bd nombre` | Cambia a la base de datos `bd` utilizando usuario `nombre`.


## Modificar tablas

Sea `tabla` el nombre de una tabla en la base de datos utilizada.

| Comando                       | Descripción                         |
| -------------                 | :-------------                      |
| `CREATE TABLE tabla (atr_1 tipo PRIMARY KEY, ..., atr_n tipo, FOREIGN KEY (atr_i) REFERENCES tabla_2(atr));` | Crea una tabla donde `tipo` es un [tipo de datos](https://www.postgresql.org/docs/9.5/datatype.html) de PSQL (ojo con la versión).  |
| `INSERT INTO tabla VALUES(0, 'string', 'YYYY-MM-DD', ..., atr_n);` | Insertar una tupla en la tabla. Tanto con `INSERT` como `DELETE` se pueden hacer consultas anidadas.  |
| `ALTER TABLE tabla DROP COLUMN atr;` | Borra la columna `atr`. |
| `ALTER TABLE tabla ADD COLUMN atr tipo NOT NULL DEFAULT '';`  | Añade una columna. Esta es no nula con valor por default. |
| `ALTER TABLE tabla ALTER COLUMN col SET NOT NULL;` | Establece una columna como no nula. |
| `ALTER TABLE tabla ADD CONSTRAINT constraint_name FOREIGN KEY (atr1) REFERENCES tabla(atr2);` | Agrega foreign key. |
| `DELETE FROM tabla WHERE condicion;` | Borrar todas las tuplas que cumplan la condición. |
| `DROP TABLE IF EXISTS tabla;` | Borra la tabla si existe. |
| `UPDATE tabla SET atributo=input WHERE condición;` | Actualiza todas las tuplas que cumplan la condición. |
| `ALTER TABLE tabla DROP CONSTRAINT tabla_atr_fkey;` | Borra una referencia. |
| `CREATE SEQUENCE tabla_atr_seq START WITH maximo_atr + 1;` | Crea una secuencia para simular el datatype `SERIAL`. |
| `ALTER SEQUENCE tabla_atr_seq OWNED BY tabla.atr;` | Asignarle una tabla y un atributo a la secuencia. |
| `ALTER TABLE tabla ALTER COLUMN atr SET DEFAULT nextval('tabla_atr_seq');`	| Setear que el `atr` de la `tabla` de rige por la secuencia (setear `atr` a not null si no lo es). |


## SQL relacional


| Comando                       | Descripción                       |
| -------------                 | :-------------                    |
| `SELECT DISTINCT atributo_1, ..., atributo_n INTO tabla`	| **Proyección**. El `DISTINCT` para que sean conjuntos. `INTO` inserta las columnas seleccionadas en otra tabla (se puede usar `IN external_db`), también se pueden guardar valores en variables. |
| `WHERE condicion_1 AND cond_2 OR NOT cond_3` | **Selección**. Se pueden usar condiciones como `=`, `>=`, `<`, `<>` (distinto), etc. |
| `atr LIKE '_input%'` | Para hacer match. Se usa `%` para hacer match con varios carácteres y '\_' uno sólo. |
| `atr IN consulta` | Ve que esté dentro del conjunto (elimina duplicados). |
| `atr operador ANY/ALL (subconsulta)` | Usados para comparar un atributo con otra subconsulta. `All` es que  `atr` se compara por `operador` exitosamente con cada elemento del resultado (no monótono). `ANY` es similar pero para algún elemento (monónoto). |
| `atr ~* regex` | Permite utilizar regex case-insensitive (sin `*` para case-sensitive). |
| `EXISTS (subconsulta)` | Cuando la subconsulta retorna al menos una tupla, el operador retorna `TRUE` y `FALSE` caso contrario. |
| `||` | Concatenar strings. |
| `FROM tabla_1, tabla_2` | **Producto cruz** de 2 tablas (puede extenderse). |
| `SELECT atributos FROM tabla_1, tabla_2 WHERE condicion` | **Join** de ambas tablas. |
| `consulta_1 UNION consulta_2` | **Union**. Elimina duplicados porque trabaja con conjuntos. `UNION ALL` no elimina duplicados. |
| `consulta_1 INTERSECT consulta_2` | **Intersección**. |
| `consulta AS nuevo_nombre` | **Renombrar** subconsulta. También se puede renombrar una tabla, agregación o atributos. |
| `consulta_1 EXCEPT consulta_2` | **Diferencia**. Operador no monótono. |

## Agregación

| Comando               | Descripción                   |
| -------------         | :-------------                 |
| `COUNT(DISTINCT atr)` | Cuenta el número de valores diferentes.  |
| `MAX(atr)`            | Arroja el valor máximo de dicha columna. |
| `MIN(atr)`            | Arroja el valor mínimo de dicha columna. |
| `SUM(atr)`            | Suma cierto atributo numérico al agrupar por otro atributo. |
| `GROUP BY atr`        | **Agrupa** por atributo. Incluir todos los que se proyecten (se usa comúnmente con el `COUNT`). |
| `HAVING condicion`    | Después del `GROUP BY` y antes del `ORDER BY`. Es para condicionar agregaciones (no usar los alias). |
| `ORDER BY atr`        | **Ordena** por atributo. `ASC` o `DESC` al final de la consulta. |

## Iteración

También existen `WHILE` y `LOOP`, no obligatorio tener que declarar una variable. En el último de los siguientes casos hay que declarar la variable como `RECORD`.

```sql
FOR var IN a...b LOOP	
    sentencias_sql
END LOOP;

FOR var_tipo_record IN consulta_sql LOOP
    sentencias_sql
END LOOP;
```

## Condicionales

```sql
IF condición_booleana THEN
    sentencias_sql
ELSE
    sentencias_sql
END IF;

CASE WHEN condición_booleana THEN sentencias_sql;
    ...
    WHEN condición_booleana_n THEN sentencias_sql_n-1;
    ELSE sentencias_sql_n;
END CASE;
```


## Esquema de recursión

```sql
WITH RECURSIVE tabla_recursiva(atr_1, atr_2) AS
(
   SELECT * FROM tabla
   UNION
   SELECT T.atr_1, TR.atr_2 FROM tabla AS T, tabla_recursiva AS TR WHERE condición
)
SELECT * FROM tabla_recursiva;
```


## SQL dinámico

`EXECUTE` ejecuta el string de una consulta con variables dinámicas que pueden cambiar.

```sql
EXECUTE 'consulta con $1, ..., $n;' USING atr_1, ..., atr_n;
```

## Procedimientos almacenados en [PL/PgSQL](https://www.postgresql.org/docs/12/plpgsql.html)

Se puede guardar un procedimiento en `nombre_fn.sql` (en cualquier carpeta sin `;` al final) o en la base de datos. La consola se debe correr en dicha carpeta y para importarla en PSQL se usa `\i nombre_fn.sql`.

```sql
# Declaración
CREATE OR REPLACE FUNCTION nombre_fn (atr_1 tipo_1, ..., atr_n tipo_n)
RETURNS tipo_resultado AS
# Usar void cuando no se retorna nada. Puede ser INTEGER, TABLE(atr_1 tipo_1,...), etc.
$$
DECLARE
    declaración_de_var;   # Declara variables propias de la función y su tipo.
BEGIN
    sentencias_sql RETURN var; # Puede incluir consultas.
    # 'RETURN QUERY' para asignar la consulta a la tabla declarada como variable. Después debe venir un 'RETURN' vacio.
END
$$ LANGUAGE plpgsql;

# Uso
SELECT nombre_fn(input_1, ..., input_n);

# Importar prodecimiento en una base de datos
\i nombre_fn.sql

# Uso de variables en las sentencias
var := to_char(i, '999999999');
# Se define el valor de la variable declarada anteriormente como el resultado de una función.
```