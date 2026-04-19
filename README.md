
# flake8-only-english

`⭐️ Thanks everyone who has starred the project, it means a lot!`

[![PyPI version](https://img.shields.io/pypi/v/flake8-only-english.svg?logo=pypi&logoColor=white)](https://pypi.org/project/flake8-only-english/)
Install from **PyPI** by clicking the badge above

[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?logo=github&logoColor=white)](https://github.com/AlgorithmAlchemy/flake8-only-english)  
View the **source code on GitHub**

![Downloads](https://pepy.tech/badge/flake8-only-english)
![License](https://img.shields.io/pypi/l/flake8-only-english.svg)

---

## Overview

**flake8-only-english** is a Flake8 plugin that enforces English-only text in Python code.

It detects and reports any **non-ASCII / non-English characters** in:

- comments
- docstrings
- string literals

This helps maintain consistency and readability in international teams and corporate codebases.

---

## Features

- Detects non-English text in:
  - comments (`# ...`)
  - docstrings (`""" ... """`, `''' ... '''`)
  - string literals (`"..."`, `'...'`, f-strings, raw strings)
- Supports:
  - nested structures
  - f-strings
  - async functions, classes, properties
- Respects `# noqa`:
  - `# noqa`
  - `# noqa: NLE001`
  - `# noqa: NLE002`
  - `# noqa: NLE003`
- Ignores:
  - URLs
  - numeric-only strings/comments
  - whitespace-only content
- Fully compatible with:
  - Flake8
  - pre-commit

---

## Installation

```bash
pip install flake8-only-english
````

Uninstall:

```bash
pip uninstall flake8-only-english
```

---

## Usage

Run with Flake8:

```bash
flake8 .
```

Filter only this plugin:

```bash
flake8 --select=NLE
```

Specific rules:

```bash
flake8 --select=NLE001  # comments
flake8 --select=NLE002  # strings
flake8 --select=NLE003  # docstrings
```

---

## Example

```python
# Valid
def hello():
    """Valid English docstring"""
    return "Hello world"
```

```python
# Invalid
def hello():
    """Привет"""
    return "Hello"
```

Output:

```
example.py:3:0: NLE003 Non-English text in docstring
```

---

## Error Codes

* **NLE001** — Non-English text in comment
* **NLE002** — Non-English text in string literal
* **NLE003** — Non-English text in docstring

---

## Configuration

Disable checks via Flake8 options:

```bash
flake8 --no-nle-comments
flake8 --no-nle-strings
```

---

## Ignoring Errors

Use `noqa`:

```python
print("Привет")  # noqa: NLE002
```

Disable all checks on a line:

```python
print("Привет")  # noqa
```

---

## pre-commit Integration

```yaml
repos:
  - repo: https://github.com/AlgorithmAlchemy/flake8-only-english
    rev: v0.4.2
    hooks:
      - id: flake8
        additional_dependencies: [flake8-only-english]
```

Run:

```bash
pre-commit run --all-files
```

---

## Development

```bash
git clone https://github.com/AlgorithmAlchemy/flake8-only-english
cd flake8-only-english
pip install -e .[dev]
pytest
```

---

## License

MIT License © 2026 AlgorithmAlchemy
