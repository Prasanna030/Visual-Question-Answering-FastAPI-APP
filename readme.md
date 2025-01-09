# Visual Question Answering Application

A Docker containerizable web application that performs Visual Question Answering (VQA) using the ViLT model from Hugging Face. The application allows users to upload an image and ask questions about it, receiving AI-generated answers in real-time.Did this project to explore deployment of ML Models using FastAPI and Docker.

## Features

- Visual Question Answering using the ViLT-B32 model fine-tuned for VQA
- RESTful API built with FastAPI
- Dockerized application for easy deployment
- Simple and intuitive user interface
- Efficient image processing and model inference

## Technology Stack

- **ML Model**: [ViLT-B32 (dandelin/vilt-b32-finetuned-vqa)](https://huggingface.co/dandelin/vilt-b32-finetuned-vqa)
- **Backend**: FastAPI
- **Containerization**: Docker
- **Python Dependencies**: transformers, torch, Pillow, fastapi, uvicorn

## Installation

### Using Docker

1. Clone the repository:
```bash
git clone <your-repository-url>
cd <repository-name>
```

2. Compose Up and build:
```bash
docker compose up --build
```

### Manual Installation

1. Clone the repository:
```bash
git clone <your-repository-url>
cd <repository-name>
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run the application:
```bash
uvicorn main:app --reload # For auto reloading
```

## Usage

1. Access the application at `http://localhost:8000`
2. Upload an image using the interface
3. Enter your question about the image
4. Click "Submit" to receive the AI-generated answer

## API Endpoints

### POST `/ask`
Performs visual question answering on an uploaded image.

**Request Body**:
- `image`: Image file (multipart/form-data)
- `text`: String containing the question about the image

**Response**:
```json
{
    "answer": "<Generated answer to the question>",

}
```

## Docker Configuration

The application is containerized using Docker with the following specifications:

```dockerfile
FROM python:3.10.12
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["uvicorn", "main:app", "--reload"]
```


## Acknowledgments

- [Hugging Face](https://huggingface.co/) for providing the ViLT model
- The ViLT model creators and contributors
- Patrick Loeber (https://github.com/patrickloeber)