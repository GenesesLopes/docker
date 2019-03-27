FROM node:alpine

ENV HOME=/home/node

RUN chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g create-react-app

EXPOSE 3000

ENTRYPOINT [ "/bin/sh" ]
