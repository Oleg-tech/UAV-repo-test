# Use the official Python image
FROM python:3.10-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set the working directory inside the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y gcc python3-dev libpq-dev

# Install Python dependencies
COPY requirements.txt /app/

RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy the rest of the application code
COPY . /app/

WORKDIR /app/uav_components_search

# Run database migrations (optional, you can move this to your docker-compose)
CMD ["python", "manage.py", "migrate"]

# Expose the port Django runs on
EXPOSE 8000

# Run the Django development server
CMD ["python", "manage.py", "runserver"]
