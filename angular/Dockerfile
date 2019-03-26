FROM node:alpine

ENV HOME=/home/node

RUN chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g typescript 
RUN npm install -g @angular/cli --silent --progress=false

EXPOSE 4200

ENTRYPOINT [ "/bin/sh" ]
