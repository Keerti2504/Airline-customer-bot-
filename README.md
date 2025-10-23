# Airline-customer-bot-

This project is an **intent classification chatbot** built using a fine-tuned **DistilBERT transformer model**.  
It provides an interactive **Streamlit UI** for chatting, collects **user feedback**, and automatically **re-trains** the model after accumulating enough confirmed interactions — all **without needing internet connectivity**.

---

## 🚀 Features

- 🗣️ **Intent Recognition** using Hugging Face’s DistilBERT model  
- 💬 **Interactive Chat Interface** powered by Streamlit  
- 📈 **Automatic Feedback Capture** for model improvement  
- 🔁 **Auto-Retraining** after a configurable number of feedback samples  
- 🧱 **Fully Offline** — model, data, and retraining all work locally  
- 📁 **Modular Folder Structure** separating model, backend, and data  

---

## 📂 Project Structure
```bash
Airline_customer_bot/
│
├── distilbert_model/
│   ├── config.json
│   ├── model.safetensors
│   ├── tokenizer.json
│   ├── tokenizer_config.json
│   ├── special_tokens_map.json
│   └── vocab.txt
│
├── data/
│   ├── airline_intents_clean.csv
│   └── feedback.csv
│
├── backend/
│   └── _train_model.py
│
├── streamlit_app.py
├── requirements.txt
```

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/Keerti2504/Airline-customer-bot-.git
cd Airline-customer-bot-
```
### 2️⃣ Create and Activate a Virtual Environment
```bash
python -m venv env
env\Scripts\activate      # On Windows
```
### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```
### 4️⃣ Run the Application
```bash
streamlit run streamlit_app.py
```
### *Retraining script
Manual retraining can be triggered with:
```bash
python backend/_train_model.py

```
---

## 🧠 Workflow Overview

- User Query → The model predicts an intent (e.g., cancel_order).
- Confirmation → The chatbot asks the user to verify the predicted intent.
- Feedback Logging → Confirmed samples are appended to feedback.csv.
- Auto Retraining → Once the feedback count reaches a threshold (e.g.,1000),the model retrains automatically using both the base dataset and feedback data

---

## 🛠️ Tech Stack

- **Frontend & UI**: Streamlit (Python)
- **Backend & API**: Streamlit (Python)
- **NLP Model**: Hugging Face Transformers — DistilBERT
- **Machine Learning Framework**: PyTorch
- **Data Management**: Pandas (CSV-based for intents and feedback)
- **Model Retraining**: Hugging Face Trainer API
- **Environment & Dependencies**: Python 3.11+, `requirements.txt`
- **Version Control**: Git / GitHub

---

## 📝 Notes

- User interactions and feedback are stored locally in CSV files (`feedback.csv`) to allow for incremental retraining.
- Automatic retraining is triggered after a predefined number of feedback entries (configurable), ensuring the model evolves with user corrections.
- The **DistilBERT model file** (`model.safetensors`) is **not included** in this repository due to its large size.
- To run the application, you need to **download or generate the model** separately and place it in the `distilbert_model/` directory.
