FROM node:12.14-alpine AS build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install -g @angular/cli
RUN npm install
COPY . .
RUN npm run build --prod

FROM nginx:latest
COPY --from=build /usr/src/app/dist/client /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 4200