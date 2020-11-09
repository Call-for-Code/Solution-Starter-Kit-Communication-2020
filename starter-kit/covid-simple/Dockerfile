FROM node:lts-slim

RUN mkdir /app /app/health /app/public
COPY package-slim-docker.json /app/package.json
COPY app.js server.js  .env  /app/
COPY health /app/health/
COPY public /app/public/
WORKDIR /app
RUN npm install

EXPOSE 3000

CMD ["node", "server.js"]
