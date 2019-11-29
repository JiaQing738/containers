FROM node:latest

## How image is build
# Set environment variables
ENV APP_ROOT=/APP_ROOT
ENV APP_PORT=3000

#create the diectory and cd into
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views

# run some command
RUN npm install

## How an image is provision/run
# what port container will be exposing
EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]

CMD [ "" ]

#add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1