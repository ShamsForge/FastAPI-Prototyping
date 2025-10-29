# Simple Dockerfile for the Boilerplate FastAPI app
# - Uses python:3.11-slim
# - Installs dependencies from requirements.txt if present; otherwise installs fastapi and uvicorn
# - Copies the source under /app and runs uvicorn

FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /app

# Copy requirements if present; if pip install fails (no file), fall back to installing minimal deps
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt || pip install --no-cache-dir fastapi uvicorn

# Copy the project source
COPY src/ /app

EXPOSE 8000

# Run the FastAPI app. Adjust module path if your app object lives elsewhere.
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
