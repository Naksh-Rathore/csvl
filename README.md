# CSVL: A SQL-like Interpreter for CSV Files

## Overview

**CSVL** is a C++ project that implements a SQL-like interpreter for CSV files. It allows users to interactively query multiple CSV tables, dynamically add new tables, and view results in a GDB-style text-based user interface (TUI). This project emphasizes learning **C++ programming**, **data structures**, **parsing**, and optionally, **low-level systems concepts** if extended into debugging and binary analysis.

The core idea:
- Load CSV files as tables.
- Run SQL-like queries (`SELECT`, `WHERE`, `JOIN`) on the tables.
- Interact through a GDB-style TUI with panels for output, tables, and commands.
- Optionally, dynamically add or remove tables during runtime.

---

## Features

### Command-Line Usage
text
./csvl table1=table1.csv table2=table2.csv
endtext
- Loads the specified CSV files into memory.
- Each table is represented as a C++ class encapsulating columns, rows, and query methods.

### Command Format
text
csvl: SELECT col1, col2 FROM table1 WHERE col3 > 10
csvl: add table table3=table3.csv
csvl: remove table table2
csvl: list tables
endtext

### GDB-Style TUI Layout
text
+---------------------------+---------------------------+
|       Output Panel        |       Tables Panel        |
|  (query results, errors)  | table1  col1, col2, col3 |
|                           | table2  col1, col2       |
+---------------------------+---------------------------+
| Command Panel: csvl: _                           |
+--------------------------------------------------+
endtext
- **Output Panel**: Scrollable query results and error messages.
- **Tables Panel**: Shows currently loaded tables and their columns.
- **Command Panel**: For typing queries and table management commands, supports history and shortcuts.

### Table Class Design
text
class Table {
private:
    std::string name;
    std::vector<std::string> columns;
    std::vector<std::vector<std::string>> rows;

public:
    // Constructor to load CSV
    Table(const std::string& tableName, const std::string& filename);

    // Accessors
    const std::string& getName() const;
    const std::vector<std::string>& getColumns() const;
    const std::vector<std::vector<std::string>>& getRows() const;

    // Query functions
    std::vector<std::vector<std::string>> select(
        const std::vector<std::string>& cols, 
        const std::function<bool(const std::vector<std::string>&)>& filter
    ) const;

    // Optional: add rows dynamically
    void addRow(const std::vector<std::string>& row);
};
endtext

---

## Learning Goals

### C++ Concepts
- Classes, encapsulation, constructors, and member functions.
- STL containers: `vector`, `map`, `unordered_map`.
- File I/O: reading CSV files safely and efficiently.
- String manipulation and parsing.
- References, pointers, and memory management.

### Intermediate & Advanced Skills
- Optimizing query evaluation on CSV data.
- Implementing efficient filtering and selection.
- Modular program structure for maintainability.
- TUI development with libraries like `ncurses` or `FTXUI`.
- Optional: low-level debugging concepts (if extending toward binary analysis).

---

## Optional Extensions
- Syntax highlighting for SQL keywords in the TUI.
- Aggregates: `SUM`, `COUNT`, `AVG`.
- JOIN functionality for multiple tables.
- Temporary table creation and session-based queries.
- Dynamic breakpoints or binary-like analysis for educational challenges.
- Large CSV optimization: lazy loading, caching, or memory-efficient structures.

---

## Development Roadmap

1. **Basic CSV Loader**
   - Load one CSV file into a `Table` class.
   - Display column headers and first few rows.

2. **Basic Query Engine**
   - Support `SELECT` with optional `WHERE` filters.
   - Return results as a vector of rows.

3. **GDB-Style TUI**
   - Implement panels: output, tables, command.
   - Command history and scrollable output.

4. **Multiple Tables**
   - Load multiple tables at startup.
   - Support dynamic `add table` and `remove table`.

5. **Advanced Queries**
   - Implement `JOIN` operations, aggregates, and sorting.
   - Optional: syntax highlighting and advanced filters.

6. **Optimization & Performance**
   - Implement efficient search/filtering.
   - Consider caching and memory optimizations for large CSVs.

7. **Optional Debugger Challenge**
   - Disassemble a small binary.
   - Insert breakpoints with `0xCC`.
   - Step through instructions in a controlled environment.

---

## Tools & Libraries
- **C++17 or later**
- **ncurses** or **FTXUI** for TUI
- STL containers (`vector`, `map`, `unordered_map`)
- Optional: system headers for low-level process manipulation (if doing debugger
