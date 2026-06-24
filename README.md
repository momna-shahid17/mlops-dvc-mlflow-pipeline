# End-to-End MLOps Pipeline with DVC, MLflow, and DagsHub

## Overview

This project demonstrates an end-to-end Machine Learning Operations (MLOps) pipeline built using DVC, MLflow, and DagsHub. The pipeline automates data preprocessing, model training, and evaluation while ensuring reproducibility, experiment tracking, and version control throughout the machine learning lifecycle.

A Random Forest Classifier is trained on the Pima Indians Diabetes Dataset to predict diabetes outcomes. DVC is used for data and model versioning, while MLflow tracks experiments, metrics, parameters, and artifacts.

---

## Architecture

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
Model Evaluation
     │
     ▼
MLflow Tracking
     │
     ▼
DVC Versioning
     │
     ▼
DagsHub Remote Storage
```

---

## Features

* End-to-end MLOps workflow
* Data versioning using DVC
* Model versioning and reproducibility
* Experiment tracking with MLflow
* Automated pipeline execution
* Hyperparameter tracking
* Model artifact management
* DagsHub integration for collaboration
* Reproducible machine learning workflows

---

## Workflow

### 1. Data Preprocessing

The preprocessing stage reads the raw dataset and performs necessary transformations before generating the processed dataset.

**Input**

* Raw dataset

**Output**

* Processed dataset

### 2. Model Training

A Random Forest Classifier is trained using the processed dataset.

**Tracked Parameters**

* Random State
* Number of Estimators
* Maximum Tree Depth

**Generated Artifact**

* Trained Model (`model.pkl`)

### 3. Model Evaluation

The trained model is evaluated and performance metrics are logged to MLflow.

**Tracked Metrics**

* Accuracy Score
* Experiment Metadata
* Model Artifacts

---

## Tech Stack

| Category                | Tools         |
| ----------------------- | ------------- |
| Programming Language    | Python        |
| Machine Learning        | Scikit-learn  |
| Experiment Tracking     | MLflow        |
| Data & Model Versioning | DVC           |
| Collaboration Platform  | DagsHub       |
| Version Control         | Git           |
| Data Processing         | Pandas, NumPy |

---

## Project Structure

```text
.
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
└── README.md
```

---

## Pipeline Stages

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

### Run Complete Pipeline

```bash
dvc repro
```

---

## DVC Pipeline Definition

The following commands were used to create the DVC pipeline stages:

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

These commands generate the pipeline definition stored in `dvc.yaml`, enabling reproducible and automated execution of the machine learning workflow.

---

## Project Outcomes

* Built a reproducible machine learning workflow
* Implemented data and model versioning using DVC
* Tracked experiments and metrics using MLflow
* Integrated DagsHub for remote collaboration
* Automated ML pipeline execution through DVC stages
* Demonstrated MLOps best practices for experiment management

---

## Use Cases

* MLOps Learning Projects
* Machine Learning Experiment Tracking
* Model Versioning
* Reproducible Research
* Team Collaboration
* Production-Oriented ML Workflows

---

## Future Improvements

* CI/CD Integration
* Automated Model Deployment
* Model Monitoring
* Data Validation
* Feature Store Integration
* Kubernetes-Based Deployment

---

## Author

### Momna Shahid
**DevOps Engineer | Cloud Engineer | MLOps Engineer**
