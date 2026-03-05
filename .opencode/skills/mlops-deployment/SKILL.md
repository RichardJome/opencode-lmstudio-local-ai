---
name: mlops-deployment
description: MLOps tools - Docker, MLflow, model serving, Kubernetes
license: MIT
compatibility: opencode
metadata:
  audience: ml-engineers
  workflow: deployment
---

## What I do

- Create Dockerfiles for ML
- Set up MLflow tracking
- Configure model serving
- Kubernetes deployment
- CI/CD for ML

## When to use me

Use this when deploying ML models to production.

## Docker for ML

```dockerfile
FROM pytorch/pytorch:2.2.0-cuda12.1-cudnn8-runtime
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "serve.py"]
```

## MLflow Setup

```python
import mlflow

mlflow.set_experiment("my_experiment")
with mlflow.start_run():
    mlflow.log_param("epochs", 10)
    mlflow.log_metric("accuracy", 0.95)
    mlflow.log_artifact("model.pt")
```

## Model Serving Options

- **TorchServe**: PyTorch model serving
- **TensorFlow Serving**: TF models
- **Triton Inference Server**: NVIDIA optimized
- **FastAPI**: Custom endpoints
- **Ray Serve**: Distributed serving

## Kubernetes

```yaml
apiVersion: serving.kubeflow.org/v1beta1
kind: InferenceService
metadata:
  name: my-model
spec:
  predictor:
    model:
      modelFormat: onnx
      storageUri: s3://bucket/model.onnx
```
