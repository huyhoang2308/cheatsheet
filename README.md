# Table of Content
- [Android](#android)
- [Python](#python)
- [SQL](#sql)
  * [QUERYING DATA FROM A TABLE](#querying-data-from-a-table)
  * [QUERYING FROM MULTIPLE TABLES](#querying-from-multiple-tables)
  * [USING SQL OPERATORS](#using-sql-operators)
  * [MANAGING TABLES](#managing-tables)
  * [USING SQL CONSTRAINTS](#using-sql-constraints)
  * [MODIFYING DATA](#modifying-data)
  * [MANAGING VIEWS](#managing-views)
  * [MANAGING INDEXES](#managing-indexes)
  * [SQL AGGREGATE FUNCTIONS](#sql-aggregate-functions)
- [Markdown](#markdown)
  * [Basic Syntax](#basic-syntax)
  * [Text basics](#text-basics)
  * [Indentation](#indentation)
  * [Titles](#titles)
  * [Example lists (1)](#example-lists--1-)
  * [Links](#links)
  * [Images](#images)
  * [Code](#code)
  * [Math](#math)
  * [GitHub Flavored Markdown](#github-flavored-markdown)
  * [Parsers and Extensions](#parsers-and-extensions)
    + [*Python-Markdown*](#-python-markdown-)
      - [Extra Extensions](#extra-extensions)
      - [Other Extensions](#other-extensions)
      - [3rd Party Extensions](#3rd-party-extensions)
      - [Default Extensions](#default-extensions)
  * [Examples](#examples)
    + [Tables](#tables)
    + [Wiki Tables](#wiki-tables)
    + [Definition Lists](#definition-lists)
  * [About](#about)

# Android

**adb command**

- start server over tcpip `*adb tcpip <port> (5555)*`
- conenct device   `*adb connect <device_ip>:5555*`
- check devices connect ` *adb devices*`
- check log  `adb logcat | grep -i <context1>|\<context2>*`

# Python
**Virtual Env**

`python -m venv /path/to/your/dir
`
# SQL

## QUERYING DATA FROM A TABLE

- Query data in columns c1, c2 from a table
```sql
SELECT c1, c2 FROM t;
```

- Query all rows and columns from a table
```sql
SELECT * FROM t;
```

- Query data and filter rows with a condition
```sql
SELECT c1, c2 FROM t
WHERE condition;
```

- Sort the result setin ascending or descending order
```sql
SELECT c1, c2 FROM t
ORDER BY c1ASC [DESC];
```

- Skip offsetof rows and return the next n rows
```sql
SELECT c1, c2 FROM t
ORDER BY c1
LIMIT nOFFSET offset;
```

- Group rows using an aggregate function
```sql
SELECT c1, aggregate(c2)
FROM t
GROUP BY c1;
```

- Filter groups using HAVING clause
```sql
SELECT c1, aggregate(c2)
FROM t
GROUP BY c1
HAVING condition;
```

## QUERYING FROM MULTIPLE TABLES

- Inner join t1 and t2
```sql
SELECT c1, c2
FROM t1
INNER JOIN t2 ON condition;

```

- Left join t1 and t2
```sql
SELECT c1, c2
FROM t1
LEFT JOIN t2 ON condition;

```

- Right join t1 and t2
```sql
SELECT c1, c2
FROM t1
RIGHT JOIN t2 ON condition;
```

- Perform full outer join
```sql
SELECT c1, c2
FROM t1
FULL OUTER JOIN t2 ON condition;

```

- Perform Cross Join
```sql
SELECT c1, c2
FROM t1
CROSS JOIN t2;
```
*OR*
```sql
SELECT c1, c2
FROM t1, t2;

```

- Join t1 to itself using INNER JOIN clause
```sql
SELECT c1, c2
FROM t1 A
INNER JOIN t2 B ON condition;
```

## USING SQL OPERATORS

- Combine rows from two queries

```sql
SELECT c1, c2 FROM t1
UNION [ALL]
SELECT c1, c2 FROM t2;

```

- Return the intersection of two queries
```sql
SELECT c1, c2 FROM t1
INTERSECT
SELECT c1, c2 FROM t2;
```

- Subtract a result set from another result set
```sql
SELECT c1, c2 FROM t1
MINUS
SELECT c1, c2 FROM t2;
```

- Query rows using pattern matching %, _
```sql
SELECT c1, c2 FROM t1
WHERE c1[NOT] LIKE pattern;
```

- Query rows value not in list
```sql
SELECT c1, c2 FROM t
WHERE c1 [NOT] IN value_list;
```

- Query rows between two values
```sql
SELECT c1, c2 FROM t
WHERE c1 BETWEEN low AND high;
```

- Check if values in a table is NULL or not
```sql
SELECT c1, c2 FROM t
WHERE c1 IS [NOT] NULL;
```

## MANAGING TABLES
- Create new table with three columns
```sql
CREATE TABLE t (
idINT PRIMARY KEY,
nameVARCHAR NOT NULL,
priceINT DEFAULT 0
);
```

- Delete the table from the database
```sql
DROP TABLE t ;
```

- Add a new column to the table
```sql
ALTER TABLE t ADDcolumn;
```

- Drop column c from the table
```sql
ALTER TABLE t DROP COLUMN c ;
```

- Add a constraint
```sql
ALTER TABLE t ADD constraint;
```

- Drop a constraint
```sql
ALTER TABLE t DROP constraint;
```

- Rename a table from t1 to t2
```sql
ALTER TABLE t1 RENAME TO t2;
```

- Rename column c1 to c2
```sql
ALTER TABLE t1 RENAME c1 TO c2;
```

- Remove all data in a table
```sql
TRUNCATE TABLE t;
```

## USING SQL CONSTRAINTS
- Set c1 and c2 as a primary key
```sql
CREATE TABLE t(
c1INT, c2INT, c3VARCHAR,
PRIMARY KEY (c1,c2)
);
```

- Set c2 column as a foreign key
```sql
CREATE TABLE t1(
c1INT PRIMARY KEY,
c2INT,
FOREIGN KEY (c2)REFERENCES t2(c2)
);
```

- Make the valuesin c1 and c2 unique
```sql
CREATE TABLE t(
c1INT, c1INT,
UNIQUE(c2,c3)
);
```

- Ensure c1 > 0 and values in c1 >= c2
```sql
CREATE TABLE t(
c1INT, c2INT,
CHECK(c1> 0 AND c1 >= c2)
);
```

- Set values in c2 column not NULL

```sql
CREATE TABLE t(
c1INT PRIMARY KEY,
c2VARCHAR NOT NULL
);
```

## MODIFYING DATA
- Insert one row into atable
```sql
INSERT INTO t(column_list)
VALUES(value_list);
```

- Insert multiple rows into a table
```sql
INSERT INTO t(column_list)
VALUES (value_list),
(value_list), ….;
```

- Insert rows from t2 into t1
```sql
INSERT INTO t1(column_list)
SELECT column_list
FROMt2;
```

- Update new value in the column c1 for all rows
```sql
UPDATE t
SET c1= new_value;
```

- Update values in the column c1, c2that match the condition
```sql
UPDATE t
SET c1 = new_value,
c2 = new_value
WHERE condition;
```

- Delete all data in a table
```sql
DELETE FROM t;
```

- Delete subset of rows in a table
```sql
DELETE FROM t
WHERE condition;
```

## MANAGING VIEWS
- Create new view that consists of c1 and c2
```sql
CREATE VIEW v(c1,c2)
AS
SELECT c1, c2
FROM t;
```

- Create a new view with check option
```sql
CREATE VIEW v(c1,c2)
AS
SELECT c1, c2
FROM t;
WITH [CASCADED | LOCAL] CHECK OPTION;
```

- Create a recursive view
```sql
CREATE RECURSIVEVIEW v
AS
select-statement--anchor part
UNION [ALL]
select-statement;--recursive part
```

- Create a temporary view
```sql
CREATE TEMPORARYVIEW v
AS
SELECT c1, c2
FROM t;
```

- Delete a view
```sql
DROP VIEW view_name
```

## MANAGING INDEXES
- Create an index on c1 and c2 of the table t
```sql
CREATE INDEX idx_name
ON t(c1,c2);
```

- Create a unique index on c3, c4 of the table t
```sql
CREATE UNIQUE INDEX idx_name
ON t(c3,c4);
```

- Drop an index
```sql
DROP INDEX idx_name;
```

- Create a temporary view
```sql
CREATE TEMPORARYVIEW v
AS
SELECT c1, c2
FROM t;
```

- Delete a view
```sql
DROP VIEW view_name
```

## SQL AGGREGATE FUNCTIONS
```sql
AVG #returns the average of a list
COUNT #returns the number of elements of a list
SUM #returns the total of a list
MAX #returns the maximum value in a list
MIN #returns the minimum value in a list
```
# Markdown

## Basic Syntax

## Text basics
this is *italic* and this is **bold** .  another _italic_ and another __bold__

this is `important` text. and percentage signs : % and `%`

This is a paragraph with a footnote (builtin parser only). [^note-id]

Insert `[ TOC ]` without spaces to generate a table of contents (builtin parsers only).

## Indentation
> Here is some indented text
>> even more indented

## Titles
> # Big title (h1)
> ## Middle title (h2)
> ### Smaller title (h3)
> #### and so on (hX)
> ##### and so on (hX)
> ###### and so on (hX)

## Example lists (1)

 - bullets can be `-`, `+`, or `*`
 - bullet list 1
 - bullet list 2
    - sub item 1
    - sub item 2

        with indented text inside

 - bullet list 3
 + bullet list 4
 * bullet list 5

## Links

This is an [example inline link](http://lmgtfy.com/) and [another one with a title](http://lmgtfy.com/ "Hello, world").

Links can also be reference based : [reference 1][ref1] or [reference 2 with title][ref2].

References are usually placed at the bottom of the document

## Images

A sample image :

![revolunet logo](http://www.revolunet.com/static/parisjs8/img/logo-revolunet-carre.jpg "revolunet logo")

As links, images can also use references instead of inline links :

![revolunet logo][revolunet-logo]


## Code

It's quite easy to show code in markdown files.

Backticks can be used to `highlight` some words.

Also, any indented block is considered a code block.  If `enable_highlight` is `true`, syntax highlighting will be included (for the builtin parser - the github parser does this automatically).

    <script>
        document.location = 'http://lmgtfy.com/?q=markdown+cheat+sheet';
    </script>

## Math

Math can be displayed in the browser using MathJax or Katex. The feature can be enabled by correctly configuring the `"js"`, `"css"`, and `"markdown_extensions"` configuration fields. This allows for inline math to be included \\(\frac{\pi}{2}\\) $\pi$.

Alternatively, math can be written on its own line:

$$F(\omega) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} f(t) \, e^{ - i \omega t}dt$$

\\[\int_0^1 f(t) \mathrm{d}t\\]

\\[\sum_j \gamma_j^2/d_j\\]



## GitHub Flavored Markdown

If you use the Github parser, you can use some of [Github Flavored Markdown][gfm] syntax :

 * User/Project@SHA: revolunet/sublimetext-markdown-preview@7da61badeda468b5019869d11000307e07e07401
 * User/Project#Issue: revolunet/sublimetext-markdown-preview#1
 * User : @revolunet

Some Python code :

```python
import random

class CardGame(object):
    """ a sample python class """
    NB_CARDS = 32
    def __init__(self, cards=5):
        self.cards = random.sample(range(self.NB_CARDS), 5)
        print 'ready to play'
```

Some Javascript code :

```js
var config = {
    duration: 5,
    comment: 'WTF'
}
// callbacks beauty un action
async_call('/path/to/api', function(json) {
    another_call(json, function(result2) {
        another_another_call(result2, function(result3) {
            another_another_another_call(result3, function(result4) {
                alert('And if all went well, i got my result :)');
            });
        });
    });
})
```

The Github Markdown also brings some [nice Emoji support][emoji] : :+1: :heart: :beer:

[^note-id]: This is the text of the note. 

## Parsers and Extensions

Markdown Preview comes with **Python-Markdown** preloaded.

### *Python-Markdown*

The [Python-Markdown Parser][] provides support for several extensions.

[Python-Markdown Parser]: https://github.com/Python-Markdown/markdown

#### Extra Extensions

* `abbr` -- [Abbreviations][]
* `attr_list` -- [Attribute Lists][]
* `def_list` -- [Definition Lists][]
* `fenced_code` -- [Fenced Code Blocks][]
* `footnotes` -- [Footnotes][]
* `tables` -- [Tables][]
* `smart_strong` -- [Smart Strong][]

[Abbreviations]: https://python-markdown.github.io/extensions/abbreviations
[Attribute Lists]: https://python-markdown.github.io/extensions/attr_list
[Definition Lists]: https://python-markdown.github.io/extensions/definition_lists
[Fenced Code Blocks]: https://python-markdown.github.io/extensions/fenced_code_blocks
[Footnotes]: https://python-markdown.github.io/extensions/footnotes
[Tables]: https://python-markdown.github.io/extensions/tables
[Smart Strong]: https://python-markdown.github.io/extensions/smart_strong


You can enable them all at once using the `extra` keyword.

    extensions: [ 'extra' ]

If you want all the extras plus the `toc` extension,
your settings would look like this:

    {
        ...
        parser: 'markdown',
        extensions: ['extra', 'toc'],
        ...
    }


#### Other Extensions

There are also some extensions that are not included in Markdown Extra
but come in the standard Python-Markdown library.

* `code-hilite` -- [CodeHilite][]
* `header-id` -- [HeaderId][]
* `meta_data` -- [Meta-Data][]
* `nl2br` -- [New Line to Break][]
* `sane_lists` -- [Sane Lists][]
* `smarty` -- [Smarty][]
* `toc` -- [Table of Contents][]
* `wikilinks` -- [WikiLinks][]

[CodeHilite]:  https://python-markdown.github.io/extensions/code_hilite
[HeaderId]:  https://python-markdown.github.io/extensions/header_id
[Meta-Data]:  https://python-markdown.github.io/extensions/meta_data
[New Line to Break]:  https://python-markdown.github.io/extensions/nl2br
[Sane Lists]:  https://python-markdown.github.io/extensions/sane_lists
[Table of Contents]:  https://python-markdown.github.io/extensions/toc
[WikiLinks]:  https://python-markdown.github.io/extensions/wikilinks
[Smarty]: hhttps://python-markdown.github.io/extensions/smarty

#### 3rd Party Extensions

*Python-Markdown* is designed to be extended.

Some included ones are:

* `delete` -- github style delte support via `~~word~~`
* `githubemoji` --  github emoji support
* `tasklist` -- github style tasklists
* `magiclink` -- github style auto link conversion of http|ftp links
* `headeranchor` -- github style header anchor links
* `github` -- Adds the above extensions in one shot
* `b64` -- convert and embed local images to base64.  Setup by adding this `b64(base_path=${BASE_PATH})`

There are also a number of others available:

Just fork this repo and add your extensions inside the `.../Packages/Markdown Preview/markdown/extensions/` folder.

Check out the list of [3rd Party extensions](
https://github.com/waylan/Python-Markdown/wiki/Third-Party-Extensions).


#### Default Extensions

The default extensions are:

* `footnotes` -- [Footnotes]
* `toc` -- [Table of Contents]
* `fenced_code` -- [Fenced Code Blocks] 
* `tables` -- [Tables]

Use the `default` keyword, to select them all.
If you want all the defaults plus the `definition_lists` extension,
your settings would look like this:

    {
        ...
        parser: 'markdown',
        extensions: ['default', 'definition_lists'],
        ...
    }

## Examples

### Tables

The `tables` extension of the *Python-Markdown* parser is activated by default,
but is currently **not** available in *Markdown2*.

The syntax was adopted from the [php markdown project](http://michelf.ca/projects/php-markdown/extra/#table),
and is also used in github flavoured markdown.

| Year | Temperature (low) | Temperature (high) |  
| ---- | ----------------- | -------------------|  
| 1900 |               -10 |                 25 |  
| 1910 |               -15 |                 30 |  
| 1920 |               -10 |                 32 |  


### Wiki Tables

If you are using *Markdown2* with the `wiki-tables` extra activated you should see a table below:

|| *Year* || *Temperature (low)* || *Temperature (high)* ||  
||   1900 ||                 -10 ||                   25 ||  
||   1910 ||                 -15 ||                   30 ||  
||   1920 ||                 -10 ||                   32 ||  


### Definition Lists

This example requires *Python Markdown*'s `def_list` extension.

Apple
:   Pomaceous fruit of plants of the genus Malus in 
    the family Rosaceae.

Orange
:   The fruit of an evergreen tree of the genus Citrus.


## About

This plugin and this sample file is proudly brought to you by the [revolunet team][revolunet]

 [ref1]: http://revolunet.com
 [ref2]: http://revolunet.com "rich web apps"
 [MarkdownREF]: http://daringfireball.net/projects/markdown/basics
 [MarkdownPreview]: https://github.com/revolunet/sublimetext-markdown-preview
 [ST]: http://sublimetext.com
 [revolunet]: http://revolunet.com
 [revolunet-logo]: http://www.revolunet.com/static/parisjs8/img/logo-revolunet-carre.jpg "revolunet logo"
 [gfm]: https://help.github.com/articles/github-flavored-markdown/
 [emoji]: http://www.emoji-cheat-sheet.com/
