FROM node:14.15 as build

WORKDIR /app

COPY package*.json .
RUN yarn install 
COPY . .
RUN yarn run build

FROM nginx:1.19

COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/build /usr/share/nginx/html
