FROM node:8.9.0

EXPOSE 11014

WORKDIR /root/app

RUN curl https://install.meteor.com/ | sh
RUN git clone "https://github.com/x-a-n-d-e-r-k/lair" \
    && cd lair/app \
    && meteor npm install --save babel-runtime \
    && meteor build --directory /root/app --allow-superuser

COPY ./package.json /root/app/bundle/programs/server/package.json
RUN cd bundle/programs/server \
    && npm i

ENV ROOT_URL=http://0.0.0.0
ENV PORT 11014
ENV MONGO_URL=mongodb://lairdb:27017/lair
ENV MONGO_OPLOG_URL=mongodb://lairdb:27017/local

CMD sleep 4 && cd /root/app/bundle/programs/server && meteor npm start
