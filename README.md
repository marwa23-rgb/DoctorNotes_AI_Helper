# DoctorNotes_AI_Helper  
**Automated Clinical Data Extraction from Medical Transcriptions**

## Overview  
This project streamlines medical documentation by leveraging artificial intelligence to convert **unstructured clinical narratives** into **structured, actionable data**. Using the **OpenAI API** and **Python-based NLP techniques**, the system extracts essential information—such as **symptoms, diagnoses, and treatments**—from natural language transcripts recorded during patient encounters.

## Problem Statement  
Manual extraction of medical information is:
- **Time-consuming**
- **Error-prone**
- Especially challenging for administrative and insurance documentation (e.g., ICD-10 coding)

## Solution  
To address this, the project implements an **automated pipeline** that:
- Extracts relevant clinical data from free-text transcriptions
- Cleans and processes text using **NLP techniques**
- Identifies clinical entities using **regex and pattern matching**
- Maps diagnoses to **ICD-10 codes**, the international standard for disease classification and billing

## Technologies Used  
-  **OpenAI API** – for language understanding and information extraction  
-  **Python** – for scripting and system integration  
-  **Natural Language Processing (NLP)** – for text cleaning, tokenization, and analysis  
-  **Regular Expressions (Regex)** – for entity recognition and pattern matching  
-  **ICD-10 Standards** – for classification and code assignment
