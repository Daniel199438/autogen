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

# nginx state for serving content
FROM nginx:alpine
# Set working directory to nginx asset directory
WORKDIR /usr/share/nginx/html
# Remove default nginx static assets
RUN rm -rf ./*
# Copy static assets from builder stage
COPY --from=builder /app/autogenra/web/ui .
# Containers run nginx with global directives and daemon off
ENTRYPOINT ["nginx", "-g", "daemon off;"]


