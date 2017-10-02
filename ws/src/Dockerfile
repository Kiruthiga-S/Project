FROM alpine:3.1

# Update
RUN apk add --update nodejs

# Install app dependencies
COPY package.json src/package.json

# Create a nonroot user, and switch to it
RUN /usr/sbin/useradd --create-home --home-dir /usr/local/nonroot --shell /bin/bash nonroot 

RUN chown -R nonroot /src

# Switch to our nonroot user
USER nonroot

# Set the HOME var, npm install gets angry if it can't write to the HOME dir, 
# which will be /root at this point
ENV HOME /usr/local/nonroot

# Install app source
WORKDIR /src
RUN npm install

# Bundle app source
COPY . /src

EXPOSE  8080
CMD ["node", "/src/index.js"]


