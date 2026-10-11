# 🎬 Real-Time ML Inference REST API

A machine learning project that provides a REST API for real-time movie review sentiment analysis using TensorFlow, Keras, and FastAPI.

The API accepts a movie review as JSON input and predicts whether the sentiment is **positive or negative**, returning the prediction and associated probabilities.

## 📌 Project Overview

This project demonstrates how to deploy a trained deep learning model as a REST API. It includes input validation, prediction endpoints, automated testing, and Docker configuration.

**Project:** Task 6 — Real-Time ML Inference REST API & Capstone  
**Organization:** RABTECH Academy  
**Model:** Deep Learning Text Classifier  
**Dataset:** IMDb Movie Reviews (ACL IMDb dataset)  
**Test Accuracy:** 84.56%

## 🚀 Features

- Real-time movie review sentiment predictions
- FastAPI REST API
- Positive and negative sentiment probabilities
- JSON request and response formats
- Input validation using Pydantic
- Health-check endpoint
- Automated API tests using Pytest
- Docker container configuration
- Interactive API documentation

## 🧠 Model Information

The sentiment classifier was trained using the IMDb movie review dataset.

The model processes review text and generates a sentiment probability.

| Output | Description |
|---|---|
| `positive` | Review classified as positive |
| `negative` | Review classified as negative |
| `positive_probability` | Model score for positive sentiment |
| `negative_probability` | Complement of the positive probability |

**Test accuracy:** 84.56%

Note: The probabilities represent the model's scores and are not necessarily calibrated estimates of real-world likelihood.

## 🏗️ Project Architecture

1. A client sends a movie review to the API.
2. FastAPI validates the incoming JSON request.
3. The trained TensorFlow/Keras model processes the text.
4. The model generates a sentiment score.
5. The API returns the sentiment label and probabilities as JSON.

## 📂 Repository Structure

```text
task6_project/
├── app/
│   └── main.py
├── models/
│   └── imdb_sentiment_api.keras
├── tests/
│   └── test_api.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
├── .gitignore
└── README.md
```

## 🛠️ Technologies Used

- Python 3.11
- TensorFlow
- Keras
- FastAPI
- Uvicorn
- Pydantic
- Pytest
- HTTPX
- Docker

## ⚙️ Installation and Setup

### Prerequisites

Install the following before running the project:

- Python 3.11
- pip
- Docker (optional, for containerized deployment)

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Replace `YOUR_USERNAME` and `YOUR_REPOSITORY` with your GitHub username and repository name.

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Start the API

Run this command from the project root:

```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

### 4. Open the API documentation

Visit:

http://localhost:8000/docs

The interactive Swagger UI allows you to test the API directly from your browser.

## 🔌 API Endpoints

### 1. Health Check

**Endpoint:** `GET /health`

Checks whether the API is running and the model has loaded.

Example response:

```json
{
  "status": "ok",
  "model_loaded": true
}
```

### 2. Sentiment Prediction

**Endpoint:** `POST /predict`

Accepts a movie review and returns its predicted sentiment.

**Example request:**

```json
{
  "text": "This movie was fantastic, entertaining, and beautifully acted!"
}
```

**Example response:**

```json
{
  "prediction": "positive",
  "positive_probability": 0.95,
  "negative_probability": 0.05
}
```

The probability values above are illustrative examples. Actual predictions depend on the trained model and input text.

### Example negative review

**Request:**

```json
{
  "text": "This movie was boring and disappointing."
}
```

**Possible response:**

```json
{
  "prediction": "negative",
  "positive_probability": 0.08,
  "negative_probability": 0.92
}
```

These example values are illustrative, not guaranteed model outputs.

## 🧪 Automated Testing

The project includes automated tests to validate the API's behavior.

Run the tests from the project root:

```bash
pytest -q
```

The test suite checks:

- Health endpoint response
- Prediction response schema
- Probability values and their sum
- Rejection of empty review text

The tests use a lightweight fake model to test API behavior without loading the full trained model.

## 🐳 Docker Deployment

The project includes a Dockerfile for containerized deployment.

### Build the Docker image

Run from the project root:

```bash
docker build -t imdb-sentiment-api .
```

### Run the container

```bash
docker run --rm -p 8000:8000 imdb-sentiment-api
```

Once the container starts, open:

http://localhost:8000/docs

**Note:** The first Docker build may take some time because TensorFlow has substantial dependencies.

## 📊 Model Evaluation

| Metric | Result |
|---|---|
| Dataset | IMDb Movie Reviews |
| Task | Binary sentiment classification |
| Test Accuracy | 84.56% |
| Classes | Positive, Negative |
| Deployment Framework | FastAPI |
| ML Framework | TensorFlow/Keras |

Accuracy is reported from the model's evaluation on the test dataset. Performance on new reviews may differ.

## 🎯 Learning Outcomes

This project demonstrates practical skills in:

- Training and evaluating a deep learning text classifier
- Saving and loading a trained ML model
- Building REST APIs with FastAPI
- Validating input and output schemas
- Writing automated tests with Pytest
- Managing dependencies with `requirements.txt`
- Containerizing an ML application using Docker
- Preparing a machine learning project for GitHub

## 🔮 Future Improvements

- Add batch prediction support
- Introduce request logging and monitoring
- Add model versioning
- Evaluate additional classification metrics
- Deploy the API to a cloud platform
- Add continuous integration for automated testing

## 👨‍💻 Author

**RABTECH Academy — Task 6 Project**

Developed as part of a machine learning deployment and capstone assignment.

## 📄 License

This project is intended for educational and demonstration purposes. Add a license file if you intend to distribute or reuse the project under specific terms.
