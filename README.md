# Understanding Power Transform on Concrete Dataset  
**🧠 AI-Generated README (custom prompt used for clarity and learning ease)**  

---

## 📘 Overview  
This notebook demonstrates how **Power Transformation** helps improve model performance by making data more normally distributed.  
The experiment is conducted on the **Concrete Strength dataset** available in the repository.  

---

## 🧩 Steps and Implementation  

### 1. Library Imports  
All required libraries such as `numpy`, `pandas`, `matplotlib.pyplot`, `seaborn`, `sklearn.preprocessing`, and `sklearn.linear_model` were imported.

---

### 2. Dataset Loading & Initial Check  
- The dataset was loaded from the repo.  
- Verified **no null values** were present.  
- Found several **zero values**, making **log transformation unsuitable**, so **Power Transform** was chosen instead.

---

### 3. Baseline Model Performance  
A **Linear Regression (LR)** model was trained **without transformation**:  
- **R² Score (Train):** 0.62  
- **Cross Validation Mean Score:** 0.27  

This served as a baseline for comparison.

---

### 4. Standard Scaling  
Data was first **standardized** using `StandardScaler` to ensure each feature contributed equally before applying transformations.

---

### 5. Data Distribution Analysis  
Plotted **PDFs** and **QQ plots** for all features:  
- Observed that most columns were **not normally distributed**.  
- Some were **right-skewed**, others **left-skewed**, and a few were **peaked in the middle**.  
- Visualization images are attached at the bottom of the notebook.

---

### 6. Applying Power Transform  
Used `PowerTransformer(method='box-cox')` on all numeric columns:  
- Added **0.00001** to all values to make them **Box-Cox compatible** (since it requires positive values).  
- After transformation, distributions became **much closer to normal**.

**Results after Power Transform (Box-Cox):**  
- **R² Score (Train):** 0.80  
- **Cross Validation Mean Score:** 0.66  

---

### 7. Yeo-Johnson Transformation Comparison  
Also applied **Yeo-Johnson** (which supports zero and negative values):  
- Performed slightly lower but still improved the results.  
- **R² Score:** ~0.68  

---

### 8. Visualization  
- **Before and After** Power Transform plots for all columns are shown in the notebook.  
- A few visual samples are attached here to highlight distribution improvements.

---

## 🧠 Observations  
- Log Transform fails when dataset contains **zeros or negative values**.  
- **Power Transform** and **Yeo-Johnson** help achieve **near-normal distributions**.  
- Linear Regression accuracy improved **from 0.62 → 0.80**, and cross-validation from **0.27 → 0.66**.  
- Transformation benefits **linear models** more than tree-based models.

---

## 🧰 Tools Used  
- **Python Libraries:** pandas, numpy, matplotlib, seaborn  
- **Scikit-learn:** StandardScaler, PowerTransformer, LinearRegression, cross_val_score  
- **Dataset:** Concrete Strength (from repo)

---

## 📈 Key Results Summary  

| Transformation Type | R² (Train) | Cross Val Score | Notes |
|----------------------|-------------|------------------|-------|
| None (Raw Data) | 0.62 | 0.27 | Data highly skewed |
| Power Transform (Box-Cox) | 0.80 | 0.66 | Major improvement |
| Yeo-Johnson | 0.68 | 0.60 | Works with zero values |

---

## 🖼️ Attached Visuals  
1. Distributions before Power Transform  
2. Distributions after Power Transform  
3. QQ plots before and after (confirming normalization trend)
   <img width="1156" height="393" alt="pt1" src="https://github.com/user-attachments/assets/aa93e29e-61e9-452e-845a-463368cd7fcb" />
   <img width="1156" height="393" alt="pt2" src="https://github.com/user-attachments/assets/34937b56-8235-4706-a1ea-2c7dd48935a2" />
    <img width="1156" height="393" alt="pt3" src="https://github.com/user-attachments/assets/6eedf314-ebcd-42c5-8f38-dcd10ec99053" />
<img width="1156" height="393" alt="pt4" src="https://github.com/user-attachments/assets/ad54ed03-fb15-457f-9a59-0baa5a3a148e" />
<img width="1156" height="393" alt="pt5" src="https://github.com/user-attachments/assets/e35b8ee7-6369-46ae-814e-2b9190ddc9af" />
<img width="1156" height="393" alt="pt6" src="https://github.com/user-attachments/assets/5a621a2e-d295-41dc-a26d-d53377e6c5a1" />
<img width="1156" height="393" alt="pt7" src="https://github.com/user-attachments/assets/9fd15637-19a0-461d-939e-a101673be3bc" />
<img width="1156" height="393" alt="pt8" src="https://github.com/user-attachments/assets/334d3386-ac02-4925-92c1-8328695c97ad" />
<img width="1173" height="393" alt="pt9" src="https://github.com/user-attachments/assets/86c75e97-5f2e-482f-99f1-6b559e8e2dfc" />
<img width="1182" height="393" alt="pt10" src="https://github.com/user-attachments/assets/2dcf5422-4287-44df-b385-940dfc504c1a" />
<img width="1173" height="393" alt="pt11" src="https://github.com/user-attachments/assets/5958f67b-7bec-4bc9-8878-3f96bd61b237" />
<img width="1173" height="393" alt="pt12" src="https://github.com/user-attachments/assets/a8c7de91-e402-42f7-a8ac-49c2619d675a" />
<img width="1173" height="393" alt="ptt13" src="https://github.com/user-attachments/assets/4f051afb-70f1-4a4a-805b-fe541a3598c7" />
<img width="1173" height="393" alt="pt14" src="https://github.com/user-attachments/assets/5eb73658-d7ca-493b-a1eb-d33cb3d9ede1" />
<img width="1173" height="393" alt="pt15" src="https://github.com/user-attachments/assets/944f538c-baef-4894-8f70-8fb0b6027597" />
<img width="1165" height="393" alt="pt16" src="https://github.com/user-attachments/assets/6019f083-2265-424c-a00d-9f3d4d1b3143" />


### Final Comparison
<img width="1177" height="393" alt="pt-l" src="https://github.com/user-attachments/assets/4ed72bb1-122a-4be3-a217-6bb8fe51103b" />



---

## ✅ Conclusion  
Power Transformation significantly improves model performance by stabilizing variance and normalizing skewed data.  
For datasets with zeros or negatives, **Yeo-Johnson** is a practical alternative.

---

📎 *Note: This README was AI-generated using a custom prompt for educational clarity and to simplify conceptual understanding.*
