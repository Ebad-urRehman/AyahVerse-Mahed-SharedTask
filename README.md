# AyahVerse at MAHED Shared Task: Fine-Tuning ArabicBERT for Hope & Hate Detection

[![Paper](https://img.shields.io/badge/Paper-ArabicNLP%202025-blue)](https://sites.google.com/view/arabicnlp2025)
[![Conference](https://img.shields.io/badge/Accepted-EMNLP%20Workshop-green)](https://aclanthology.org/2025.arabicnlp-sharedtasks.92/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Official Implementation** of the paper presented at the **3rd ArabicNLP Workshop (co-located with EMNLP 2025)**.

## 📄 Abstract
This repository contains the system description and code for **AyahVerse**, our submission to the **MAHED Shared Task 2025 (Subtask 1)**. The task involves detecting **Hope**, **Hate**, or **Not Applicable** labels in Multi-dialect Arabic tweets.

We proposed two architectures:
1.  **Single Multiclass Classifier:** Fine-tuned ArabicBERT with class-weighted loss.
2.  **Stacked Binary Ensemble:** A two-stage architecture using binary classifiers (Hope vs. Neutral, Hate vs. Neutral) fed into a Logistic Regression meta-classifier.

Our best-performing configuration (Stacked Ensemble with Emoji Removal) achieved a **Macro-F1 score of 0.91** on the test set.

## 🚀 Key Features
* **Preprocessing Pipeline:** Custom Arabic text cleaning including tatweel removal, diacritic normalization, and **strategic emoji removal** (which significantly boosted F1 scores).
* **Models:** Utilizes `bert-base-arabic` (ArabicBERT) fine-tuned on the MAHED dataset.
* **Handling Imbalance:** Implemented class weighting and split-label strategies to handle the "Not Applicable" class dominance.

## 📊 Results
While our official submission achieved an F1 of 0.48 due to underfitting, our **post-submission improvements** (detailed in the paper) demonstrated performance:

| Model Architecture | Configuration | Validation F1 | **Test F1** |
| :--- | :--- | :---: | :---: |
| **Stacked Binary Ensemble** | **No Emojis (Best)** | 0.59 | **0.91** |
| Stacked Binary Ensemble | Emojis Replaced | 0.60 | 0.63 |
| Single Multiclass BERT | Adjusted Weights | 0.60 | 0.63 |
| *Official Submission* | *Baseline* | *0.38* | *0.48* |

> **Analysis:** We found that emojis often introduced noise (e.g., "laughing" emojis in sarcastic hate speech), and removing them improved the model's ability to detect implicit hate.

## 🛠️ Installation & Usage

### 1. Clone the repository
```bash
git clone [https://github.com/Ebad-urRehman/AyahVerse-Mahed-SharedTask.git](https://github.com/Ebad-urRehman/AyahVerse-Mahed-SharedTask.git)
cd AyahVerse-Mahed-SharedTask
```

📜 Citation

If you use this code or findings in your research, please cite our paper:
```bash
@inproceedings{rashid-hashir-khalil-2025-ayahverse,
    title = "{A}yah{V}erse at {MAHED} Shared Task: Fine-Tuning {A}rabic{BERT} with Preprocessing for Hope and Hate Detection",
    author = "Rashid, Ibad-ur-Rehman  and
      Hashir Khalil, Muhammad",
    editor = "Darwish, Kareem  and
      Ali, Ahmed  and
      Abu Farha, Ibrahim  and
      Touileb, Samia  and
      Zitouni, Imed  and
      Abdelali, Ahmed  and
      Al-Ghamdi, Sharefah  and
      Alkhereyf, Sakhar  and
      Zaghouani, Wajdi  and
      Khalifa, Salam  and
      AlKhamissi, Badr  and
      Almatham, Rawan  and
      Hamed, Injy  and
      Alyafeai, Zaid  and
      Alowisheq, Areeb  and
      Inoue, Go  and
      Mrini, Khalil  and
      Alshammari, Waad",
    booktitle = "Proceedings of The Third Arabic Natural Language Processing Conference: Shared Tasks",
    month = nov,
    year = "2025",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.arabicnlp-sharedtasks.92/",
    doi = "10.18653/v1/2025.arabicnlp-sharedtasks.92",
    pages = "670--676",
    ISBN = "979-8-89176-356-2",
    abstract = ""
}
```

👥 Authors

Ibad-ur-Rehman Rashid - First Author - Govt. Post Graduate College, Mansehra

Muhammad Hashir Khalil - Co-author

Supervisor - Professor Junaid Hussain
