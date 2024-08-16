FROM python:3.9-slim-buster
LABEL Name="Python Flask Demo App" Version=1.3.0

WORKDIR /demoapp
COPY src/requirements.txt .
COPY src/run.py .
RUN pip install --no-cache-dir -r requirements.txt

#COPY run.py .
COPY src/app ./app

EXPOSE 5000

CMD ["gunicorn", "-b", "0.0.0.0:5000", "run:app"]