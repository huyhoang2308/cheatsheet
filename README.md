# Table of Content
- [Android](#android)
  * [ADB](#adb)
- [GIT](#git)
- [Python](#python)
  * [Virtual Env](#virtual-env)
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
  * [Examples](#examples)
  * [About](#about)

# Android

## ADB

- start server over tcpip `*adb tcpip <port> (5555)*`
- conenct device   `*adb connect <device_ip>:5555*`
- check devices connect ` *adb devices*`
- check log  `adb logcat | grep -i <context1>|\<context2>*`
- Debug webview `connect device` and type `chrome://inspect` in chrome browser

# GIT
- Checkout and swith to it
```bash
git checkout -b my-new-branch
```

- Clone
```bash
git clone branch.git
```

-  branch
```bash
git branch [-a]
# List all local branches in repository. With -a: show all branches (with remote).
git branch [branch_name]
# Create new branch, referencing the current HEAD.
git checkout [-b][branch_name]
# Switch working directory to the specified branch. With -b: Git will create the specified branch if it does not exist.
git merge [from name]
# Join specified [from name] branch into your current branch (the one you are on currently).
git branch -d [name]
#  Remove selected branch, if it is already merged into any other. -D instead of -d forces deletion.
```

- Add file
```bash
# Add single file
git add file.txt

# Add multiple files
git add file1.txt file2.txt

# Add all text files in current dir
git add *.txt

# Add files in "my-dir"
git add my-dir`
```
- Config
```bash
git config --global --edit

#email
git config user.email

# Worktree
git config --worktree user.email

# Local (current repository)
git config --local user.email

# Global
git config --global user.email

# System
git config --system user.email

#Set up the default text editor
git config --global core.editor "'C:/path/to/executable' -parameters"

```

- Add file
```bash
# Edit the .gitignore file
# Ignore all txt files
*.txt

# Track "file1.txt" even if all other txt files are ignored
!file1.txt

# Ignore a file called "credentials" in the current directory
/credentials

# Ignore all files in any directory named "logs"
logs/

# ignore all txt files in the "logs" folder, but not "logs/apache/log.txt"
logs/*.txt

# ignore all ".txt" files in the "logs" directory and any of its subdirectories
logs/**/*.txt
```

- Log
```bash
# Show all commits
git log

# Show the most recent 5 commits
git log -5

# Show commits on one line
git log --oneline

# Show a patch with changes introduced by each commit
# Limiting the result to the most recent two commits
git log -p -2`

#Displaying commits made between 2021-01-01 (inclusive) and 2021-02-01 (exclusive):

# Using before and after
git log --after="2021-01-01" --before="2021-02-01"

# Using since and until
git log --since="2021-01-01" --until="2021-02-01"

# Filter the log entries by commit message containing a string
git log --grep="hello" -i
```

- Revert
```bash
git revert abc123
```

- Add remote repo
```bash
git remote add my-remote-name https://gitcheatsheet.org/example-git-repository.git
```

- Pull
```bash
# Pull from "origin" remote
git pull

# Pull from "my-remote-name" remote
git pull my-remote-name
```

- Push
```bash
# Push the current branch on the remote repository
git push

# Push the main (a.k.a. master) branch to the main branch on the "origin" remote
git push origin main
```
- Untrack files
```bash
#Untrack files AND remove them from working tree
git rm file1.txt file2.txt

#Untrack files from staging area, without removing them from the working tree
git rm --cached file1.txt file2.txt
```

- Reset
```bash
git reset HEAD fileToUnstage.txt

#Reset the working directory to the state of a specific commit
git reset --hard abc123
```

- Restorte
```bash
git restore --staged fileToUnstage.txt
```

- Rebase
```bash
# Regular rebase
git rebase other-branch

# Interactive rebase
git rebase -i other-branch
```

- Diff
```bash
#Show the changes of both staged and unstaged files since the last commit
git diff HEAD

#Show the changes of files that are staged
git diff --staged
```

- Cherry pick
```bash
git cherry-pick abc123
```

- Stash
```bash
# Stash local modifications
git stash push -m "My Stash Message"

# Include untracked files
git stash push -u -m "Including untracked files"

# Stash only specified files
git stash push -u -m "Stashing specific files" -- file1.txt file2.txt

# List the stash entries
git stash list

# Apply the LATEST stash entry (index 0)
git stash apply

# Apply SPECIFIC stash entry (index 1)
git stash apply stash@{1}

# Pop the LATEST stash entry (index 0)
git stash pop

# Pop a SPECIFIC stash entry (index 1)
git stash pop stash@{1}

# Drop the LATEST stash entry (index 0)
git stash drop

# Drop a SPECIFIC stash entry (index 1)
git stash drop stash@{1}

#Clear all the stash entries
git stash clear
```

- Tagging
```bash
git tag
# List all tags.
git tag [name] [commit sha]
#  Create a tag reference named name for current commit. Add commit sha to tag a specific commit instead of current one.
git tag -a [name] [commit sha]
# Create a tag object named name for current commit.
git tag -d [name]
# Remove a tag from local repository.
```

# Python
## Virtual Env

```
python -m venv /path/to/your/dir
```

## Jupyter Notebook
- Setup Jupyter Lab
```bash
pip install jupyterlab
```

- Setup Jupyer Notebook
```python
pip install notebook
```

- Start Jupyter
```python
jupyter notebook
```

- Shortcut

| *Function* | *Keyboard Shortcut* | *Menu Tools*     |  
| -------- | ----------------- | ----------------|  
| Run Cell | Ctrl + Enter      | Cell → Run Cell |  
| Create new cell | above: Esc + a, Below: Esc + b | Insert→ Insert Cell Above OR Insert → Insert Cell Below |
| Copy Cell | c                | Copy Key        |
| Paste Cell | v               | Paste Key      |

## Common
- Unpacking Elements
```python
>>> record = ('Dave', 'dave@example.com', '773-555-1212', '847-555-1212')
>>> name, email, *phone_numbers = user_record
>>> name
'Dave'
>>> email
'dave@example.com'
>>> phone_numbers
['773-555-1212', '847-555-1212']
##############
>>> line = 'nobody:*:-2:-2:Unprivileged User:/var/empty:/usr/bin/false'
>>> uname, *fields, homedir, sh = line.split(':')
>>> uname
'nobody'
>>> homedir
'/var/empty'
>>> fields
['*', '-2', '-2', 'Unprivileged User']
########### 
"""
    Using *_ to assign unuse value
"""
>>> record = ('ACME', 50, 123.45, (12, 18, 2012))
>>> name, *_, (*_, year) = record
>>> name
'ACME'
>>> year
2012
```

- Keep the last N item 
```python
from collections import deque

def search(lines, pattern, history=5):
    previous_lines = deque(maxlen=history)
    for line in lines:
        if pattern in line:
            yield line, previous_lines
        previous_lines.append(line)
```

- Finding the Largest or Smallest N Items
```python
import heapq
portfolio = [
{'name': 'IBM', 'shares': 100, 'price': 91.1},
{'name': 'AAPL', 'shares': 50, 'price': 543.22},
{'name': 'FB', 'shares': 200, 'price': 21.09},
{'name': 'HPQ', 'shares': 35, 'price': 31.75},
{'name': 'YHOO', 'shares': 45, 'price': 16.35},
{'name': 'ACME', 'shares': 75, 'price': 115.65}
]
cheap = heapq.nsmallest(3, portfolio, key=lambda s: s['price'])
expensive = heapq.nlargest(3, portfolio, key=lambda s: s['price'])

>>> cheap
[{'name': 'YHOO', 'shares': 45, 'price': 16.35},
 {'name': 'FB', 'shares': 200, 'price': 21.09},
 {'name': 'HPQ', 'shares': 35, 'price': 31.75}]
>>> expensive
[{'name': 'AAPL', 'shares': 50, 'price': 543.22},
 {'name': 'ACME', 'shares': 75, 'price': 115.65},
 {'name': 'IBM', 'shares': 100, 'price': 91.1}]
```

- Priority Queue
```python
import heapq

class PriorityQueue:
    def __init__(self):
        self._queue = []
        self._index = 0

    def push(self, item, priority):
        heapq.heappush(self._queue, (-priority, self._index, item))
        self._index += 1
    
    def pop(self):
        return heapq.heappop(self._queue)[-1]


############# Usage
class Item:
    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return 'Item({!r})'.format(self.name)

>>> q = PriorityQueue()
>>> q.push(Item('foo'), 1)
>>> q.push(Item('bar'), 5)
>>> q.push(Item('spam'), 4)
>>> q.push(Item('grok'), 1)
>>> q.pop()
Item('bar')
>>> q.pop()
Item('spam')
>>> q.pop()
Item('foo')
>>> q.pop()
Item('grok')
```

- Mapping Keys to Multiple Values in a Dictionary
```python
from collections import defaultdict

d = defaultdict(list)
d['a'].append(1)
d['a'].append(2)
d['b'].append(4)
>>> d
defaultdict(list, {'a': [1, 2], 'b': [4]})
################
d = defaultdict(set)
d['a'].add(1)
d['a'].add(2)
d['b'].add(4)
>>> d 
defaultdict(set, {'a': {1, 2}, 'b': {4}})
```


## Logging
```python
import logging
log_format = '[%(asctime)s]-[%(levelname)s]-[%(filename)s:%(lineno)s- %(funcName)20s() ] \n>>> %(message)s'
loggin.basicConfig(format=log_format, level=logging.DEBUG) #INFO
```

## Pandas
```python
import pandas
pandas.options.mode.chained_assignment = None  # default='warn', igonre warning



```

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

 [ref1]: http://revolunet.com
 [ref2]: http://revolunet.com "rich web apps"
 [MarkdownREF]: http://daringfireball.net/projects/markdown/basics
 [MarkdownPreview]: https://github.com/revolunet/sublimetext-markdown-preview
 [ST]: http://sublimetext.com
 [revolunet]: http://revolunet.com
 [revolunet-logo]: http://www.revolunet.com/static/parisjs8/img/logo-revolunet-carre.jpg "revolunet logo"
 [gfm]: https://help.github.com/articles/github-flavored-markdown/
 [emoji]: http://www.emoji-cheat-sheet.com/
