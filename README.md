## Network Security Project for Phishing Data


## Overview

The Network Security System is designed to detect phishing attacks using a machine learning pipeline. The project includes data ingestion, validation, transformation, model training, and API deployment for real-time predictions. The system is built using FastAPI, MongoDB, and MLflow for model tracking.

## Features

- Data Ingestion: Extracts phishing data from CSV and loads it into MongoDB.

- Data Validation: Ensures data quality before model training.

- Data Transformation: Prepares data for training.

- Model Training: Uses scikit-learn to build a phishing detection model.

- Deployment: FastAPI-based API for real-time inference.

- Docker Support: Containerized deployment with Docker.

## Project Structure

```
├── app.py                 # FastAPI application for API serving
├── main.py                # Main training pipeline execution
├── push_data.py           # Script to insert phishing data into MongoDB
├── test_mongodb.py        # MongoDB connection test
├── setup.py               # Package setup script
├── requirements.txt       # List of dependencies
├── Dockerfile             # Docker setup for deployment
├── .gitignore             # Files to be ignored in Git
├── README.md              # Documentation

```

## Installation

### Prerequisites

- Python 3.8+

- MongoDB

- Docker (optional for deployment)

### Setup

**1. Clone the Repository**
```
git clone https://github.com/your-repo/network-security-system.git
cd network-security-system
```

**2. Install Dependencies**
```
pip install -r requirements.txt
```

**3. Set Up MongoDB**

Ensure MongoDB is running and configure .env with:
```
MONGODB_URL_KEY=<your-mongodb-connection-string>
```

### Usage

#### Running the Application

1. Start the FastAPI Server

```
uvicorn app:app --host 0.0.0.0 --port 8000
```
Visit `http://localhost:8000/docs` to test API endpoints.

2. Train the Model

Use the `/train` API endpoint to start model training.
```
curl -X GET "http://localhost:8000/train"
```
3. Make Predictions

Upload a CSV file to the `/predict` endpoint to get predictions.
```
curl -X POST -F "file=@phishing_data.csv" "http://localhost:8000/predict"
```

### Docker Deployment

1. Build the Docker Image
```
docker build -t network-security .
```

2. Run the Container

```
docker run -p 8000:8000 network-security
```

