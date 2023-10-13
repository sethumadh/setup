FROM node:13-alpine

ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=password

RUN npm install -g nodemon

RUN mkdir -p /home/app

WORKDIR /home/app

COPY . .

RUN npm install

CMD ["npm", "run","dev"]
