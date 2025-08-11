# ⚖️ Fine-Tuning ChatGPT with the Caselaw Access Project

This project explores fine-tuning a ChatGPT model using the **Caselaw Access Project (CAP)** dataset to classify legal case outcomes as "Favorable" or "Unfavorable." The goal is to test the feasibility, costs, and methodology of creating a domain-specific legal AI model.

---

## 📌 Objective
- Load and preprocess legal case texts from CAP.
- Assign binary outcome labels using a rule-based approach.
- Convert the labeled data into a format suitable for OpenAI fine-tuning.
- Evaluate practical constraints like dataset size, cost, and performance.

---

## 📊 Dataset Overview
- **Source**: [Caselaw Access Project on Hugging Face](https://huggingface.co/datasets/common-pile/caselaw_access_project)
- **File Used**: `cap_00000.jsonl.gz`
- **Size Loaded**: 40,000 rows
- **Key Variables**:
  - `text`: Full case narrative
  - `metadata`: Author and license info
- **Focus Field**: `text` column for decision outcome extraction

---

## 🛠 Methods
1. **Labeling**  
   - Classified cases as:
     - **Favorable**: Contained terms like "affirmed" + "appellee" or "reversed" + "appellant"
     - **Unfavorable**: Contained terms like "dismissed" + "appellant" or "reversed" + "appellee"
   - Dropped rows with insufficient context.
   - Result: 30,560 labeled examples from 40,000 rows.

2. **Subsampling for Cost Control**  
   - Reduced dataset to:
     - **Training**: 200 examples
     - **Validation**: 50 examples
   - Reduced size to avoid exceeding fine-tuning cost limits.

3. **Formatting for Fine-Tuning**  
   - Converted labeled data to JSONL with OpenAI-compatible `messages` structure:
     - System: `"You're a chatbot that only responds with emojis!"`  
     - User: Truncated case text (≤500 chars)  
     - Assistant: Outcome label ("Favorable" or "Unfavorable")

---

## 📈 Analysis & Observations
- **Cost Constraint**: Initial fine-tuning run estimated at $104.30, exceeding budget; reduced sample size to fit $9.28 remaining quota.
- **Rule-Based Limitations**: Simple keyword search missed nuanced cases (e.g., mixed rulings, procedural dismissals).
- **Training Output**: Prepared small-scale test files (`train.jsonl` and `valid.jsonl`) for model fine-tuning.

---

## 🏆 Key Findings
1. Large legal datasets can quickly exceed fine-tuning budgets.
2. Rule-based labeling works for proof-of-concept but lacks nuance.
3. Smaller datasets can be used to validate the pipeline before scaling up.

---

## 💡 Recommendations
- Implement **NLP parsing** or **LLM-assisted labeling** for more accurate outcome classification.
- Use **active learning** to iteratively improve labels.
- Fine-tune with a **larger budget** and **balanced dataset** for real deployment.
- Consider embeddings-based retrieval before fine-tuning for cost efficiency.

---

## ⚖️ Ethical Considerations
- Legal text is public domain but must be handled responsibly to avoid bias amplification.
- Classification should **not be used for legal advice**; intended for research/educational purposes only.
- Transparency in labeling criteria is critical to prevent misinterpretation.

---

## 📚 References
- Caselaw Access Project – https://case.law/
- OpenAI Fine-Tuning Documentation – https://platform.openai.com/docs/guides/fine-tuning
- Hugging Face Datasets – https://huggingface.co/datasets
