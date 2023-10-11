#Using a node alpine image
FROM node:alpine3.18

# setting the working directory
RUN mkdir -p envr/myapp/server
WORKDIR /envr/myapp/server

# Copying the package.json file to the working directory
COPY package*.json envr/myapp/server

# Installing the dependencies
RUN npm install --silent

# Copying the resr of the files to the working directory
COPY . envr/myapp/server

# Running the app
CMD ["npm", "start"]
