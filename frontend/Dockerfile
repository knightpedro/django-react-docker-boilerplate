FROM node:12

WORKDIR /usr/src/app/frontend
COPY package.json yarn.lock ./
RUN npm install
COPY . ./