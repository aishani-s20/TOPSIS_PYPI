# TOPSIS Command Line Tool

**TOPSIS-Aishani-102303250** is a package that provides a command-line implementation of the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** method for multi-criteria decision making.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install this package.

```bash
pip install Topsis-Aishani-102303250

---

## Usage

You can use this package via the command line.  
The input file must be a **CSV file containing numeric data**.

---

## Command Syntax

```bash
topsis <InputDataFile> <Weights> <Impacts> <OutputResultFileName>
```

---

## Arguments

| Argument | Description |
|--------|-------------|
| `InputDataFile` | Path to the input CSV file |
| `Weights` | Comma-separated numerical weights (e.g., `1,1,1,2`) |
| `Impacts` | Comma-separated signs (`+` or `-`) (e.g., `+,+,-,+`) |
| `OutputResultFileName` | Name of the output CSV file |

> **Note:**  
> If weights or impacts contain spaces, enclose them in double quotes.  
> Example: `"1, 1, 1, 2"`

---

## Example

### Sample Input (`data.csv`)

| Model | Storage | Camera | Price | Looks |
|------|---------|--------|-------|-------|
| M1 | 16 | 12 | 250 | 5 |
| M2 | 16 | 8 | 200 | 3 |
| M3 | 32 | 16 | 300 | 4 |
| M4 | 32 | 8 | 275 | 4 |
| M5 | 16 | 16 | 225 | 2 |


---

### Execution

Run the following command in your terminal:

```bash
topsis data.csv "0.25,0.25,0.25,0.25" "+,+,-,+" result.csv
```

---

### Output (`result.csv`)

The output file contains the original data along with two additional columns:
- **Topsis Score**
- **Rank**

| Model | Storage | Camera | Price | Looks | Topsis Score | Rank |
|------|---------|--------|-------|-------|--------------|------|
| M1 | 16 | 12 | 250 | 5 | 0.53428 | 3 |
| M2 | 16 | 8 | 200 | 3 | 0.30837 | 5 |
| M3 | 32 | 16 | 300 | 4 | 0.69163 | 1 |
| M4 | 32 | 8 | 275 | 4 | 0.53474 | 2 |
| M5 | 16 | 16 | 225 | 2 | 0.40105 | 4 |


---

## Constraints & Validations

- Input file must be a valid **CSV**.
- Input file must contain **at least three columns**.
- The **first column** is assumed to be the object/alternative name and is excluded from calculations.
- All columns from the **second column onward must be numeric**.
- Number of **weights** must match the number of feature columns.
- Number of **impacts** must match the number of feature columns.
- Impacts must be either:
  - `+` → Positive impact  
  - `-` → Negative impact  

---

## Interpretation

- A **higher TOPSIS score** indicates a better alternative.
- **Rank 1** represents the most preferred option based on given weights and impacts.

---

## License

This project is licensed under the MIT License.