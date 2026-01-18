FROM python:3.11-slim
WORKDIR /app
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

COPY requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt && pip install --no-cache-dir gunicorn

# copy the backend context (Docker build context is ./backend when used from docker-compose)
COPY . .
EXPOSE 5000

# run.py exposes a top-level `app` so gunicorn run:app works
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "run:app"]
