FROM node:8

RUN apt-get update -q && \
    apt-get dist-upgrade -y && \
    apt-get clean && \
    apt-get autoclean

EXPOSE 8000

ENV SRV_PATH /usr/local/share/koel

RUN mkdir -p $SRV_PATH && \
    chown node:node $SRV_PATH

WORKDIR $SRV_PATH

USER node

COPY ./package.json ./yarn.lock $SRV_PATH/

RUN yarn install

COPY . $SRV_PATH/

CMD [ "npm", "start" ]