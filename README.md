# Aéro Guard Backend & Safety Gate Service

Aéro Guard is a production-grade FastAPI application designed to evaluate commuter exposure risk. It integrates a trained Random Forest classification model with automated safety gate logic to flag high-risk conditions in real time.

---

## 🚀 Key Features

* **FastAPI Backend**: High-performance asynchronous API endpoints for health checks and live inference.
* **Random Forest Inference**: Directly loads and executes serialized models (`aeroguard_model.joblib`) with strict input feature contracts.
* **Automated Safety Gate**: Evaluates model prediction outputs against predefined risk thresholds to trigger safety gates when high exposure is detected.
* **Robust Error Handling**: Graceful failure handling for missing models, invalid payload shapes, or runtime exceptions.

---

## 🛠️ Project Architecture & Specifications

* **Model Type**: `RandomForestClassifier` (Binary classification: `[0, 1]`)
* **Input Shape**: Exactly 3 positional features (`n_features_in_ = 3`) mapped via Pydantic data contracts.
* **Primary Endpoints**:
* `GET /`: Returns service status and model loading state.
* `GET /health`: Kubernetes/Cloud-ready health check probe.
* `POST /predict`: Evaluates feature payloads, computes risk levels, and returns safety gate flags.



---

## 📦 Installation & Setup

1. **Clone or navigate to the project directory**:
```bash
cd /content/deploy_dir

```


2. **Install dependencies**:
```bash
pip install -r requirements.txt

```


3. **Run the FastAPI server locally**:
```bash
uvicorn app:app --host 0.0.0.0 --port 8000 --reload

```



---

## 🔌 API Usage Example

### Request (`POST /predict`)

```json
{
  "feature_0": 0.12,
  "feature_1": -1.5,
  "feature_2": 0.25
}

```

### Response

```json
{
  "prediction": 1,
  "risk_level": "HIGH",
  "safety_gate_triggered": true,
  "message": "Safety gate engaged due to high exposure risk threshold."
}

```

---

## 🐳 Containerization (Google Cloud Run)

To containerize the service for cloud deployment, use a standard multi-stage or python base `Dockerfile`:

```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8080

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8080"]

```

---
