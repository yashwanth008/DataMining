#  Apache Beam in Colab — End-to-End Demonstration

This project demonstrates how to use **Apache Beam (Python SDK)** in Google Colab using the **DirectRunner**.  
It covers all required Beam features for the assignment:

- ✅ Composite Transform  
- ✅ Pipeline I/O (Read/Write)  
- ✅ ParDo (DoFn)  
- ✅ Map and Filter  
- ✅ Partition  
- ✅ Windowing (FixedWindows)  
- ✅ *(Optional)* BeamML RunInference with scikit-learn  

---

## Overview

We simulate a small **sales dataset (`data/sales.csv`)** with event-time fields.  
The notebook and script demonstrate the following:

1. **Composite Transform (`CleanAndEnrich`)**  
   Combines parsing, filtering, computing revenue, and applying a ParDo discount.  
2. **Pipeline I/O** – Reads from CSV and writes JSON outputs.  
3. **ParDo (DoFn)** – Custom DoFn adds a discount field.  
4. **Map & Filter** – Used for enrichment and selection.  
5. **Partition** – Splits data into multiple outputs based on country.  
6. **Windowing** – Groups events into 30‑second fixed windows and sums SKU revenue.  
7. **BeamML** – (Optional) Demonstrates ML inference using a small scikit-learn model.  

---

## How to Run (in Google Colab)

```bash
# 1. Upload or unzip the project folder into Colab
!unzip -o beam_colab_project.zip -d /content/

# 2. Install dependencies
!pip -q install -r /content/beam_colab_project/requirements.txt

# 3. Run all pipelines
!python /content/beam_colab_project/src/beam_demo.py --base /content/beam_colab_project --run_all

# 4. View outputs in:
# /content/beam_colab_project/out/
```

---

##  Project Structure

```
beam_colab_project/
├── data/
│   └── sales.csv
├── src/
│   └── <main file>.ipynb
├── out/
├── README.md
```

---

## Key Beam Concepts Demonstrated

| Feature | Beam API Used | Description |
|----------|---------------|--------------|
| **Composite Transform** | `PTransform` | Groups multiple steps together |
| **Pipeline I/O** | `ReadFromText`, `WriteToText` | File input/output |
| **ParDo / DoFn** | `ParDo(AddDiscountDoFn())` | Adds custom field per element |
| **Map / Filter** | `beam.Map`, `beam.Filter` | Basic elementwise transforms |
| **Partition** | `beam.Partition` | Splits data by country |
| **Windowing** | `WindowInto(FixedWindows(30))` | Groups events into time windows |
| **BeamML** | `RunInference(SklearnModelHandlerNumpy)` | ML model inference inside Beam |

---

## Sample Outputs

### Partitioned Output (US / CA / Other)
```json
{"order_id": 2, "sku": "A100", "country": "US", "quantity": 2,
 "unit_price": 10.0, "revenue": 20.0, "discount": 0.0, "final_revenue": 20.0}
```

### Windowed Revenue Output
```json
{"window_start": "2025-10-26T12:00:00",
 "window_end": "2025-10-26T12:00:30",
 "sku": "A100", "window_revenue": 20.0}
```

---

## Learning Outcomes

- Build and run Beam pipelines in Colab or locally.  
- Understand composite transforms, ParDo, partitioning, and windowing.  
- Learn basic BeamML integration.  
- Produce explainable, reproducible outputs for submission.  

---

## Requirements

- Python 3.9 – 3.12  
- Apache Beam 2.58+  
- scikit-learn ≥ 1.2  
- joblib ≥ 1.3  

---

##  Author

**Venkata Yashwanth Paladugu**  
_Data Science Assignment – Apache Beam Features Demo_
