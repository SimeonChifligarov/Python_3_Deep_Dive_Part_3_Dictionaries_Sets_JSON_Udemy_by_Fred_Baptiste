# Python 3 Deep Dive — Part 3

### Dictionaries, Sets, Hashing, Serialization & JSON

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Course](https://img.shields.io/badge/Udemy-Python%203%20Deep%20Dive-A435F0?logo=udemy&logoColor=white)](https://www.udemy.com/)

A structured collection of Jupyter notebooks, exercises, experiments, and project solutions created while studying **Python 3: Deep Dive (Part 3 — Dictionaries, Sets, JSON)** by **Dr. Fred Baptiste**.

> **Important**
>
> This is an independent educational repository containing personal notes, implementations, experiments, and solutions created during the learning process.  
> It is **not an official course repository** and is **not a replacement for the original course**.

---

## Table of Contents

- [Overview](#overview)
- [Topics Covered](#topics-covered)
  - [Dictionaries](#dictionaries)
  - [Hashing and Hashability](#hashing-and-hashability)
  - [Sets and Frozen Sets](#sets-and-frozen-sets)
  - [Serialization and Deserialization](#serialization-and-deserialization)
  - [JSON](#json)
  - [Specialized Dictionaries](#specialized-dictionaries)
- [Learning Objectives](#learning-objectives)
- [Repository Structure](#repository-structure)
- [Project](#project)
- [Notebook Conventions](#notebook-conventions)
- [Getting Started](#getting-started)
- [Recommended Learning Path](#recommended-learning-path)
- [Educational Scope](#educational-scope)
- [Contributing](#contributing)
- [Course Attribution and Disclaimer](#course-attribution-and-disclaimer)
- [Related Repository](#related-repository)
- [License](#license)
- [Author](#author)

---

## Overview

This repository documents my progress through the third part of **Fred Baptiste's Python 3 Deep Dive series**.

The material focuses on Python's hash-based data structures and structured-data representation — from the mechanics of dictionary keys and hashing to sets, serialization, JSON processing, schema-like validation, and specialized mapping types from Python's standard library.

The repository includes:

- Executable Jupyter notebooks organized by course section
- Detailed explorations of Python dictionaries and mapping behavior
- Examples involving hashing, equality, and hashability
- Dictionary views, merging, updating, and copying
- Set theory and practical set operations
- Mutable `set` and immutable `frozenset` objects
- Serialization and deserialization techniques
- JSON encoding and decoding
- Custom handling of non-standard JSON types
- Specialized mapping classes from `collections`
- Coding exercises and experimentation
- A practical recursive dictionary-validation project
- Additional notes covering Python language updates and related topics

The goal is not simply to learn dictionary and JSON syntax, but to understand **why Python's hash-based containers behave the way they do**, how Python converts data between representations, and how these concepts apply to real software systems such as APIs, configuration processing, data pipelines, caching, validation, and data interchange.

---

# Topics Covered

## Dictionaries

Python dictionaries are one of the language's most important data structures and form the foundation of many higher-level Python concepts.

Topics explored include:

- Creating dictionaries
- Dictionary literals and the `dict()` constructor
- Dictionary comprehensions
- Reading, inserting, updating, and deleting values
- Membership testing
- Dictionary iteration
- Keys, values, and key-value pairs
- `keys()`, `values()`, and `items()`
- Dictionary views
- Dynamic behavior of dictionary views
- Merging dictionaries
- Updating dictionaries
- Copying dictionaries
- Shallow-copy considerations
- Dictionary equality
- Dictionary ordering behavior
- Nested dictionaries
- Dictionaries as lookup structures
- Dictionaries as lightweight structured records
- Practical mapping patterns

A central theme is understanding that dictionaries are **hash-table-based mappings**, rather than simply collections of key-value pairs.

---

## Hashing and Hashability

Dictionary keys and set members depend on Python's hashing model.

This section explores:

- The built-in `hash()` function
- Hash values
- Hashable versus unhashable objects
- Immutable objects and hashability
- Why lists and dictionaries cannot normally be dictionary keys
- Why tuples may or may not be hashable
- Equality and hashing
- The relationship between `__eq__()` and `__hash__()`
- Hashing custom classes
- Using custom objects as dictionary keys
- Hash consistency requirements
- Hash collisions
- Identity versus equality
- Designing objects suitable for hash-based containers

An important invariant is:

```python
a == b  =>  hash(a) == hash(b)
```

Equal hash values do **not** necessarily imply equal objects, but objects considered equal must produce compatible hashes when they are hashable.

Understanding this relationship is essential when designing custom classes intended for use as dictionary keys or set elements.

---

## Sets and Frozen Sets

Python sets use hashing to provide collections of unique elements with efficient membership testing.

Topics include:

- Creating sets
- Creating empty sets
- Removing duplicate values
- Membership testing
- Adding and removing elements
- Set comprehensions
- Set equality
- Subsets and supersets
- Proper subsets and proper supersets
- Disjoint sets
- Union
- Intersection
- Difference
- Symmetric difference
- Update operations
- In-place set operations
- Copying sets
- Mutable versus immutable set types
- `frozenset`
- Using frozen sets as dictionary keys
- Dictionary views and set-like behavior

Common mathematical operations include:

```python
a | b   # union
a & b   # intersection
a - b   # difference
a ^ b   # symmetric difference
```

Sets are especially useful for:

- Deduplication
- Fast membership checks
- Comparing collections
- Detecting overlap
- Finding missing or additional values
- Relationship analysis between datasets

---

## Serialization and Deserialization

Serialization converts an in-memory Python object or data structure into a representation suitable for storage or transmission.

Deserialization performs the inverse transformation.

Concepts explored include:

- What serialization means
- What deserialization means
- Object representation
- Text versus binary serialization
- Serializing Python data structures
- Reconstructing objects from serialized representations
- Persisting structured data
- Data interchange
- Type preservation
- Serialization limitations
- Custom serialization strategies
- Handling nested structures
- Working with complex application data

These concepts appear frequently in:

- REST APIs
- Messaging systems
- Configuration files
- Data pipelines
- Caching
- Persistent application state
- Inter-process communication
- Distributed systems

---

## JSON

**JSON — JavaScript Object Notation** — is one of the most widely used formats for exchanging structured data.

Python provides JSON support through the standard-library `json` module.

Core operations include:

```python
import json

data = {
    "name": "Python",
    "type": "programming language",
    "dynamic": True
}

json_string = json.dumps(data)

restored = json.loads(json_string)
```

Topics explored include:

- JSON syntax
- Python-to-JSON type conversion
- JSON-to-Python type conversion
- `json.dumps()`
- `json.loads()`
- `json.dump()`
- `json.load()`
- Reading JSON from files
- Writing JSON to files
- Formatting JSON output
- Indentation
- Sorting keys
- JSON-compatible data types
- Handling unsupported Python objects
- Custom serialization
- Custom encoding
- Custom decoding
- Object hooks
- Nested JSON documents
- Serializing application objects
- Reconstructing richer Python structures
- Validation concepts for JSON-like data

Typical Python-to-JSON mappings include:

| Python | JSON |
|---|---|
| `dict` | object |
| `list`, `tuple` | array |
| `str` | string |
| `int`, `float` | number |
| `True` | `true` |
| `False` | `false` |
| `None` | `null` |

Not every Python object has a direct JSON representation, which makes custom serialization an important part of working with application-level objects.

---

## Specialized Dictionaries

Python's `collections` module provides specialized mapping implementations designed for common data-processing patterns.

### `defaultdict`

Provides automatic default values for missing keys.

```python
from collections import defaultdict

word_counts = defaultdict(int)

for word in words:
    word_counts[word] += 1
```

Useful for:

- Grouping
- Counting
- Accumulation
- Avoiding repetitive missing-key checks

---

### `OrderedDict`

A dictionary implementation with explicit order-related behavior and additional order-manipulation methods.

Topics include:

- Ordered mappings
- Reordering keys
- `move_to_end()`
- Order-sensitive equality
- Differences between `OrderedDict` and modern plain dictionaries

---

### `Counter`

A dictionary subclass designed for counting hashable objects.

```python
from collections import Counter

counts = Counter("mississippi")
```

Useful for:

- Frequency analysis
- Histograms
- Most-common-element queries
- Multiset-style operations

---

### `ChainMap`

Combines multiple mappings into a single logical view.

```python
from collections import ChainMap

configuration = ChainMap(
    command_line_options,
    environment_options,
    defaults
)
```

Useful for:

- Layered configuration
- Scope resolution
- Fallback mappings
- Combining mappings without copying them

---

### `UserDict`

A wrapper around dictionary behavior intended to make custom mapping implementations easier and safer than directly subclassing `dict` in certain situations.

It is useful when implementing:

- Validated dictionaries
- Restricted mappings
- Normalized-key dictionaries
- Custom dictionary APIs
- Domain-specific mapping behavior

---

# Learning Objectives

By working through this repository, the learner should be able to:

- Explain how Python dictionaries work conceptually
- Understand the relationship between dictionaries and hash tables
- Distinguish between hashable and unhashable objects
- Explain the relationship between equality and hashing
- Implement custom classes that behave correctly as dictionary keys
- Work effectively with dictionary views
- Merge, update, and copy mappings
- Select appropriate dictionary access patterns
- Use sets for membership testing and uniqueness
- Apply union, intersection, difference, and symmetric difference
- Distinguish between `set` and `frozenset`
- Use immutable sets in hash-based structures
- Explain serialization and deserialization
- Convert Python structures to and from JSON
- Customize JSON serialization for unsupported objects
- Work with nested structured data
- Validate dictionary-like structures recursively
- Use `defaultdict`, `OrderedDict`, `Counter`, `ChainMap`, and `UserDict`
- Choose the appropriate mapping abstraction for a particular problem
- Reason about the trade-offs between convenience, mutability, ordering, identity, equality, and hashability

---

# Repository Structure

| Section | Subject | Description |
|---|---|---|
| `Section_03_Dictionaries` | Dictionaries | Dictionary creation, common operations, views, updating, merging, copying, custom classes, and hashing |
| `Section_04_Coding_Exercises` | Dictionary Exercises | Practical exercises reinforcing dictionary and hashing concepts |
| `Section_05_Sets` | Sets | Set creation, set algebra, update operations, copying, frozen sets, and dictionary views |
| `Section_06_Project_1` | Project 1 | Recursive validation of nested dictionary structures against a template |
| `Section_07_Serialization_and_Deserialization` | Serialization | Serialization concepts, JSON encoding/decoding, custom objects, and structured-data interchange |
| `Section_08_Coding_Exercises` | Serialization Exercises | Practical exercises involving serialization and structured data |
| `Section_09_Specialized_Dictionaries` | Specialized Dictionaries | `defaultdict`, `OrderedDict`, `Counter`, `ChainMap`, and `UserDict` |
| `Section_10_Coding_Exercises` | Mapping Exercises | Exercises involving specialized dictionary types |
| `Section_11_Python_Updates` | Python Updates | Relevant dictionary, set, and language changes introduced in newer Python versions |
| `Section_12_Extras` | Extras | Additional experiments and complementary material |

> Folder and notebook names may reflect the organization used while working through the course.

---

# Project

## Project 1 — Recursive Dictionary Structure Validation

The project applies dictionary and set concepts to a problem resembling **validation of structured JSON input received by an API**.

The objective is to validate one nested dictionary against a template describing:

- Required keys
- Nested structure
- Expected value types
- Invalid missing keys
- Invalid additional keys
- Type mismatches

For example, a template may look like:

```python
template = {
    "user_id": int,
    "name": {
        "first": str,
        "last": str
    },
    "bio": {
        "dob": {
            "year": int,
            "month": int,
            "day": int
        },
        "birthplace": {
            "country": str,
            "city": str
        }
    }
}
```

A valid data structure must contain the same structure while supplying values of the expected types:

```python
user = {
    "user_id": 100,
    "name": {
        "first": "John",
        "last": "Doe"
    },
    "bio": {
        "dob": {
            "year": 1990,
            "month": 5,
            "day": 10
        },
        "birthplace": {
            "country": "Bulgaria",
            "city": "Sofia"
        }
    }
}
```

The validator must recursively traverse both structures and identify problems such as:

```text
mismatched keys: bio.birthplace.city
```

or:

```text
bad type: bio.dob.month
```

The project reinforces:

- Recursive algorithms
- Nested dictionaries
- Set-based key comparison
- Runtime type checking
- Path construction
- Error reporting
- Separation of validation logic
- Exception-based error handling
- Schema-validation concepts

Although intentionally simplified for educational purposes, the underlying problem closely resembles real-world data validation performed by API and schema-validation libraries.

---

# Notebook Conventions

The repository primarily uses Jupyter notebooks for experimentation and explanation.

Common naming patterns may include:

| Pattern | Meaning |
|---|---|
| `*.ipynb` | Core explanation, implementation, or exploration |
| `*_advanced.ipynb` | Extended implementation or deeper exploration |
| `*_advanced_extra.ipynb` | Additional experiments beyond the main material |
| `*_Description.ipynb` | Exercise or project requirements |
| `*_Solution*.ipynb` | Goal-based or complete solutions |

Depending on the section, notebooks may also be accompanied by:

- JSON files
- Text files
- Sample datasets
- Serialized data
- Python source files
- Generated output files

The notebooks are intended to be **executed, modified, broken, repaired, and experimented with** rather than treated as static documentation.

---

# Getting Started

## Prerequisites

You will need:

- **Python 3**
- **Git**
- **Jupyter Notebook** or **JupyterLab**
- A Python virtual environment — recommended

A recent Python 3 release is recommended.

Some notebooks originated from earlier Python 3 environments, so minor compatibility differences may occasionally appear when running them on newer interpreter versions.

---

## Clone the Repository

```bash
git clone https://github.com/SimeonChifligarov/Python_3_Deep_Dive_Part_3_Dictionaries_Sets_JSON_Udemy_by_Fred_Baptiste.git
```

```bash
cd Python_3_Deep_Dive_Part_3_Dictionaries_Sets_JSON_Udemy_by_Fred_Baptiste
```

---

## Create a Virtual Environment

### Linux and macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows PowerShell

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

### Windows Command Prompt

```cmd
py -m venv .venv
.venv\Scripts\activate.bat
```

---

## Install JupyterLab

```bash
python -m pip install --upgrade pip
python -m pip install jupyterlab
```

Most of the core material uses Python's standard library.

If an individual notebook explores an additional third-party library, install the dependency required by that notebook separately.

---

## Start JupyterLab

```bash
jupyter lab
```

Navigate to the desired section and open a notebook.

---

# Recommended Learning Path

For the best learning experience:

1. Follow the numbered sections in order.
2. Run each notebook cell rather than only reading the code.
3. Modify dictionary keys and values and observe the resulting behavior.
4. Experiment with mutable and immutable objects as dictionary keys.
5. Override `__eq__()` and `__hash__()` in custom classes and inspect the consequences.
6. Compare dictionary views before and after modifying the underlying dictionary.
7. Re-create set operations manually before using their built-in equivalents.
8. Complete coding exercises without consulting solutions first.
9. Attempt Project 1 independently before reviewing the provided solution.
10. Serialize increasingly complex Python structures to JSON.
11. Experiment with objects that JSON cannot serialize automatically.
12. Compare specialized dictionaries with equivalent plain-dictionary implementations.
13. Rebuild important examples in a separate notebook from memory.

> **Tip**
>
> Dictionaries and sets become much easier to understand once you stop thinking of them only as containers and start thinking in terms of **hashing, equality, identity, and lookup semantics**.

---

# Educational Scope

This repository is intended for **learning, experimentation, and reference**.

It is not designed as:

- An installable Python package
- A production application
- A reusable public API
- A benchmarking suite
- A comprehensive JSON-validation framework
- A production serialization library
- A substitute for the original course

Some implementations intentionally favor **clarity, experimentation, and explanation** over production architecture or optimization.

The notebooks may also contain multiple approaches to the same problem in order to explore different Python techniques.

---

# Contributing

Corrections and improvements are welcome.

Appropriate contributions include:

- Fixing typographical errors
- Correcting broken notebook cells
- Improving explanations
- Updating examples for newer Python versions
- Fixing portability issues
- Improving Markdown formatting
- Adding useful references
- Correcting technical inaccuracies

For significant changes, opening an issue before submitting a pull request is recommended.

Please keep contributions aligned with the repository's educational purpose.

---

# Course Attribution and Disclaimer

This repository was created while studying:

**Python 3: Deep Dive (Part 3 — Dictionaries, Sets, JSON)**  
Instructor: **Dr. Fred Baptiste**  
Platform: **Udemy**

The course, its original instructional material, and associated intellectual property belong to their respective author and rights holders.

This repository contains my own:

- Study notes
- Implementations
- Experiments
- Exercise solutions
- Project solutions
- Additional explanations

It is maintained independently and is **not affiliated with, endorsed by, or officially maintained by Fred Baptiste or Udemy**.

If you are interested in learning the material in its intended form, please support the instructor by obtaining the original course.

---

# Related Repository

This repository continues the learning path from:

### Python 3 Deep Dive — Part 2: Iterators & Generators

[Python_3_Deep_Dive_Part_2_Iterators_Generators_Udemy_by_Fred_Baptiste](https://github.com/SimeonChifligarov/Python_3_Deep_Dive_Part_2_Iterators_Generators_Udemy_by_Fred_Baptiste)

Part 2 focuses on:

- Sequences
- Iterables and iterators
- Generators
- `itertools`
- Context managers
- Generator-based coroutines
- Lazy evaluation and processing pipelines

Part 3 builds on those Python foundations by focusing on **hash-based data structures and structured-data representation**.

---

# License

This repository is licensed under the **MIT License**.

See the [LICENSE](LICENSE) file for details.

Course materials and intellectual property belonging to the original instructor or course platform remain subject to their respective terms and copyrights.

---

# Author

**Simeon Chifligarov**

Data Engineer focused on Python, Apache Spark, Airflow, SQL, cloud-native data platforms, and maintainable software engineering.

- GitHub: [@SimeonChifligarov](https://github.com/SimeonChifligarov)
- LinkedIn: [Simeon Chifligarov](https://www.linkedin.com/in/simeon-chifligarov/)

---

If this repository is useful to you, consider giving it a ⭐.

More importantly, experiment with the notebooks — **Python's dictionaries, sets, and serialization mechanisms are best understood by observing their behavior directly.**
