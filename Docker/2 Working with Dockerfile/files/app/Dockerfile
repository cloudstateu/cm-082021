FROM node:10

COPY package.json .
COPY server.js .

EXPOSE 8080

RUN npm install

CMD ["node", "server.js"]