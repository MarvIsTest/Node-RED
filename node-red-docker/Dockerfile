FROM node:18

ENV http_proxy=http://rb-proxy-de.bosch.com:8080
ENV https_proxy=http://rb-proxy-de.bosch.com:8080
ENV HTTP_PROXY=http://rb-proxy-de.bosch.com:8080
ENV HTTPS_PROXY=http://rb-proxy-de.bosch.com:8080


WORKDIR /usr/src/node-red
# copy node-red project files into place
COPY ./src/project/flows.json /data/flows.json
#COPY flows_cred.json /data/flows_cred.json
COPY ./src/project/settings.js /data/settings.js


# copy package.json to the WORKDIR so npm builds for node-red
COPY ./src/environment/package.json .

RUN npm install -C /usr/src/node-red/node_modules/node-red-contrib-uibuilder vue bootstrap vue-bootstrap 

#RUN cat /etc/hosts
RUN npm install --unsafe-perm --no-update-notifier --no-audit ---omit=dev

CMD ["node-red", "--userDir", "/data", "--flows", "/data/flows.json"]