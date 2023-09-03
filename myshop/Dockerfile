# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory to /app
WORKDIR /app

# Install gcc
RUN apt-get update && apt-get install -y gcc
# Install necessary system libraries
RUN apt-get update && apt-get install -y libglib2.0-0

# Install necessary system libraries
RUN apt-get update && apt-get install -y libpango1.0-0

# Install necessary system libraries
RUN apt-get update && apt-get install -y gettext

# Install necessary system libraries
RUN apt-get update && apt-get install -y libgtk-3-dev

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 8000

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000","gunicorn", "myshop.wsgi:application", "--bind", "0.0.0.0:8000", "--workers", "4", "--log-file", "/var/log/gunicorn.log"]
