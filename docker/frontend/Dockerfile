FROM node:16 as build-stage

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:alpine

COPY src/nginx.conf /etc/nginx/nginx.conf

COPY --from=build-stage /app/dist/book-network-front /usr/share/nginx/html

EXPOSE 80