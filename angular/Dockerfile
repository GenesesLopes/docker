ARG ANGULAR_IMAGE=node:14.2-stretch

FROM ${ANGULAR_IMAGE}

ENV HOME=/home/node

RUN chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g typescript @angular/cli --silent --progress=false

EXPOSE 4200

ENTRYPOINT [ "/bin/bash" ]
