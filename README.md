# MASP Dataset: Multi-Agent Service Pattern Recommendation

This repository provides the documentation and download instructions for the **MASP Dataset**, a comprehensive, large-scale benchmark designed for Multi-Agent Service Pattern (MASP) recommendation tasks. It bridges the semantic and structural gap between unstructured user requirements and complex collaborative workflows.

## 📥 Download and Extraction

Due to its large scale, the complete dataset is compressed as a `.tar.gz` file and hosted on Baidu Netdisk.

- **Baidu Netdisk Link:** https://pan.baidu.com/s/1rLvLVCXLG6H1wHzsMJHwsw 
- **Access Code:** 3ywi

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

Once extracted, the `MASP` dataset directory follows a hierarchical structure categorized by domain. Each pattern instance is stored in a numbered subfolder containing its metadata and topological structure:

```text
MASP/
├── ecommerce/             # MASPs and requirements for the E-commerce domain
│   ├── 0/
│   │   ├── meta.json      # Metadata containing user requirements and QoS constraints
│   │   └── pattern.bpmn   # Multi-agent collaborative topology in BPMN format
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

Each entry consists of two files:

**1. `meta.json`**: Contains the semantic details, mapping a set of user requirements to the specific service pattern.

```json
{
  "Pattern_ID": 2,
  "Pattern_Category": "Apparel, Shoes & Bags",
  "Pattern_Title": "Slip-On Mules",
  "Pattern_Scenario": "user bought slip-on mules on an e-commerce platform , but the tracking hasn't updated for days, so user initiated a shipping complaint.",
  "Augment_Scenario": "cost_optimized",
  "user_requirements": [
    {
      "persona": "Variant-Trigger Persona (e.g., Patient / Low-Urgency Buyer)",
      "requirement": "Hey, I noticed my slip-on mules haven’t arrived yet and the tracking seems frozen. Not a huge rush—I’m just curious if you can look into it whenever you get a chance."
    },
    {
      "persona": "Variant-Trigger Persona (e.g., Passive / Non-Demanding Customer)",
      "requirement": "Hi, my order might be delayed—the tracking hasn’t changed in a few days. I don’t have any special deadlines, so feel free to handle this through your normal process."
    }
  ],
  "Pattern_Description": "A standard e-commerce service pattern."
}

```

*(Note: If your actual JSON keys use `"query"` instead of `"requirement"`, make sure to adjust your parsing scripts accordingly, though the conceptual terminology remains "requirement".)*

**2. `pattern.bpmn`**: An XML-based Business Process Model and Notation (BPMN) file that formally defines the multi-role collaborative structure, execution nodes, and information flows for the MASP.

## 🚀 Usage

You can load and parse this dataset using standard Python libraries such as `json` and `os`.

```python
import os
import json

# Define the path to your extracted dataset
DATASET_ROOT = "/home/zzh/Service_Pattern_Rec/pattern_dataset/MASP"

# Example: Load metadata for an E-commerce pattern
sample_meta_path = os.path.join(DATASET_ROOT, "ecommerce", "0", "meta.json")

if os.path.exists(sample_meta_path):
    with open(sample_meta_path, 'r', encoding='utf-8') as f:
        meta_data = json.load(f)
        print(f"Title: {meta_data.get('Pattern_Title')}")
        # Print the first user requirement
        if 'user_requirements' in meta_data and len(meta_data['user_requirements']) > 0:
            # Adjust the key below if your actual JSON uses 'query'
            print(f"Requirement: {meta_data['user_requirements'][0].get('requirement', '')}")
else:
    print("Dataset not found. Please ensure it is downloaded and extracted correctly.")

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

This dataset is licensed under the [MIT License](https://www.google.com/search?q=LICENSE) (or specify your preferred license, e.g., CC-BY-4.0).
