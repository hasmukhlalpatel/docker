FROM node:latest as builder

WORKDIR /app

RUN git clone https://github.com/totaljs/cms.git \
 && cd cms \
 && npm install total.js

COPY . /app

FROM node:latest 

WORKDIR /app
EXPOSE 9000
COPY --from=builder /app/cms .
CMD node debug.js
