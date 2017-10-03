FROM alpine:3.1

# Update
RUN apk add --update nodejs

# Install app dependencies
COPY package.json /src/package.json
RUN cd /src; sudo apt-get install npm 

# Bundle app source
COPY . /src

EXPOSE  8080
CMD ["node", "/src/index.js"]

