FROM node:14-alpine

RUN mkdir -p /home/node/api/node_modules
WORKDIR /home/node/api

COPY package.json ./

RUN yarn

COPY . .

EXPOSE 3333

ENTRYPOINT [ "node", "server.js" ]
