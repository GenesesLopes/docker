ARG REACT_IMAGE=node:14.2-stretch
FROM ${REACT_IMAGE}

ENV HOME=/home/node

RUN apt update && apt install git nano && chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g create-react-app create-next-app

EXPOSE 3000

ENTRYPOINT [ "/bin/bash" ]
