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

To exit:

```
csvl: exit
Exiting...
$
```

### Future features to implement later

* Config file (something like `~/.gdbinit`)
* Command line queries (something like `python3 -c 'print("Hello World")'`)
* Table sharing (join with a code)

---

## Tools & Structure

This project requires some prior thinking, as any building without a blueprint is not a sturdy one (quote by me :D), so here are some tools that are needed for this project:

| Tool | Description |
|:-----|:--------:|
| C++ | Main language      |
| Hashmap    | For putting the tables to memory       |
| Makefile | Compiling the project, make it recursive |
| g++ | Compiler (clang could be used but g++ is better since it is with gcc) |
| Networking libraries | For the table sharing feature |

Here is a basic code flow, including datatypes and OOP:

1. Tables are mapped to a class with CRUD functions and hashmaps with command line arguments
2. TUI is printed
3. Get user input for a query/command
4. If the input begins with a trigger word, it is a command otherwise a query
5. If it is a command, execute it however it may be
6. If it is a query, execute that query via the CRUD methods in the table class

---

## Contributing

Contributions are highly valued! Feel free to submit a PR, issue, or DM me about questions in my socials. However, when you are submitting or asking anything, please make it:

* Relevant: No unrelated issues or PRs
* Helpful: Something you believe will help the project
* Informative: Avoid vague PRs or issues like `Fixed issue` or `BUG` with no extended information

Contributions that don't comply with these rules are either given the `info-needed` tag, asked to elaborate, or are closed.

## License

This project uses the MIT License. More info can be found in [the license](https://github.com/Naksh-Rathore/csvl/blob/main/LICENSE).

Thanks!

---
