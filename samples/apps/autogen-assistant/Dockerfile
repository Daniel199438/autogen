FROM python:3.11
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

EXPOSE 8099

WORKDIR /app

CMD ["autogenra ui --port 8099"]

