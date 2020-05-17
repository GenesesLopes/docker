ARG REACT_IMAGE=node:14.2-stretch
ARG UID=1000 
ARG GID=1000
FROM ${REACT_IMAGE}

ENV HOME=/home/node

RUN apt update && apt install git && chmod -R 777 $HOME

WORKDIR $HOME

RUN npm install -g create-react-app create-next-app

EXPOSE 3000

ENTRYPOINT [ "/bin/bash" ]
