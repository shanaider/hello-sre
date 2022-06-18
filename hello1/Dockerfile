FROM node:16-alpine

ENV NODE_ENV=production

WORKDIR /app
COPY . .

RUN npm install express
RUN npm install redis@3.1.2


ENV port=redis_port
ENV host=redis_host
ENV password=redis_password


EXPOSE 8000

CMD [ "node", "hello-1.js" ]
