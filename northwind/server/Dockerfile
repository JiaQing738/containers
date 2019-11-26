FROM node:latest

## How image is build
# Set environment variables
ENV APP_ROOT=/APP_ROOT DB_HOST='localhost' DB_PORT=3306 DB_USER='root' DB_PASSWORD='changeit' APP_PORT=3000

#create the diectory and cd into
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

# run some command
RUN npm install

## How an image is provision/run
# what port container will be exposing
EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]

HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1