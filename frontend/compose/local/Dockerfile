FROM node:lts-slim

ARG APP_HOME=/app

WORKDIR ${APP_HOME}

RUN apt-get update && apt-get install

COPY package*.json ./

RUN npm install

EXPOSE 3000

COPY . .

CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0", "--port", "3000"]
