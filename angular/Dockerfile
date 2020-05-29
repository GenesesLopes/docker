ARG ANGULAR_IMAGE=node:14.2-stretch

FROM ${ANGULAR_IMAGE}

ENV HOME=/home/node

RUN apt update && apt install git nano -y && chmod -R 777 $HOME && chmod -R 777 /usr/local/lib/node_modules && chmod -R 777 /usr/local/bin

WORKDIR $HOME

RUN npm install -g typescript @angular/cli --silent --progress=false

EXPOSE 4200

ENTRYPOINT [ "/bin/bash" ]
