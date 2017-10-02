FROM alpine:3.1

# Update
RUN apk add --update nodejs

# Install app dependencies
COPY package.json src/package.json

# Create a nonroot user, and switch to it
RUN /usr/sbin/useradd --create-home --home-dir /usr/local/nonroot --shell /bin/bash nonroot
RUN /usr/sbin/adduser nonroot sudo
RUN chown -R nonroot /usr/local/
RUN chown -R nonroot /usr/lib/
RUN chown -R nonroot /usr/bin/
RUN chown -R nonroot /src

RUN /bin/su nonroot

# Install app source
RUN cd /src; npm install

# Bundle app source
COPY . /src

EXPOSE  8080
CMD ["node", "/src/index.js"]


