# 🚀 End-to-End MLOps Pipeline with DVC, MLflow, and DagsHub

## Overview

This project implements an end-to-end MLOps pipeline using DVC, MLflow, and DagsHub to automate data preprocessing, model training, evaluation, experiment tracking, and version control. The pipeline is designed to ensure reproducibility, traceability, and collaboration throughout the machine learning lifecycle.

A Random Forest Classifier is trained on the Pima Indians Diabetes Dataset to predict diabetes outcomes. DVC manages data and model versioning, MLflow tracks experiments, metrics, and artifacts, while DagsHub provides remote storage and collaboration for reproducible machine learning workflows.

---

## ✨ Features

* End-to-End MLOps Workflow
* Data Versioning with DVC
* Model Versioning & Reproducibility
* Experiment Tracking with MLflow
* Automated Pipeline Execution
* Hyperparameter Tracking
* Model Artifact Management
* Pipeline Reproducibility
* Parameter Management
* Artifact Versioning
* DagsHub Integration for Collaboration
* Reproducible Machine Learning Workflows

---

## 🏗️ Architecture

```text
Raw Dataset
     │
     ▼
Data Preprocessing
     │
     ▼
Model Training
     │
     ▼
MLflow Experiment Tracking
     │
     ▼
Model Evaluation
     │
     ▼
DVC Data & Model Versioning
     │
     ▼
DagsHub Remote Storage
```

---

## 🔄 Workflow

### 1. Data Preprocessing

The preprocessing stage reads the raw dataset and performs the required transformations before generating the processed dataset.

**Input**

* Raw Dataset

**Output**

* Processed Dataset

---

### 2. Model Training

A Random Forest Classifier is trained using the processed dataset.

**Tracked Parameters**

* Random State
* Number of Estimators
* Maximum Tree Depth

**Generated Artifact**

* Trained Model (`model.pkl`)

---

### 3. Model Evaluation

The trained model is evaluated and the results are automatically logged to MLflow.

**Tracked Metrics**

* Accuracy Score
* Experiment Parameters
* Model Artifacts

---

## 🛠️ Tech Stack

| Category                | Technologies  |
| ----------------------- | ------------- |
| Programming Language    | Python        |
| Machine Learning        | Scikit-learn  |
| Experiment Tracking     | MLflow        |
| Data & Model Versioning | DVC           |
| Collaboration Platform  | DagsHub       |
| Data Processing         | Pandas, NumPy |
| Version Control         | Git, GitHub   |
| Configuration           | YAML          |

---

## 📁 Project Structure

```text
mlops-dvc-mlflow-pipeline/
├── data/
│   ├── raw/
│   └── processed/
├── models/
├── src/
│   ├── preprocess.py
│   ├── train.py
│   └── evaluate.py
├── dvc.yaml
├── dvc.lock
├── params.yaml
├── requirements.txt
├── README.md
```

---

## ⚙️ Installation

### Clone the repository

```bash
git clone https://github.com/momna-shahid17/mlops-dvc-mlflow-pipeline.git
```

### Navigate to the project directory

```bash
cd mlops-dvc-mlflow-pipeline
```

### Create a virtual environment

```bash
python -m venv venv
```

### Activate the virtual environment

**Windows**

```bash
venv\Scripts\activate
```

**Linux / macOS**

```bash
source venv/bin/activate
```

### Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Run Individual Pipeline Stages

### Preprocess Stage

```bash
python src/preprocess.py
```

### Train Stage

```bash
python src/train.py
```

### Evaluate Stage

```bash
python src/evaluate.py
```

---

## 🚀 Run the Complete Pipeline

```bash
dvc repro
```

---

## 📄 DVC Pipeline Definition

The following commands were used to create the DVC pipeline stages.

### Preprocess Stage

```bash
dvc stage add -n preprocess \
    -p preprocess.input,preprocess.output \
    -d src/preprocess.py -d data/raw/data.csv \
    -o data/processed/data.csv \
    python src/preprocess.py
```

### Train Stage

```bash
dvc stage add -n train \
    -p train.data,train.model,train.random_state,train.n_estimators,train.max_depth \
    -d src/train.py -d data/raw/data.csv \
    -o models/model.pkl \
    python src/train.py
```

### Evaluate Stage

```bash
dvc stage add -n evaluate \
    -d src/evaluate.py \
    -d models/model.pkl \
    -d data/raw/data.csv \
    python src/evaluate.py
```

These commands generate the pipeline definition stored in **dvc.yaml**, enabling reproducible and automated execution of the machine learning workflow.

---

## 🎯 Project Outcomes

* Built a reproducible end-to-end MLOps workflow using DVC and MLflow.
* Implemented data and model versioning to ensure experiment reproducibility.
* Tracked model parameters, metrics, and artifacts with MLflow.
* Integrated DagsHub for remote experiment collaboration and version control.
* Automated machine learning workflows using DVC pipeline stages.
* Demonstrated industry-standard MLOps practices for machine learning lifecycle management.

---

## 💼 Use Cases

* MLOps Learning Projects
* Machine Learning Experiment Tracking
* Data & Model Versioning
* Reproducible Machine Learning Workflows
* Team Collaboration
* Production-Oriented ML Pipelines

---

## 🚀 Future Enhancements

* CI/CD Integration
* Docker Containerization
* GitHub Actions Automation
* Automated Model Deployment
* Model Monitoring
* Data Validation
* Feature Store Integration
* Kubernetes-Based Deployment

---

## 👩‍💻 Author

**Momna Shahid**

**DevOps • Cloud • Kubernetes • MLOps Engineer**

**GitHub:** https://github.com/momna-shahid17

**LinkedIn:** https://www.linkedin.com/in/momna-shahid/

---

## 📄 License

This project is licensed under the **MIT License**.
