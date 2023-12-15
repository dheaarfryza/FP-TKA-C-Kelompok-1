FROM python:alpine

WORKDIR /app

COPY ./src/ /app/

RUN pip install -r requirements.txt

CMD ["gunicorn", "-w", "20", "-b", "0.0.0.0:80", "app:app"]
