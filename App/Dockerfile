FROM python:3.12

WORKDIR /app

COPY requirements.txt requirements.txt

#env

ARG DB_USER
ENV DB_USER=$DB_USER
ARG DB_PASS
ENV DB_PASS=$DB_PASS
ARG DB_HOST
ENV DB_HOST=$DB_HOST

RUN pip3 install -r requirements.txt

COPY . .

EXPOSE 4000

CMD [ "python3", "app.py" ]