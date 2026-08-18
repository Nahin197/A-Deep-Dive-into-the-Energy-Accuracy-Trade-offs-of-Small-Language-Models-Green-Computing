# ⚡ A Deep Dive into the Energy-Accuracy Trade-offs of Small Language Models

> An empirical benchmarking study of **17 Small Language Models (SLMs)** — from 270M to 7B parameters — measuring performance accuracy **and** real-world energy/carbon footprint on three core NLP tasks.

---

## 📄 Abstract

This research presents a comprehensive empirical evaluation of 17 SLMs on three fundamental NLP tasks:

- 🎭 **Sentiment Analysis** (IMDB Movie Reviews)
- 📰 **News Classification** (AG News)
- 🚫 **Offensive Language Detection** (OLID)

Using **CodeCarbon** inside a reproducible **Google Colab** environment, we measure energy usage (kWh), CO₂ emissions (kg), and computational efficiency alongside standard performance metrics (Accuracy, F1-score).

**Key finding:** Parameter count is a poor proxy for either performance or efficiency. StableLM-Zephyr-3B achieved **94.9% accuracy on sentiment analysis** consuming only `5.69×10⁻³ kWh` — **10× less energy** than comparable 7B models.

---

## 👥 Authors

| Name | Student ID | Institution |
|---|---|---|
| Md. Khademul Islam Nahin | 011221282 | United International University, Dhaka |
| Shekh Rifat Islam | 011213036 | United International University, Dhaka |
| Mahi Hoque | 011221283 | United International University, Dhaka |
| Md. Shoaib Siddiqi Shaon | 011213164 | United International University, Dhaka |
| Arshad Md. Adel | 011221299 | United International University, Dhaka |

**Department:** Computer Science & Engineering (CSE)

---

## 🗂️ Repository Structure

```
 📁 Models/                      # Jupyter notebooks for each model
    ├── Falcon3_3B_Instruct.ipynb
    ├── LLaMA_3_2_1B.ipynb
    ├── Phi4mini.ipynb
    ├── Qwen2.5-0.5B.ipynb
    ├── QwenQwen3-4B.ipynb
    ├── TinyLlama_1_1B_intermediate_step_1431k_3T-Base_Model.ipynb
    ├── TinyLlama_TinyLlama_1_1B_Chat_v1_0.ipynb
    ├── btlm_3b_8k_base.ipynb
    ├── falcon_7b.ipynb
    ├── gemma-2-2b.ipynb
    ├── google_gemma_2_2b_it.ipynb
    ├── google_gemma_3_1b_it.ipynb
    ├── google_gemma_3_270m_it_Fine_Tune_model.ipynb
    ├── google_gemma_3_4b_it.ipynb
    ├── mistralaiMistral_7B_v0_1.ipynb
    ├── zephyr_3b.ipynb
    └── zephyr_7b_beta.ipynb
```

---

## 🤖 Models Evaluated

| Model | Organization | Parameters | Category |
|---|---|---|---|
| Gemma-3-270M | Google | 270M | ≤ 1B |
| Qwen2.5-0.5B | Alibaba | 500M | ≤ 1B |
| LLaMA-3.2-1B | Meta | 1B | ≤ 1B |
| TinyLlama-1.1B (Base) | TinyLlama Team | 1.1B | ≤ 1B |
| TinyLlama-1.1B (Chat) | TinyLlama Team | 1.1B | ≤ 1B |
| Gemma-2-2B | Google | 2B | 1B–3B |
| Gemma-2-2B-IT | Google | 2B | 1B–3B |
| Gemma-3-1B-IT | Google | 1B | 1B–3B |
| BTLM-3B | Cerebras | 3B | 1B–3B |
| StableLM-Zephyr-3B ⭐ | Stability AI | 3B | 1B–3B |
| Falcon3-3B-Instruct | TII | 3B | 1B–3B |
| Phi-4-Mini | Microsoft | 3.8B | 3B–8B |
| Gemma-3-4B-IT | Google | 4B | 3B–8B |
| Qwen3-4B | Alibaba | 4B | 3B–8B |
| Falcon-7B | TII | 7B | 3B–8B |
| Mistral-7B-v0.1 | Mistral AI | 7B | 3B–8B |
| StableLM-Zephyr-7B | Stability AI | 7B | 3B–8B |

---

## 🧪 Methodology

All experiments were conducted in a **controlled, reproducible Google Colab environment**:

1. **Task Selection** — Three NLP tasks of increasing linguistic complexity
2. **Data Collection** — Publicly available Hugging Face datasets
3. **Model Selection** — 17 diverse SLMs (270M → 7B parameters)
4. **Evaluation** — Performance (Accuracy, F1) + Energy (CodeCarbon tracker)

### Datasets

| Task | Dataset | Instances | Type |
|---|---|---|---|
| Sentiment Analysis | IMDB Movie Reviews | 50,000 | Binary Classification |
| News Classification | AG News | 120,000 | Multi-class Classification |
| Offensive Language Detection | OLID | 14,100 | Hate Speech Detection |

---

## 📊 Key Results

### 🎭 Sentiment Analysis (IMDB)

| Rank | Model | Accuracy | F1 | Energy (kWh) | CO₂ (kg) |
|---|---|---|---|---|---|
| 🥇 | StableLM-Zephyr-3B | **94.9%** | 0.947 | 0.005688 | 0.001991 |
| 🥈 | Qwen3-4B | 94.6% | 0.944 | 0.017439 | 0.006104 |
| 🥉 | Phi-4-Mini | 93.3% | 0.929 | 0.008171 | 0.002860 |
| ⚡ Most Efficient | Qwen2.5-0.5B | 90.1% | 0.901 | **0.003245** | **0.001136** |

### 📰 News Classification (AG News)

| Rank | Model | Accuracy | F1 | Energy (kWh) |
|---|---|---|---|---|
| 🥇 | Qwen3-4B | **83.0%** | 0.827 | 0.017439 |
| 🥈 | Falcon3-3B-Instruct | 81.7% | 0.816 | 0.008351 |
| 🥉 | StableLM-Zephyr-7B | 80.0% | 0.797 | 0.056217 |

### 🚫 Offensive Language Detection (OLID)

| Rank | Model | Accuracy | F1 | Energy (kWh) |
|---|---|---|---|---|
| 🥇 | Qwen3-4B | **74.5%** | 0.763 | 0.017439 |
| 🥈 | Gemma-3-1B-IT | 72.8% | 0.769 | **0.007512** |
| 🥉 | Phi-4-Mini | 72.3% | 0.684 | 0.008171 |

---

## 💡 Key Findings

### 1. 🔄 Parameter Size Paradox
> Larger models ≠ better performance. **Mistral-7B** (7B params) underperformed **StableLM-Zephyr-3B** (3B params) on **every single task**.

### 2. ⚡ Energy Efficiency Champions
> The smallest models (**Qwen2.5-0.5B**, **LLaMA-3.2-1B**) consumed **10–15× less energy** than 7B models while delivering competitive performance on simpler tasks.

### 3. 🎯 Task-Specific Performance
> Model rankings shift dramatically by task. Falcon3-3B-Instruct scored 87% on sentiment analysis but **completely failed** offensive language detection (50% accuracy, F1 = 0).

### 4. 🌍 18× Sustainability Impact
> Running 1M inferences with **Qwen2.5-0.5B** vs **Mistral-7B**:
> - Energy: `3.245 kWh` vs `57.737 kWh` → **17.8× less**
> - CO₂: `1.136 kg` vs `20.208 kg` → **17.8× less**

---

## ✅ Practical Recommendations

| Use Case | Recommended Model | Reason |
|---|---|---|
| 🏭 High-throughput production | **Qwen2.5-0.5B** | Lowest energy, solid accuracy on simple tasks |
| ⚖️ Balanced performance/efficiency | **StableLM-Zephyr-3B** | Best overall energy-accuracy tradeoff |
| 🧠 Deep linguistic understanding | **Qwen3-4B** or **Gemma-3-1B-IT** | Best on complex tasks like offensive language detection |
| ❌ Avoid for most NLP tasks | 7B models (Mistral, Zephyr-7B, Falcon-7B) | High energy cost with little accuracy benefit |

---

## 🔬 Limitations

- Experiments confined to **Google Colab** (single hardware setup)
- Only **3 NLP task types** covered (no MT, QA, code generation, multimodal)
- **Zero-shot / few-shot evaluation** only — no task-specific fine-tuning
- Energy measured at **run-level granularity** (not per-token or per-layer)
- 17 models evaluated; newer MoE / SSM architectures not included

---

## 🚀 Future Work

- 🌐 **Multi-lingual and cross-lingual** energy-accuracy analysis
- 🔧 **Fine-tuning energy costs** (full lifecycle analysis)
- 💻 **Hardware diversity** (edge TPUs, mobile GPUs, different generations)
- 🔀 **Dynamic model selection** based on input complexity
- 🌱 **Carbon-aware scheduling** with renewable energy sources
- 📏 **Larger benchmarks** (GLUE, SuperGLUE, domain-specific tasks)
- ✂️ **Quantization and compression** effects on energy-accuracy Pareto frontier

---

## 📦 Requirements

Each notebook in the `Models/` directory is self-contained and runs on **Google Colab** (free tier). Required packages are installed within each notebook:

```python
pip install transformers datasets codecarbon torch accelerate
```

---

## 🔗 Source Code

Full implementation available on Google Drive:  
👉 [https://drive.google.com/drive/folders/1Wm4vILtWJkHI7i1XP_7VKF3wpNFUfL4X](https://drive.google.com/drive/folders/1Wm4vILtWJkHI7i1XP_7VKF3wpNFUfL4X)

---

## 📚 References

| Citation | Paper |
|---|---|
| Strubell et al. (2019) | Energy and Policy Considerations for Deep Learning in NLP |
| Henderson et al. (2020) | Towards the Systematic Reporting of Energy and Carbon Footprints of ML |
| Barros et al. (2025) | Small is Sufficient: Reducing World AI Energy Consumption Through Model Selection |
| Jeanquartier et al. (2026) | Assessing the Carbon Footprint of Language Models |
| Ashraf et al. (2025) | Toward Green Code: Prompting SLMs for Energy-Efficient Code Generation |
| Sun et al. (2020) | MobileBERT: A Compact Task-Agnostic BERT for Resource-Limited Devices |
| Samsi et al. (2023) | From Words to Watts: Benchmarking Energy Costs of LLM Inference |
| Ji and Jiang (2026) | A Systematic Review of Electricity Demand for LLMs |
| Ashraf et al. (2025b) | Energy-Aware Code Generation: Benchmarking SLMs vs LLMs |
| Sanh et al. (2019) | DistilBERT: Smaller, Faster, Cheaper and Lighter |

---

## 🏷️ Keywords

`Small Language Models` · `Energy Efficiency` · `Green Computing` · `Sustainable AI` · `Carbon Emissions` · `NLP Benchmarking` · `Model Selection` · `Environmental Impact` · `CodeCarbon` · `Google Colab`

---

## 📜 License

This project is an academic research paper submitted for IEEE conference publication. 

---

<div align="center">
  <b>🌱 Building a more sustainable AI, one inference at a time.</b>
  <br/>
  <i>United International University — Department of CSE, Dhaka, Bangladesh</i>
</div>
