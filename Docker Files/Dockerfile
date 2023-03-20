# Use an official Node.js runtime as a parent image
FROM node:18

#proxy settings
ENV http_proxy http://rb-proxy-de.bosch.com:8080
ENV https_proxy http://rb-proxy-de.bosch.com:8080


# Install Node-RED and uibuilder
RUN npm install -g --unsafe-perm node-red node-red-contrib-alasql node-red-contrib-config node-red-contrib-fs node-red-contrib-moment node-red-contrib-spreadsheet-in node-red-contrib-statistics node-red-contrib-uibuilder node-red-dashboard node-red-node-email node-red-contrib-fs-ops node-red-contrib-safe-queue node-red-node-mysql node-red-contrib-json-schema-validator node-red-contrib-modbus node-red-contrib-zip node-red-contrib-image-tools node-red-contrib-batcher node-red-contrib-influxdb node-red-contrib-watchdirectory node-red-node-ping node-red-contrib-excelsheets node-red-contrib-mssql node-red-contrib-spreadsheet-in node-red-contrib-ui-upload node-red-contrib-opcua
RUN npm install -C /usr/src/node-red/node_modules/node-red-contrib-uibuilder vue bootstrap vue-bootstrap 

COPY settings.js /data/settings.js
COPY flows_cred.json /data/flows_cred.json
COPY flows.json /data/flows.json
# Expose the port used by Node-RED (default is 1880)
EXPOSE 1880

# Set the working directory to /user/src/node-red
WORKDIR /usr/src/node-red

# Start Node-RED with uibuilder
CMD ["node-red", "--userDir", "/data", "--flows", "/data/flows.json"]
