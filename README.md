# Text-to-Emotion-Predictor

A FastAPI web application that predicts the emotional tone of a sentence using a trained BiGRU deep learning model. The app accepts free-text input and returns the likely emotion along with confidence scores for all supported classes.

## Supported emotions

- sadness
- joy
- love
- anger
- fear
- surprise

## Features

- Text preprocessing for cleaner input
- BiGRU model inference using Keras
- REST API endpoint for prediction
- Responsive browser UI for testing the model interactively
- Confidence breakdown across all emotion classes

## Project structure

- `main.py` — FastAPI app, model loader, and prediction endpoint
- `static/` — frontend HTML, CSS, and JavaScript for the web UI
- `Artifacts/` — trained model and tokenizer files
- `requirements.txt` — Python dependencies
- `runtime.txt` — Python runtime version

## Local setup

1. Clone the repository.
2. Create and activate a virtual environment.
3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Run the application:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

5. Open the browser at:

```text
http://localhost:8000
```

## API usage

### Health check

```bash
curl http://localhost:8000/health
```

### Predict emotion

```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{"text":"I feel so happy today!"}'
```

Example response:

```json
{
  "text": "I feel so happy today!",
  "predicted_emotion": "joy",
  "confidence": 0.91,
  "all_probabilites": {
    "sadness": 0.02,
    "joy": 0.91,
    "love": 0.03,
    "anger": 0.01,
    "fear": 0.01,
    "surprise": 0.02
  }
}
```

## Tech stack

- Python 3.11
- FastAPI
- TensorFlow / Keras
- NumPy
- Pydantic
- Static HTML/CSS/JavaScript frontend

## License

This project is provided for educational and demonstration purposes.
