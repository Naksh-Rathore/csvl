# CSVL: CSV Language

---

## Overview

A SQL interpreter for querying `.csv` files, given in a `gdb`-style TUI. Tables can be given, queried, edited. 
This project will be optimized as much as possible to work on bigger files, so it can theorectically be given as a *"database"*.
I feel like `.csv` files should be interacted more with SQL, and this project will help that. Also, I am making this to help
me learn C++, and this project will teach me **pointers**, **file handling**, **string handling and manipulation**, **optmization**, and more.

---

## Features

### Basic features

Basic usage:

```bash
./csvl [args]
```

the TUI:

```
csvl: INPUT

OUTPUT
```

To add a table (command-line):

```bash
./csvl [table_name]=[csv file]
```

To add a table (TUI):

```
csvl: table add [table_name]=[csv file]
```

To remove a table:

```
csvl: table remove [table_name]
```

To list all tables:

```
csvl: table list
```

To do a query:

```
csvl: [query]
```

### Future features to implement later

* Config file (something like `~/.gdbinit`)
* Command line queries (something like `python3 -c 'print("Hello World")'`)
* Table sharing (join with a code)

---

## Tools

---

## Contributing

---
