# MASP Dataset: Multi-Agent Service Pattern Recommendation

This repository provides the documentation and download instructions for the **MASP Dataset**, a comprehensive, large-scale benchmark designed for Multi-Agent Service Pattern (MASP) recommendation tasks. It bridges the semantic and structural gap between unstructured user requirements and complex collaborative workflows.

## 📥 Download and Extraction

Due to its large scale, the complete dataset is compressed as a `.tar.gz` file and hosted on Baidu Netdisk.

- **Baidu Netdisk Link:** https://pan.baidu.com/s/1RioTJ38KOwGEwbUD43axIw 
- **Access Code:** ez2j


After downloading the `MASP.tar.gz` archive, you can extract it to your preferred directory using the following command:

```bash
# Example extraction to your local path
tar -xzvf MASP.tar.gz -C /home/zzh/Service_Pattern_Rec/pattern_dataset/

```

## 📊 Dataset Overview

The rapid development of service computing drives the widespread adoption of multi-agent systems. This dataset addresses the critical data scarcity challenge in MASP recommendation by providing high-quality mappings between complex structural workflows and constrained natural language user requirements.

* **Total Service Patterns:** 27,947
* **Total Requirements:** 55,850
* **Covered Domains:**
* 🛒 E-commerce (12,220 patterns / 24,440 requirements)
* 🏥 Healthcare (12,185 patterns / 24,326 requirements)
* 🏦 Finance (3,542 patterns / 7,084 requirements)


* **Average Tasks per Pattern:** ~10 nodes
* **Average Requirement Length:** 41.4 words
* **Average Description Length:** 207 characters

## 📂 Dataset Structure

Once extracted, the `MASP` dataset directory follows a hierarchical structure categorized by domain. Each pattern instance is stored in a numbered subfolder containing its metadata, multi-granularity descriptions, and topological structure:

```text
MASP/
├── ecommerce/             # MASPs and requirements for the E-commerce domain
│   ├── 0/
│   │   ├── meta.json               # Metadata containing user requirements and QoS constraints
│   │   ├── meta_descriptions.json  # Multi-granularity textual descriptions of the workflow
│   │   └── pattern.bpmn            # Multi-agent collaborative topology in BPMN format
│   ├── 1/
│   └── ...
├── fin/                   # MASPs and requirements for the Finance domain
│   ├── 0/
│   └── ...
└── health/                # MASPs and requirements for the Healthcare domain
    ├── 0/
    └── ...

```

## 🛠️ Data Format

Each entry consists of three files:

**1. `meta.json`**: Contains the semantic details, mapping a set of user requirements to the specific service pattern.

```json
{
    "Pattern_ID": 1,
    "Pattern_Title": "Slip-On Mules",
    "Pattern_Scenario": "user bought slip-on mules on an e-commerce platform , but the tracking hasn't updated for days, so user initiated a shipping complaint.",
    "Augment_Scenario": "time_optimized",
    "user_requirements": [
        {
            "persona": "Variant-Trigger Persona (e.g., Gift Recipient with Hard Deadline)",
            "query": "I need this resolved today—my sister’s birthday dinner is in under five hours and these slip-on mules were her gift. The tracking hasn’t moved in two days. Can you locate the package or send a replacement immediately?"
        },
        {
            "persona": "Variant-Trigger Persona (e.g., Small Business Reseller with Same-Day Fulfillment Promise)",
            "query": "I run a small boutique and promised same-day dispatch for pre-orders. One customer’s slip-on mules show no tracking movement since shipment, and I’m already getting complaints. I need a confirmed status or resolution within the next few hours to maintain trust."
        }
    ]
}

```


**2. `meta_descriptions.json`**: Contains text descriptions of the workflow at varying levels.

```json
{
    "Description1": "Slip-On Mules",
    "Description2": "user bought slip-on mules on an e-commerce platform , but the tracking hasn't updated for days, so user initiated a shipping complaint.",
    "Description3": "A standard quality slip-on mules sourced from reliable suppliers.",
    "Description4": "Shipping Complaint Resolution for Undelivered Slip-On Mules",
    "Description5": "This business process handles a customer's complaint about non-updating tracking for slip-on mules purchased on an e-commerce platform. The customer files a shipping complaint, which triggers the E-commerce Platform System to generate a shipping investigation package by reading the Customer Complaint Summary; this action produces three critical artifacts: the Carrier Tracking Log, the Order Fulfillment Record, and the Inventory Allocation Certificate. These documents are then passed to the Logistics Provider Team, which validates the package completeness and initiates escalation, simultaneously updating the Customer Complaint Summary with enriched operational context. The Logistics Provider Team then assesses the investigation outcome. If all data aligns and the carrier confirms delivery or locates the package, the complaint resolution is finalized. Conversely, if minor discrepancies are found in the tracking log that require re-validation without new data generation, the Logistics Provider Team loops back to re-execute the validation step using the existing package. If the Order Fulfillment Record or Inventory Allocation Certificate reveals material inconsistencies—such as mismatched SKUs or unallocated stock—the Logistics Provider Team requests the E-commerce Platform System to regenerate the entire shipping investigation package from scratch. Finally, if the investigation uncovers a systemic failure in the carrier’s tracking infrastructure affecting multiple orders, the Logistics Provider Team triggers a full restart of the complaint intake process to capture fresh customer input and initiate a broader diagnostic workflow.",
    "Description6": "A standard e-commerce service pattern."
}

```

**3. `pattern.bpmn`**: An XML-based Business Process Model and Notation (BPMN) file that formally defines the multi-role collaborative structure, execution nodes, and information flows for the MASP.

## 🚀 Usage

You can load and parse this dataset using standard Python libraries such as `json` and `os`.

```python
import os
import json

# Define the path to your extracted dataset
DATASET_ROOT = "./MASP"

# Example: Load metadata and descriptions for a Finance pattern
sample_dir = os.path.join(DATASET_ROOT, "fin", "0")
meta_path = os.path.join(sample_dir, "meta.json")
desc_path = os.path.join(sample_dir, "meta_descriptions.json")

if os.path.exists(meta_path) and os.path.exists(desc_path):
    # Load core metadata
    with open(meta_path, 'r', encoding='utf-8') as f:
        meta_data = json.load(f)
        print(f"Title: {meta_data.get('Pattern_Title')}")
        if 'user_requirements' in meta_data and len(meta_data['user_requirements']) > 0:
            print(f"Requirement: {meta_data['user_requirements'][0].get('requirement', '')}")
            
    # Load multi-granularity descriptions
    with open(desc_path, 'r', encoding='utf-8') as f:
        desc_data = json.load(f)
        print(f"Detailed Workflow (Desc 5): {desc_data.get('Description5')[:150]}...")
else:
    print("Dataset files not found. Please ensure it is downloaded and extracted correctly.")

```

## 📝 Citation

If you find this dataset useful in your research, please consider citing our paper (currently under review):

```bibtex
@misc{xi2026masp,
  title={A Requirement-Driven Approach for Multi-Agent Service Pattern Recommendation},
  author={Xi, Meng and Zhang, Zihao and Jin, Yechen and Cheng, Guanjie and Guan, Hao and Li, Ying and Pan, Xiaohua and Yin, Jianwei},
  year={2026},
  note={Under review}
}

```

*(Note: The citation format will be updated upon official publication.)*

## 📄 License

This dataset is licensed under the [MIT License](https://opensource.org/licenses/MIT).

