# 🧠 Supply Chain Management (SCM) Product List Cleaning using GenAI (Python + OpenAI API)

## 📌 Project Overview

This project focuses on automating the cleaning and structuring of raw Supply Chain product master data using Generative AI (OpenAI API) integrated within a Python ETL pipeline.

The objective was to convert messy, inconsistent product names into structured fields:

- `main_product`
- `product_type`
- `SKU`

The solution uses prompt engineering + JSON-enforced responses to ensure structured, production-ready outputs.

---

# 🚀 Problem Statement

The SCM master product list contained:

- Inconsistent naming formats
- Embedded SKU values (e.g., "50g", "Rs.10", "6PCS")
- Mixed casing
- Spelling errors (e.g., "Mashroom", "Agarwatti")
- Random spacing
- Brand + variant merged together

Manual cleaning was:
- Time consuming
- Error prone
- Not scalable

---

# 🛠 Solution Architecture

### 🔹 Technology Stack

- Python
- OpenAI API (GPT-4o)
- Pandas
- JSON enforcement mode
- Chunk-based saving
- Resume-safe processing logic

---

# 🧠 GenAI Prompt Engineering Logic

The system prompt was carefully designed to:

1. Identify SKU first (numbers, price, weight).
2. Extract main product (brand or primary identity).
3. Extract product type (middle descriptive portion).
4. Correct spelling errors automatically.
5. Normalize casing.
6. Enforce strict JSON output format.

### Example:

Input:
```
Oyester Mashroom
```

Output:
```json
{
  "main_product": "Oyster Mushroom",
  "product_type": "",
  "SKU": ""
}
```

Input:
```
Parle-G Gold Biscuits -10 RS
```

Output:
```json
{
  "main_product": "Parle-G",
  "product_type": "Gold Biscuits",
  "SKU": "10 RS"
}
```

---

# 🔄 ETL Pipeline Design

### 1️⃣ Data Extraction
- Loaded raw CSV product master file.
- Handled missing or invalid rows before API calls.

### 2️⃣ Transformation (AI-Based Cleaning)
- Sent one product string at a time to OpenAI.
- Used `response_format={"type": "json_object"}` to enforce structured output.
- Set temperature = 0 for deterministic responses.
- Handled API failures with retry logic.

### 3️⃣ Incremental Loading
- Implemented chunk saving (50 rows per batch).
- Resume capability:
  - If output file exists → continue from last processed row.
- Prevented data loss in long-running jobs.

---

# 📊 Key Features

✔ AI-based structured product extraction  
✔ Automatic spelling correction  
✔ SKU detection (weight, price, count)  
✔ Deterministic output (JSON enforced mode)  
✔ Chunk-based saving to prevent crash data loss  
✔ Resume-safe execution  
✔ Error handling & retry mechanism  

---

# 📈 Business Impact

- Reduced manual product cleaning effort significantly.
- Standardized master product naming structure.
- Improved downstream analytics accuracy in SCM dashboards.
- Enabled consistent SKU-level reporting.
- Made product master usable for inventory & sales analytics.

---

# 🧪 Example Workflow

1. Load messy product CSV.
2. Process each product name through AI.
3. Extract structured fields.
4. Append results to output file.
5. Resume automatically if interrupted.

---

# 🧩 Why This Project is Important

This project demonstrates:

- Practical application of Generative AI in real business workflows.
- Prompt engineering for structured data extraction.
- Production-level Python scripting.
- ETL pipeline thinking.
- Data standardization for Supply Chain analytics.

---

# 🏷 Tech Keywords (For Recruiters)

Python, OpenAI API, GPT-4o, Prompt Engineering, JSON Parsing, ETL Pipeline, Data Cleaning, Supply Chain Analytics, Pandas, Automation

---

> This project showcases how Generative AI can be integrated into data engineering workflows to automate complex data cleaning tasks at scale.
