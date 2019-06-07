FROM node:stretch

ENV HOME=/home/node

WORKDIR $HOME

##Dependências
RUN apt-get update && apt-get install -y nano && apt-get install -y openjdk-8-jdk-headless && \
apt-get install -y openjdk-8-jdk

##Android
RUN wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip && \
unzip sdk-tools-linux-4333796.zip && mkdir -p Android/Sdk && \
mv tools Android/Sdk/. && echo "export ANDROID_HOME=~/Android/Sdk" >> .profile && \
echo "export PATH=$PATH:$ANDROID_HOME/tools" >> .profile && \ 
echo "export PATH=$PATH:$ANDROID_HOME/platform-tools" >> .profile

RUN ~/Android/Sdk/tools/bin/sdkmanager "platform-tools" "platforms;android-27" "build-tools;27.0.3"

#RUN chmod -R 777 Android
##React Native
#RUN npm install -g react-native-cli


EXPOSE 3000

#ENTRYPOINT [ "/bin/bash" ]
