# Network Security - Phishing URL Detector

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Framework-green.svg)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)

A machine learning-powered phishing URL detection application built with **FastAPI**, **scikit-learn**, and **Docker**.

It allows users to enter a URL, extracts security-related features, and predicts whether the URL is **Phishing** or **Safe**.

---

## Features

- FastAPI-based web application.
- Simple and responsive HTML UI with Tailwind CSS.
- URL feature extraction for phishing detection.
- ML model loading via serialized preprocessors and estimators.
- Docker-ready deployment.
- Modular project structure for training, validation, and inference.

---

## How It Works

1. The user submits a URL through the web interface.
2. The application extracts features such as:
   - IP address usage.
   - URL length.
   - URL shortening service.
   - Presence of `@`.
   - Double slash redirection.
   - Prefix/suffix patterns.
   - Subdomain count.
   - SSL state.
   - Domain registration length.
3. The features are passed to the trained model.
4. The app returns a prediction along with the extracted features.

---

## Tech Stack

- **Backend:** FastAPI
- **ML:** scikit-learn, numpy, pandas
- **Web UI:** Jinja2 templates, Tailwind CSS
- **Deployment:** Docker, Uvicorn
- **Utilities:** python-whois, python-dotenv

---

## Project Structure

```bash

└── sankalp2515-networksecuritysystem/
    ├── README.md
    ├── app.py
    ├── Dockerfile
    ├── LICENSE
    ├── main.py
    ├── mongodb_test.py
    ├── push_data.py
    ├── requirements.txt
    ├── setup.py
    ├── data_schema/
    │   └── schema.yaml
    ├── final_model/
    │   └── preprocessor.pkl
    ├── Network_Data/
    │   ├── __init__.py
    │   └── phisingData.csv
    ├── networksecurity/
    │   ├── __init__.py
    │   ├── cloud/
    │   │   ├── __init__.py
    │   │   └── s3_syncer.py
    │   ├── components/
    │   │   ├── __init__.py
    │   │   ├── data_ingestion.py
    │   │   ├── data_transformation.py
    │   │   ├── data_validation.py
    │   │   └── model_trainer.py
    │   ├── constants/
    │   │   ├── __init__.py
    │   │   └── training_pipeline/
    │   │       └── __init__.py
    │   ├── entity/
    │   │   ├── __init_.py
    │   │   ├── artifact_entity.py
    │   │   └── config_entity.py
    │   ├── exception/
    │   │   ├── __init_.py
    │   │   └── exception.py
    │   ├── logging/
    │   │   ├── __init_.py
    │   │   └── logger.py
    │   ├── pipeline/
    │   │   ├── __init_.py
    │   │   └── training_pipeline.py
    │   └── utils/
    │       ├── __init_.py
    │       ├── main_utils/
    │       │   ├── __init__.py
    │       │   └── utils.py
    │       └── ml_utils/
    │           ├── __init__.py
    │           ├── metric/
    │           │   ├── __init__.py
    │           │   └── classification_metric.py
    │           └── model/
    │               ├── __init__.py
    │               └── estimator.py
    ├── valid_data/
    │   └── test.csv
    └── .github/
        └── workflows/
            └── main.yaml

```

---

## Installation

### Prerequisites

- Python 3.11+
- pip
- Docker, if you want containerized deployment

### Setup with pip

```bash
git clone https://github.com/sankalp2515/NetworkSecuritySystem.git
cd NetworkSecuritySystem
pip install -r requirements.txt
```

### Run the App

```bash
python app/main.py
```

Then open:

```bash
http://localhost:8000
```

---

## Docker Setup

Build the image:

```bash
docker build -t network-security-app .
```

Run the container:

```bash
docker run -p 8000:8000 network-security-app
```

---

## Example Usage

Enter a URL such as:

```text
http://example.com
```

The app will return:
- Prediction: `Phishing` or `Safe`
- Extracted feature values used for analysis

---

## Dataset

This project uses a phishing URL dataset stored in `data/phisingData.csv`. The dataset contains URL-based and domain-based indicators commonly used for phishing detection.

---

## Testing and Code Quality

The repository includes configuration for:
- `tox`
- `mypy`
- `black`
- `isort`
- `pylint`

You can run quality checks using:

```bash
tox
```

---

## Deployment Notes

The app is containerized using a slim Python 3.11 Docker image and exposes port `8000`. It is designed for quick local deployment and easy extension into cloud or CI/CD workflows.

---

## Limitations

- Some features are currently extracted with simplified heuristics.
- The final prediction logic may need tighter alignment with the full trained feature set.
- WHOIS and SSL checks may fail for domains with network restrictions or unavailable records.

---

## Future Improvements

- Add confidence score output.
- Align feature extraction with the full training schema.
- Improve error handling for malformed URLs.
- Add API endpoint for JSON-based inference.
- Include unit tests and CI coverage badges.

---

## License

GNU GENERAL PUBLIC LICENSE.
---

## Author
Sankalp Wanjari
