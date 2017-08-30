FROM debian:9

RUN apt-get update && apt-get -y install curl less man-db xz-utils

RUN curl -LO https://nodejs.org/dist/v6.11.2/node-v6.11.2-linux-x64.tar.xz && \
    tar -xvf node-v6.11.2-linux-x64.tar.xz && \
    cp -r node-v6.11.2-linux-x64/* /usr/local && \
    rm -rf node-v6.11.2-linux-x64 node-v6.11.2-linux-x64.tar.xz

RUN useradd -m node
WORKDIR /home/node/app

COPY package.json "${PWD}"
RUN npm install
COPY "${PWD}" "${PWD}"

USER node
ENTRYPOINT ["node", "app.js"]
