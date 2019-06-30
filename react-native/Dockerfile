FROM node:stretch

ENV HOME=/home/node

WORKDIR $HOME

RUN npm install -g grunt-cli \
    && npm install -g brunch \
    && npm install -g bower \
    && npm install -g yarn \
    && npm install -g create-react-native-app \
    && npm install -g react-native-cli \ 
    && npm install -g expo-cli 

#Dependências
RUN apt-get update && apt-get install -y nano && apt-get install -y openjdk-8-jdk-headless && \
apt-get install -y openjdk-8-jdk && apt-get install adb -y

#Android
#RUN wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip && \
#unzip sdk-tools-linux-4333796.zip
#RUN mkdir -p /home/node/Android/Sdk && mv tools Android/Sdk/.
# adb kill-server && adb start-server && react-native init Projeto
RUN echo "export ANDROID_HOME=/home/node/Android/Sdk" >> /etc/bash.bashrc && \
echo "export PATH=$PATH:$ANDROID_HOME/tools" >> /etc/bash.bashrc && \ 
echo "export PATH=$PATH:$ANDROID_HOME/platform-tools" >> /etc/bash.bashrc

#RUN /home/node/Android/Sdk/tools/bin/sdkmanager "platform-tools" "platforms;android-27" "build-tools;27.0.3"

EXPOSE 3000 19000 19001 8081 5037 5555

CMD ["/bin/bash"]




##React Native
#RUN npm install -g react-native-cli


#EXPOSE 3000

#ENTRYPOINT [ "/bin/bash" ]
