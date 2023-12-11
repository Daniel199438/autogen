FROM python:3.11 AS builder
RUN apt-get update && apt-get -y update
RUN apt-get install -y sudo git npm

COPY . /app
WORKDIR /app

RUN pip install -e .

RUN npm install -g gatsby-cli
RUN npm install --global yarn

WORKDIR /app/frontend

RUN yarn install
RUN yarn build

EXPOSE 8081

# Führen Sie den Befehl aus, wenn der Container gestartet wird
CMD ["python", "-m", "autogenra.cli", "ui"]


