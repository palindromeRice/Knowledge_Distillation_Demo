# 🧠 T5 Knowledge Distillation for Summarization

This project demonstrates how to perform knowledge distillation from a fine‐tuned **T5‑Base** model to a lightweight **T5‑Small** model using the [News Summary Dataset](https://www.kaggle.com/datasets/sunnysai12345/news-summary).

---

## 📘 Project Overview

This notebook shows how to:

1. **Distill** a fine‑tuned T5‑Base teacher into a T5‑Small student using KL Divergence and Cross‑Entropy  
2. **Evaluate** both models using **ROUGE** and **BERTScore**  
3. Report **knowledge retention** by comparing student scores relative to teacher scores  

> ✅ Our goal is not to maximize absolute performance but to observe **knowledge retention** through distillation.

---

## 🧠 Model Setup & Important Notes

- **Teacher model**: `mrm8488/t5-base-finetuned-summarize-news` — already **fine‑tuned** on this news summarization task (we did **not** fine‑tune it ourselves).  
- **Student model**: `google-t5/t5-small` — used **without** additional fine‑tuning.  
- This configuration follows the [PyTorch Torchtune KD tutorial](https://pytorch.org/torchtune/0.3/tutorials/llama_kd_tutorial.html), which shows that transferring knowledge from a specialized teacher into a non‑fine‑tuned student best highlights the effect of distillation.  
- ⚠️ Teacher performance (ROUGE, BERTScore) depends entirely on the original fine‑tuning quality by the model uploader.

---

## 📥 Dataset

We use the **News Summary Dataset** from Kaggle, downloaded via `kagglehub`:

- `news_summary.csv` — main file with `text` (article) and `ctext` (summary) columns. Used for both distillation and evaluation.  
- `news_summary_more.csv` — additional raw articles (not used directly in this notebook).

---

## 📂 Repository Contents

- `KD.ipynb` — Colab‑compatible notebook containing:  
  - Dataset download & exploration  
  - Knowledge distillation training loop  
  - Evaluation (ROUGE, BERTScore, retention)  

---

## 🚀 How to Use

Run all cells in order:

1. **Download dataset** via `kagglehub`  
2. **Load & filter data**  
3. **Distill** T5‑Base → T5‑Small  
4. **Evaluate** models and compute retention  

---

## 📊 Metrics Used

- **ROUGE‑1, ROUGE‑2, ROUGE‑L** — n‑gram overlap with reference summaries  
- **BERTScore (F1)** using `roberta-large` — semantic similarity  
- **Retention (%)** = (student_score / teacher_score) × 100

---

## ⚠️ Notebook Rendering on GitHub

The Jupyter notebook in this repository currently **won’t render properly** on GitHub due to a known issue (“state” key missing in `metadata.widgets`). For details, see [GitHub Discussion #155944](https://github.com/orgs/community/discussions/155944).

📥 **Workaround:** Download the notebook (`KD.ipynb`) and open it locally in Jupyter or Google Colab to view all cells and outputs correctly.


