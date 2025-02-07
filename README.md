# Drug Interaction Checker with Personalized Risk Assessment

### 📌 Overview
The Enhanced Drug Interaction Checker is an AI-powered tool designed to analyze drug interactions while integrating user-specific health conditions for personalized risk assessment. Unlike traditional drug interaction checkers that rely solely on static databases, our approach considers user-reported health conditions and real-world hospital data to provide more accurate and dynamic risk classification.

### 🔹 Key Features
✅ Extracts drug data from DailyMed (SPL XML files).

✅ Converts XML files to JSON for structured analysis.

✅ Performs drug interaction analysis using advanced ML models.

✅ User-specific risk assessment based on self-reported conditions (e.g., hypertension, diabetes).

✅ Uses MIMIC-III dataset (from Kaggle) to refine interaction risk classification.

✅ Automated severity classification based on active ingredients and health factors.

### 📌 Data Sources & Accessibility
We use multiple publicly available datasets for drug interaction analysis and risk assessment.

Dataset	Source	Accessibility
DailyMed (SPL Data)	DailyMed	✅ Publicly Available (No Restrictions)

SIDER (Side Effects Data)	SIDER Database	✅ Publicly Available (No Restrictions)

MIMIC-III (Kaggle Version)	Kaggle	✅ Publicly Available (No Restrictions)

User-Reported Health Data	Collected via user input	✅ No Restrictions

⚠ Note: The MIMIC-III dataset was obtained from Kaggle instead of PhysioNet, meaning it does not require special access or approval.

### 📌 Project Workflow
1️⃣ Extracting Drug Data from DailyMed
Script: XML_Extract.py
Function: Extracts XML files from compressed DailyMed archives.
Output: XML files saved in the extracted_xmls directory.

2️⃣ Converting XML to JSON
Script: XML-Json.py
Function: Converts SPL XML files into structured JSON format.
Output: A JSON file containing drug interactions, warnings, and dosage information.

3️⃣ Drug Interaction Analysis
Script: Drug-Interaction.py
Function:
Identifies drug-drug interactions based on active ingredients.
Uses Facebook’s BART model to generate natural language summaries of risks.
Flags potential adverse reactions based on predefined interaction rules.

4️⃣ User-Specific Risk Assessment
Script: Personalized-Risk.py
Function:
Accepts user input for pre-existing conditions (e.g., hypertension, diabetes).
Classifies interaction severity based on reported health conditions.
Uses ML models trained on MIMIC-III data to refine predictions dynamically.

Example Input:

json
Copy
Edit
{
  "user_conditions": ["hypertension", "diabetes"],
  "current_medications": ["Metformin", "Lisinopril"],
  "new_drug": "Ibuprofen"
}
Example Output:

json
Copy
Edit
{
  "risk_level": "High",
  "summary": "Ibuprofen may reduce the effectiveness of Lisinopril and increase the risk of kidney damage in patients with hypertension."
}

### 📌 Why JSON Instead of XML?
✅ Efficiency → JSON files allow faster access and processing in ML pipelines.

✅ Scalability → Structured JSON enables integration with external APIs.

✅ Better NLP Processing → JSON simplifies text-based interaction summarization.

### 📌 How to Use the System
1️⃣ Run XML_Extract.py
Extracts XML files from DailyMed’s SPL archives.

2️⃣ Run XML-Json.py
Converts the extracted XML files into a structured JSON database.

3️⃣ Run Drug-Interaction.py
🚀 Detects drug interactions using structured JSON data.
🚀 Generates BART-based NLP summaries of potential risks.

4️⃣ Run Personalized-Risk.py
🚀 Accepts user-reported conditions (e.g., diabetes, heart disease).
🚀 Uses MIMIC-III data to improve severity predictions (if available).
🚀 Outputs detailed interaction insights with personalized warnings.


### 📌 Final Thoughts
By combining drug interaction databases, machine learning, and real-world hospital data, this project moves toward AI-driven precision medicine. The goal is to make medication safety checks smarter, personalized, and accessible to all users.
