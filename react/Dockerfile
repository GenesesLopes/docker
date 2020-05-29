ARG REACT_IMAGE=node:14.2-stretch
FROM ${REACT_IMAGE}

ENV HOME=/home/node

RUN apt update && apt install git nano -y && chmod -R 777 $HOME && chmod -R 777 /usr/local/lib/node_modules && chmod -R 777 /usr/local/bin

WORKDIR $HOME

RUN npm install -g create-react-app create-next-app

EXPOSE 3000

ENTRYPOINT [ "/bin/bash" ]
