# Creating base image
FROM node:alpine3.17

# setting the working directory
RUN mkdir -p /envr/myapp/server
WORKDIR /envr/myapp/server

# Copying the package.json files to the working directory
COPY package*.json /envr/myapp/server

# Installing the dependencies
RUN npm install --silent
# RUN npm install react-scripts@3.3.1 -g --silent

# Copying the rest of the files to the working directory
COPY . /envr/myapp/server

EXPOSE 3000

# Running the app
CMD ["npm", "start"]
 