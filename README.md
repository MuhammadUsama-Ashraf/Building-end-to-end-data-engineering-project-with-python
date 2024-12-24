# Building a Database Using Python

## Overview

This repository provides a comprehensive guide for creating and managing a PostgreSQL database using Python. It demonstrates essential database operations such as connecting to a PostgreSQL instance, creating tables, inserting records, and querying data. Additionally, it includes steps for importing and uploading datasets, making it ideal for end-to-end database management and data engineering tasks.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Key Features](#key-features)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Usage Guide](#usage-guide)
6. [Code Examples](#code-examples)
7. [Dataset Management](#dataset-management)
8. [Contributing](#contributing)
9. [License](#license)

---

## Introduction

Efficient database management is a cornerstone of software development. This project showcases:

- How to establish a database connection using Python.
- Methods for creating and managing PostgreSQL databases and tables.
- Secure data manipulation using parameterized queries.
- Practical CRUD (Create, Read, Update, Delete) operations.
- Dataset integration and uploading.

This guide is tailored for both beginners and experienced developers, offering scalable and reusable solutions.

---

## Key Features

- **Seamless Database Connectivity**: Integrate PostgreSQL into your Python applications effortlessly.
- **Automated Database Creation**: Create new databases programmatically.
- **Flexible Table Management**: Define, modify, and delete tables with ease.
- **Secure Data Handling**: Utilize parameterized queries to prevent SQL injection.
- **Dataset Integration**: Import and upload datasets for analysis.
- **Extensibility**: Designed for diverse database applications.

---

## Prerequisites

Ensure the following tools and libraries are installed:

- Python 3.7 or higher
- PostgreSQL (installed and running)
- `pip` for managing Python packages

---

## Installation

### Steps to Set Up the Project

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure the PostgreSQL connection in the script or notebook by updating the credentials:
   ```python
   conn = psycopg2.connect(
       host="127.0.0.1",
       database="postgres",
       user="postgres",
       password="your_password"
   )
   ```

4. Launch the Jupyter Notebook:
   ```bash
   jupyter notebook "Building Database using python.ipynb"
   ```

---

## Usage Guide

### Step 1: Database Creation

Execute the notebook cells to create a new database named `myfirstdb`.

### Step 2: Table Creation

Define a `student` table with the following schema:

| Column Name    | Data Type | Description              |
|----------------|-----------|--------------------------|
| `student_id`   | `INT`     | Unique identifier for students |
| `student_name` | `VARCHAR` | Name of the student      |
| `age`          | `INT`     | Age of the student       |
| `gender`       | `VARCHAR` | Gender of the student    |
| `marks`        | `INT`     | Marks obtained by the student |

### Step 3: Data Operations

- **Insert Data**: Add records to the `student` table using parameterized queries.
- **Query Data**: Retrieve data using SQL queries.
- **Modify Data**: Update or delete records as required.

---

## Code Examples

### Inserting Data

```python
cursor.execute(
    """
    INSERT INTO student (student_id, student_name, age, gender, marks)
    VALUES (%s, %s, %s, %s, %s)
    """,
    (1, 'John Doe', 20, 'Male', 85)
)
```

### Querying Data

```python
cursor.execute("SELECT * FROM student;")
for row in cursor.fetchall():
    print(row)
```

---

## Dataset Management

### Imported Datasets

This project includes the following datasets:

1. **Dataset 1**: Contains demographic data for students.
2. **Dataset 2**: Academic performance metrics.
3. **Dataset 3**: Additional metadata and attributes.

### Uploading Datasets

Follow these steps to upload datasets to the PostgreSQL database:

1. Load the dataset using Pandas:
   ```python
   import pandas as pd
   data = pd.read_csv("dataset1.csv")
   ```

2. Upload the dataset to a table:
   ```python
   from sqlalchemy import create_engine
   engine = create_engine('postgresql://postgres:your_password@localhost:5432/myfirstdb')
   data.to_sql('student_data', engine, if_exists='replace', index=False)
   ```

3. Verify the upload:
   ```python
   cursor.execute("SELECT * FROM student_data;")
   for row in cursor.fetchall():
       print(row)
   ```

---

## Contributing

We welcome contributions from the community! To contribute:

1. Fork the repository.
2. Create a new feature branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes with a descriptive message:
   ```bash
   git commit -m "Add feature description"
   ```
4. Push your branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request for review.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for detailed terms.

---

Feel free to reach out with questions, suggestions, or issues by opening an issue in this repository.
