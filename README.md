# medimind_chatbot
#  MediMind: AI-Powered Medical Diagnosis and Clinical Decision Support

**MediMind** is an AI-driven healthcare chatbot that assists clinicians by predicting possible diseases based on patient symptoms and history, and offering structured clinical decision support. It uses DistilBERT for disease classification and provides human-readable summaries with exportable patient history.

---

##  Features

-  Disease prediction using fine-tuned DistilBERT model.
-  Intelligent clinical decision support based on predicted disease.
-  Unified patient input (symptoms, history, test results, query).
-  Differentiates model vs. LLM-based answers (e.g., for open-ended queries).
-  Patient record storage in CSV and JSONL.
-  Gender-aware and age-specific diagnosis formatting.
-  Human-readable outputs for physician review.
-  History search and export to PDF/CSV.
-  Runs via a Gradio Web UI.

---

##  Example Use Case

###  Example 1: Emergency Department – Suspected Cardiac Event

**Context**: A 52-year-old male presents with chest pain in the emergency department.

**Input**:
- **Symptoms**: Chest pain for 2 hours, heavy, radiating to left arm; nausea, sweating, shortness of breath.
- **Medical History**: Hypertension, smokes 1 pack/day for 20 years.
- **Test Results**: ECG shows ST-segment elevation; troponin I elevated at 2.5 ng/mL.
- **Physician Query**: “What’s the likely diagnosis, and what should we do next?”

**Output**:
- **Symptom Analysis**:
  - Acute myocardial infarction (STEMI): 92%
  - Unstable angina: 5%
  - Aortic dissection: 2%
  - Pulmonary embolism: 1%
  - **Alert**: Immediate cardiology consult recommended.

- **Clinical Decision Support**:
  - **Immediate Actions**:
    - Aspirin 325 mg (chewable) stat.
    - Heparin bolus and infusion.
    - Prepare for PCI within 90 minutes.
  - **Follow-Ups**:
    - Repeat ECG in 30 minutes.
    - Monitor troponin every 6 hours.
  - **Documentation**: STEMI diagnosed; aspirin and heparin initiated; PCI planned.

---

##  How It Works

1. **Model Training**:
   - Fine-tuned DistilBERT model on symptoms to classify diseases.
   - Uses tokenizer + TensorFlow model + label encoder.

2. **Clinical Reasoning**:
   - Rule-based support for common diseases (e.g., diabetes, cardiac).
   - Outputs structured JSON used for readable formatting.

3. **UI**:
   - Built with **Gradio** for easy input/output interaction.
   - Supports both full symptom-based queries and open-ended questions.

---

##  Project Structure
├── medimind_india_raw_data.csv # Dataset
├── model/ # Trained model and tokenizer
│ ├── model_weights.h5
│ └── label_encoder.pkl
├── patient_records.csv # CSV record of patient queries
├── patient_records.jsonl # JSONL log for advanced audit
├── app.py # Main Gradio app
├── train_model.py # Model training code
├── utils.py # Helper functions for formatting and logic

## Key Dependencies:
transformers==4.36.2
tensorflow==2.15.0
pandas==2.1.4
scikit-learn==1.3.2
gradio
joblib

