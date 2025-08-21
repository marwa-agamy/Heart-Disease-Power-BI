# 🫀 Heart Disease  Dashboard 

## 📌 Overview
This project is a **Power BI interactive dashboard** for analyzing a **Heart Disease clinical dataset**, providing insights into the impact of medical, lifestyle, and demographic factors on patient survival and risk of heart failure.  
---

## 📂 Dataset
The analysis uses **Heart_Disease_Dataset.xlsx** containing:

- **299 patient records**
- **14 clinical and demographic attributes**
- Survival outcomes based on **DEATH_EVENT**

### Key Data Dimensions:
- **Demographics**: Age, Sex, Smoking  
- **Medical History**: Anaemia, Diabetes, High Blood Pressure  
- **Clinical Tests**: Platelets, Serum Creatinine, Serum Sodium, Creatinine Phosphokinase, Ejection Fraction  
- **Outcome**: Survival vs. Death  

---

## 🔄 Data Conversion (0/1 to Categorical)
To make the dataset more **readable in Power BI**, binary columns were converted:

| Column              | 0 means        | 1 means            |
|---------------------|----------------|--------------------|
| anaemia             | No anaemia     | Has anaemia        |
| diabetes            | No diabetes    | Has diabetes       |
| high_blood_pressure | Normal BP      | High blood pressure|
| sex                 | Female         | Male               |
| smoking             | Non-smoker     | Smoker             |
| DEATH_EVENT         | Survived       | Died               |

---

## 🛠️ Features

### 📊 Interactive Dashboards
- **Patient Survival Overview** – KPIs for death vs survival  
- **Demographics Analysis** – Survival by age group, gender, smoking habits  
- **Medical Conditions** – Impact of diabetes, anaemia, blood pressure on survival  
- **Clinical Measures** – Relationship between creatinine, sodium, platelets, ejection fraction and outcomes  

### 📈 Key Visualizations
- Survival distribution (Survived vs Died)  
- Age group analysis with DEATH_EVENT  
- Medical history vs survival heatmaps  
- Clinical test indicators vs DEATH_EVENT  
- Dynamic filters for age, sex, and conditions  

---

## 🔧 Technical Implementation

### 🔄 Transformations
- Converted binary values (0/1 → categorical labels)  
- Grouped **Age into ranges** (30–39, 40–49, etc.)  
- Standardized clinical test data types  

### 📐 DAX Measures
```DAX
Total Patients = COUNTROWS(Heart_Disease_Dataset)
Total Death = CALCULATE(COUNTROWS(Heart_Disease_Dataset), Heart_Disease_Dataset[DEATH_EVENT] = "Died")
Total Survival = CALCULATE(COUNTROWS(Heart_Disease_Dataset), Heart_Disease_Dataset[DEATH_EVENT] = "Survived")
Death Rate % = DIVIDE([Deaths], [Patients], 0)
Survival Rate % = DIVIDE([Survivors], [Patients], 0)
