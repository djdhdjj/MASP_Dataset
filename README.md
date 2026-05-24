
# MASP Dataset: Multi-Agent Service Pattern Recommendation

This repository contains the **MASP Dataset**, a comprehensive, large-scale benchmark designed for Multi-Agent Service Pattern (MASP) recommendation tasks. It bridges the semantic and structural gap between unstructured user requirements and complex collaborative workflows.

## 📊 Dataset Overview

The rapid development of service computing drives the widespread adoption of multi-agent systems. This dataset addresses the critical data scarcity challenge in MASP recommendation by providing high-quality mappings between complex structural workflows and constrained natural language user requirements.

- **Total Service Patterns:** 27,947
- **Requirement-Pattern Pairs:** 139,735
- **Covered Domains:**
  - 🛒 E-commerce (12,220 patterns / 61,100 queries)
  - 🏥 Healthcare (12,185 patterns / 60,925 queries)
  - 🏦 Finance (3,542 patterns / 17,710 queries)
- **Average Tasks per Pattern:** ~10 nodes

## 📂 Repository Structure

```text
MASP_Dataset/
├── E-commerce/          # JSON/XML files for E-commerce MASPs and queries
├── Finance/             # JSON/XML files for Finance MASPs and queries
├── Healthcare/          # JSON/XML files for Healthcare MASPs and queries
├── sample_data.json     # A quick preview of the dataset format
└── README.md

```

## 🛠️ Data Format

Each entry in the dataset maps a user requirement to a specific Multi-Agent Service Pattern (represented as a multi-role collaborative structure).


```json
{
  "pattern_id": "ECO_001",
  "domain": "E-commerce",
  "description": "A workflow for processing order refunds and inventory updates...",
  "user_query": "I need a fast and automated process to handle customer returns and restock items without manual delay.",
  "qos_constraints": {
    "time_optimized": true,
    "cost_optimized": false
  },
  "topology_graph": "..."
}

```

## 🚀 Usage

You can load this dataset using standard Python libraries such as `json` or `pandas`.

```python
import json

with open('E-commerce/data.json', 'r') as f:
    masp_ecommerce = json.load(f)
    print(f"Loaded {len(masp_ecommerce)} records.")

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

