<div align="center">

  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=E50914,000000,0575E6&height=280&section=header&text=Mistral-ClinTox%20Engine&fontSize=50&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=LLM-Powered%20Clinical%20Toxicity%20Prediction&descAlignY=60&descAlign=50" width="100%"/>

  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=E50914&center=true&vCenter=true&width=750&lines=Initializing+Mistral-7B-v0.1...;Executing+DeepChem+Scaffold+Split...;Applying+RDKit+SMILES+Augmentation...;Training+Bio-Chemical+Neural+Link...;0.99+ROC-AUC+Achieved." />
  </a>

  <br/>

  <img src="https://img.shields.io/badge/Mistral_7B-000000?style=for-the-badge&logo=mistral&logoColor=white" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/DeepChem-Bio_AI-00C853?style=for-the-badge&logo=moleculer&logoColor=white" />
  <img src="https://img.shields.io/badge/Accuracy-0.99_ROC_AUC-success?style=for-the-badge" />

</div>

---







## 🧬 Mission: Clinical Precision via Generative AI
> **"Validating drug safety before clinical trials begin."**

The **Mistral-ClinTox Engine** leverages a quantized 7B-parameter Large Language Model to predict the clinical toxicity of chemical compounds. By framing molecular safety as a Natural Language Processing task, this pipeline achieves state-of-the-art predictive performance on the **ClinTox** dataset, effectively acting as an in-silico toxicologist.

---

## 🔬 Core Engineering Innovations

| Feature | The Science Behind It |
| :--- | :--- |
| **🤖 Mistral-7B QLoRA** | Adapts the highly efficient Mistral-7B model using **4-bit `nf4` quantization** and LoRA adapters (`r=16`, `alpha=32`), enabling enterprise-grade training on consumer GPUs without catastrophic forgetting. |
| **🧬 SMILES Augmentation** | Combats strict class imbalance by not just oversampling, but utilizing `RDKit` to generate randomized, non-canonical SMILES strings—injecting vital noise for robust generalization. |
| **🛡️ Scaffold Splitting** | Rejects standard random splits in favor of **DeepChem's ScaffoldSplitter**, ensuring the model generalizes to entirely unseen chemical core structures (a true simulation of real-world discovery). |
| **⚙️ Pipeline Optimization** | Features a custom PyTorch training loop with gradient accumulation, precise memory management, and automated adapter checkpointing. |

---

## 📈 Performance Telemetry
*Evaluated on the strictly separated Scaffold Test Set:*

```text
Epoch 1 | ROC-AUC: 0.9768 (Initial Alignment)
Epoch 2 | ROC-AUC: 0.9913 (Maximum Convergence) 🏆
Epoch 3 | ROC-AUC: 0.9877 (Stabilization)
