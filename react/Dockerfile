FROM node:alpine

ENV HOME=/home/node

RUN apk update && apk add git && chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g create-react-app

EXPOSE 3000

ENTRYPOINT [ "/bin/sh" ]
