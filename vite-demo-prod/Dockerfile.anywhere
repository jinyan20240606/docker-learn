FROM node:16-alpine3.15

RUN mkdir -p /home/app/

WORKDIR /home/app/

RUN npm i anywhere -g

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

EXPOSE 8080

CMD anywhere -p 8080 -d ./dist -s
