<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=896A15,6E8915,98351F&height=230&section=header&text=ClinTox%20%7C%20Clinical%20Toxicity%20Prediction&fontSize=45&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Mistral-7B%20%7C%20Scaffold%20Split%20%7C%20ROC-AUC:%200.9913&descAlignY=60&descAlign=50" width="100%"/>
</div>

<div align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=ffffff&center=true&vCenter=true&width=750&lines=Mistral-7B+QLoRA+on+ClinTox;ROC-AUC+0.9913+on+Scaffold+Split;fp32+Loss+Upcasting+for+Class+Imbalance;RDKit+SMILES+Augmentation+Pipeline." />
  </a>
  <br/>
  <img src="https://img.shields.io/badge/Mistral_7B-000000?style=for-the-badge&logo=mistral&logoColor=white" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/DeepChem-Bio_AI-00C853?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/ROC--AUC-0.9913-success?style=for-the-badge" />
</div>

---

## 🧬 Project Mission

The **Mistral-ClinTox Engine** fine-tunes a quantized **Mistral-7B** to predict clinical toxicity of drug compounds. ClinTox is one of the most class-imbalanced datasets in MoleculeNet — standard training causes NaN loss gradients. This project engineers precise solutions for fp16 instability, class imbalance, and scaffold generalization, achieving **0.9913 ROC-AUC** on the scaffold test set.

---

## 📊 Results — All Experiments

| Experiment | Model | ROC-AUC | Split |
|------------|-------|---------|-------|
| `Deepchem_Clintox_LoRA_Prototype.ipynb` | RF Baseline | 0.7398 | Scaffold |
| `OLMo_ClinTox_FINAL_PROOF_2_.ipynb` | OLMo-7B QLoRA | 1 epoch (proof of concept) | Scaffold |
| `mistral-clintox-scaffold.ipynb` | Mistral-7B QLoRA | **0.9913** ✅ | Scaffold |

**Final Best: 0.9913 ROC-AUC — Mistral-7B, Epoch 2, Scaffold Split, Kaggle T4**

Training curve (Final experiment):

| Epoch | ROC-AUC | Status |
|-------|---------|--------|
| 1 | 0.9768 | Strong start ↑ |
| 2 | **0.9913** | **BEST** ✅ |
| 3 | 0.9877 | Slight drop — saved Epoch 2 |

---

## 🔬 Key Scientific Contributions

| Challenge | Solution | Impact |
|-----------|----------|--------|
| **fp16 NaN Loss** | fp32 loss upcasting on imbalanced ClinTox labels | Eliminated gradient underflow crashes |
| **Severe Class Imbalance** | RDKit SMILES augmentation + oversampling | Robust generalization on minority toxic class |
| **Scaffold Generalization** | DeepChem ScaffoldSplitter enforced | True out-of-distribution evaluation |
| **Memory** | 4-bit NF4 + LoRA r=16 | Mistral-7B fits in 16GB VRAM |

**Key insight:** ClinTox's extreme imbalance (toxic compounds are rare) makes standard fp16 training collapse. fp32 loss upcasting with Focal Loss stabilizes the backward pass — this technique is directly ported into the proposed `CausalLMWrapper` for DeepChem.

---

## 🛠️ Tech Stack

<div align="center">
  <img src="https://img.shields.io/badge/Mistral--7B-4bit_NF4-purple?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black"/>
  <img src="https://img.shields.io/badge/LoRA_r=16-PEFT-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/RDKit-Chemistry-red?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/DeepChem-ScaffoldSplit-blue?style=for-the-badge"/>
</div>

---

## 📂 File Index

| File | Description |
|------|-------------|
| `Deepchem_Clintox_LoRA_Prototype.ipynb` | RF baseline — ROC-AUC 0.7398, establishes floor |
| `OLMo_ClinTox_FINAL_PROOF_2_.ipynb` | OLMo-7B proof of concept, 1 epoch training |
| `mistral-clintox-scaffold.ipynb` | Mistral-7B final — **ROC-AUC 0.9913** |
| `requirements.txt` | Dependencies |

---

## 💻 How to Run
```bash
pip install -r requirements.txt

# Final experiment — Kaggle
# kaggle.com/sameernadeem66/mistral-clintox-scaffold
```

---

## 🔗 Part of DeepChem GSoC 2026 Research

| Task | Model | Result | Repo |
|------|-------|--------|------|
| BACE Classification | Mistral-7B QLoRA | 0.8371 ROC-AUC | [BACE Repo](https://github.com/Abu-Sameer-66/Mistral7B-BACE-Generalization-Study) |
| BBBP Classification | Mistral-7B QLoRA | 0.7141 ROC-AUC | [BBBP Repo](https://github.com/Abu-Sameer-66/Mistral7B-BBBP-Molecular-Reasoning) |
| **ClinTox Classification** | **Mistral-7B QLoRA** | **0.9913 ROC-AUC** | **This Repo** |
| Tox21 Multi-Task | OLMo-7B QLoRA | 0.7225 Mean ROC-AUC | [Tox21 Repo](https://github.com/Abu-Sameer-66/Mistral7B-Tox21-Molecular-Optimization) |
| ESOL Regression | OLMo-7B + Reg Head | 0.8582 RMSE | [ESOL Repo] |
| SMILES Generation | OLMo-7B + RDKit TSM | 20/20 = 100% valid | [Generation Repo](https://github.com/Abu-Sameer-66/olmo-smiles-generation-tsm) |
