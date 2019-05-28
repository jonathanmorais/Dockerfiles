FROM python:3.7.3-alpine

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt && pip install pika --upgrade

CMD [ "python", "-u", "./app.py" ]