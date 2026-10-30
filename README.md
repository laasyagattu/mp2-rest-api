# MP2: Data Processing REST API

This project is a FastAPI application that wraps the MP1 data cleaning pipeline in a REST API. Users can check the service with `GET /health`, upload a CSV with `POST /upload`, retrieve stored rows with `GET /datasets/{id}`, and validate and clean a stored dataset with `POST /datasets/{id}/process`, which removes duplicates, missing values, and optional outliers based on a JSON configuration and returns a cleaning report. Datasets are kept in memory, every request is logged with a unique request ID, status code, and duration, and the main upload → process → retrieve workflow is covered by pytest tests.

## Run

    python -m pip install -r requirements.txt
    python -m uvicorn main:app --reload

Then open http://127.0.0.1:8000/docs.

## Test

    python -m pytest tests -v