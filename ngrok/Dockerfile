ARG NGROK_IMAGE=wernight/ngrok:latest
FROM ${NGROK_IMAGE}

USER root

RUN apk update && apk upgrade && apk add nano

USER ngrok
