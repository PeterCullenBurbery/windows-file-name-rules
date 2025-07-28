# Windows File Name Rules


[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.16550142.svg)](https://doi.org/10.5281/zenodo.16550142)


This repository contains a structured dataset in JSON format documenting **invalid characters** and **reserved names** for filenames on Windows. It is intended for developers, educators, or tool creators working on filename validation, cross-platform file handling, or automated sanitation of file input.

## 📦 Included Files

- `windows_filename_rules.json` — the main dataset containing:
  - Invalid characters for Windows filenames
  - Character groupings (e.g., wildcards, path separators)
  - Reserved names (e.g., `CON`, `LPT1`)
- `file-names.ipynb` — a Jupyter notebook to explore and test the rules programmatically
- `README.md` — this file
- `LICENSE` — [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/legalcode.txt)

## 📄 JSON Structure

```json
{
  "table_of_characters": [...],
  "table_of_groups_of_characters": [...],
  "table_of_characters_in_groups": [...],
  "reserved_names": [...]
}
```

Each reserved name includes a `reason` explaining why it is disallowed on Windows. For example:
```json
{ "name": "PRN", "reason": "Reserved device name: printer" }
```

## ✅ Example Use Case

You can use this data to:

- Validate or sanitize filenames in cross-platform apps
- Educate about filesystem rules
- Run automated tests using tools like `unittest` or `pytest`

### Example validation snippet (Python):

```python
with open("windows_filename_rules.json") as f:
    data = json.load(f)

def is_reserved_name(name):
    return any(entry["name"].lower() == name.lower() for entry in data["reserved_names"])
```

## 💡 Why It Matters

Windows disallows certain characters and names regardless of file extension. These rules stem from legacy DOS device names and system-reserved syntax.

Examples of invalid names:
- `CON`, `NUL`, `AUX`
- `COM1`, `LPT1`
- Names ending with space or period
- Names containing characters like `*`, `?`, `|`, `"`

## 📚 License

This project is dedicated to the public domain under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).

## 🔗 Related Publishing Options

This dataset is also suitable for publication on:
- [Hugging Face Datasets](https://huggingface.co/datasets)
- [Zenodo](https://zenodo.org/)
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Figshare](https://figshare.com/)

## 🔖 Citation

If you use this dataset, please cite it as:

> Peter Cullen Burbery. (2025). *Windows file name rules* (v1.1.0). Zenodo. https://doi.org/10.5281/zenodo.16550142