# 🧾 GPay Transaction Parser

Extract and analyze transaction data from your **Google Pay (GPay) transaction history PDF** using Python. This script parses the PDF, extracts structured transaction details (like **date, merchant, amount, and type**), and outputs them as **CSV or JSON** for further analysis.

## 🚀 Features

-   🧠 Auto-detects tables and text layout in GPay PDFs
-   💸 Extracts transaction date, description, amount, and status
-   📊 Exports data to CSV and JSON
-   ⚡ Uses pdfplumber for accurate PDF parsing
-   🔍 Data cleaning and normalization (for easy filtering/sorting)

## 🏗️ Project Structure

```plaintext
gpay-parser/
├── main.py                    # Entry point script
|
├── media/
│   └── gpay_statement.pdf     # GPay PDF 
│
├── output/
│   ├── transactions.csv
│   └── transactions.json
│
├── requirements.txt
└── README.md
```

## ⚙️ Setup

### 1️⃣ Clone the repo

```bash
git clone https://github.com/ibnu-umer/gpay-parser.git
cd gpay-parser
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Add your GPay PDF

Place your exported Google Pay statement PDF in the `media/` folder.

### 🧩 Usage

Basic Command

```bash
python main.py --file media/gpay_statement.pdf
```

### 🧩 Options

| Flag       | Description                              | Example                             |
| ---------- | ---------------------------------------- | ----------------------------------- |
| `--file`   | Path to GPay statement PDF               | `--file media/gpay_statement.pdf` |
| `--output` | Output folder                            | `--output output/`                  |
| `--format` | Output format (`csv`, `json`, or `both`) | `--format both`                     |
| `--clean`  | Apply cleaning/normalization             | `--clean`                           |

### Example:

```bash
python main.py --file media/gpay_statement.pdf --format both --clean
```

## 🧠 How It Works

-   pdfplumber opens and reads the text layout from the PDF.
-   A parser scans for known GPay patterns (e.g., Paid to, Received from, UPI Ref, etc.).
-   Each transaction line is tokenized and structured into a dictionary.
-   Data is normalized.
-   Exporter writes the output as CSV/JSON.

## 🧰 Dependencies

-   pdfplumber – PDF parsing
-   pandas – Data handling and export
-   argparse – Command-line interface
-   re – Regex-based text parsing

**Install via:**

```bash
pip install pdfplumber pandas
```

## 🧼 Example Output (CSV)

| Date       | Description         | Amount | Type   | Status     |
| ---------- | ------------------- | ------ | ------ | ---------- |
| 2024-05-01 | Paid to Swiggy      | 450.00 | Debit  | Successful |
| 2024-05-03 | Received from Rahul | 200.00 | Credit | Successful |

## 🧩 Next Steps

-   Add OCR fallback for scanned PDFs
-   Detect refunds and failed transactions
-   And dashboard visualization (Matplotlib/Plotly)
-   Package as CLI tool (pip install gpay-parser)

## ⚠️ Disclaimer

This project is not affiliated with Google or Google Pay.
Use only for personal finance tracking and non-commercial purposes.
