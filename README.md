# Inventory Management System (Python & SQLite)

## Project Overview
This project is a Command-Line Interface (CLI) application developed in **Python** with persistent storage managed by **SQLite3**. It provides a robust, end-to-end Solution for product inventory management (CRUD operations). The system enables users to register, view, search, update, and delete products, as well as generate automated low-stock alerts. It emphasizes code quality, modular architecture, strict data validation, and a clean, color-coded user experience in the terminal.

---

## Table of Contents
- [Key Features](#key-features)
- [Repository Structure](#repository-structure)
- [Database Schema](#database-schema)
- [Requirements & Installation](#requirements--installation)
- [Usage & Execution](#usage--execution)
- [Author](#author)

---

## Key Features
- **Full CRUD Functionality:** Create, Read, Update, and Delete product records in real-time.
- **Multi-Criteria Search:** Search products by `ID`, or filter dynamically by `Name` and `Category` using SQL `LIKE` pattern matching.
- **Automated Low-Stock Reporting:** Instantly filter and display products with stock counts equal to or lower than a user-specified threshold.
- **Defensive Data Validation:** A dedicated module for input handling that prevents execution crashes (`ValueError`), enforces non-empty fields, and validates numeric ranges.
- **Color-Coded Terminal Interface:** Integrated `colorama` library for enhanced user experience (UX), highlighting successes, warnings, errors, and system titles in vibrant terminal colors.
- **Clean Modular Architecture:** Strict separation of concerns across entry point, business/SQL logic, input validation, and UI styling.

---

## Repository Structure

```text
├── programa_principal.py  # Main entry point of the application
├── funciones.py           # Core business logic, SQL queries, and menu controller
├── validaciones.py        # Input validation routines and type safety
├── interfaz_color.py      # Terminal formatting and Colorama UI styling
├── inventario.db          # SQLite database (auto-generated on first run)
└── README.md              # Project documentation
```

---

## Database Schema
The system connects to a SQLite3 database (inventario.db) and automatically manages a relational table named productos with the following structure:

| Column Name	| Data Type	| Constraints / Properties |
| --- | --- | --- |
| id | INTEGER | Primary Key, Auto-increment |
| nombre | TEXT | NOT NULL |
| descripcion | TEXT | Optional ("Sin descripción" by default) |
| cantidad | INTEGER | NOT NULL (Available stock) |
| precio | REAL | NOT NULL (Unit price) |
| categoria | TEXT | Optional ("Sin categoría" by default) |

---

## Requirements & Installation

1. Clone the repository:
```Bash
git clone [https://github.com/fadalid/python-sqlite-crud.git](https://github.com/fadalid/python-sqlite-crud.git)
cd python-sqlite-crud
```

2. Install dependencies:
This application requires colorama for terminal color formatting.
```Bash
pip install colorama
```

3. Run the application:
```Bash
python programa_principal.py
```

---

## Usage & Execution
Once the application is running (`python programa_principal.py`), you will be greeted by an interactive, color-coded main menu with the following options:
1. **Register New Product (`Registrar Producto Nuevo`):** Prompts for product details (Name, Description, Stock, Price, Category). Inputs are automatically validated (ensuring non-empty strings, positive integers for stock, and positive decimal values for price) before inserting the record into the SQLite database.
2. **View Registered Products (`Ver lista de Productos registrados`):** Fetches and displays all active inventory items formatted in clean terminal cards. If the database is empty, a warning message is triggered.
3. **Search Product (`Buscar Producto`):** Opens a dedicated search sub-menu allowing users to query items by **ID** (exact match), **Name** (partial match via SQL `LIKE`), or **Category** (partial match via SQL `LIKE`).
4. **Update Product (`Actualizar registro de Producto`):** Searches for a product by ID, displays its current values, and allows field-by-field updates. Pressing `Enter` leaves existing values unchanged.
5. **Delete Product (`Borrar Producto por ID`):** Locates a product by ID, displays its name, and prompts for explicit user confirmation (`S/N`) before permanently executing the `DELETE` query.
6. **Low Stock Report (`Reporte de Bajo Stock`):** Prompts the user for a stock threshold and filters all items in the database with stock quantities less than or equal to that number.
7. **Exit (`Salir del sistema`):** Closes the database connection safely and terminates the program with a farewell message.

---

## Author
**Fernanda Denise Adamo**  
Data Analyst / Business Intelligence  
[![LinkedIn](https://shields.io)](https://linkedin/in/fadalid.com)
