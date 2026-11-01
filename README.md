<h1 align="center">🩺 Medical Transcription Data Extraction with OpenAI</h1>

<p align="center">
  Turning free-text medical transcriptions into structured data (patient age, recommended treatment and ICD codes) with GPT-4o function calling
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-Data%20Processing-150458?logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/OpenAI-GPT--4o-412991?logo=openai&logoColor=white" alt="OpenAI">
  <img src="https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white" alt="Colab">
</p>

## 📌 Overview

This project reads medical transcriptions from a CSV file and uses the **OpenAI API (GPT-4o)** to pull out structured information from each note. For every transcription it extracts the patient's **age** and the **recommended treatment or procedure**, then asks the model for the matching **ICD codes**. The results are collected into a pandas DataFrame alongside each note's medical specialty.

---

## ⚡ At a Glance

| 📄 Sample Notes | 🏥 Specialties | 🤖 Model | 📦 Output Fields |
|:---:|:---:|:---:|:---:|
| **5** | **5** | **GPT-4o** | **4** |

---

## 🔄 Workflow

1. **Load & Inspect** – Read the CSV and reviewed its columns and the first rows (`head()`, `value_counts()`).
2. **Set Up the API** – Loaded the API key from a `.env` file with `python-dotenv` and created the OpenAI client.
3. **Extract Age & Treatment** – Sent each transcription to GPT-4o with a function definition (`extract_medical_data`) so the reply comes back as structured JSON. Missing values are returned as `Unknown`.
4. **Look Up ICD Codes** – Sent each recommended treatment to GPT-4o in a second call (temperature 0.3) and asked for a list of codes only. Treatments marked `Unknown` are skipped.
5. **Build the Table** – Added each note's medical specialty and ICD code to the extracted data and converted the list of results into a DataFrame (`df_structured`).

> **Input columns:** `index` · `medical_specialty` · `transcription`
>
> **Output columns:** `Age` · `Recommended Treatment/Procedure` · `Medical Specialty` · `ICD Code`

---

## 🧾 Sample Data

| Index | Medical Specialty | Note Type |
|:---:|---|---|
| 0 | Allergy / Immunology | Clinic visit for allergic rhinitis |
| 1 | Orthopedic | Consultation for an Achilles tendon rupture |
| 2 | Bariatrics | Laparoscopic Roux-en-Y gastric bypass operative report |
| 3 | Cardiovascular / Pulmonary | Tracheostomy and stent removal operative report |
| 4 | Urology | Follow-up for urinary retention after kidney transplant |

---

## 🧩 How the Extraction Works

| Step | Function | What it does |
|---|---|---|
| 1 | `extract_info_with_openai(transcription)` | Calls GPT-4o with a function definition and returns `Age` and `Recommended Treatment/Procedure` as a dictionary |
| 2 | `get_icd_codes(treatment)` | Asks GPT-4o for the ICD codes of a treatment and returns them as text, or `Unknown` |
| 3 | Loop over `df.iterrows()` | Runs both functions on every row and stores the combined result |

## 👩‍💻 Author

**Marwa Samy** · [GitHub](https://github.com/marwa23-rgb)
