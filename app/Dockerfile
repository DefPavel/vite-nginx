FROM node:20.11-alpine as development

WORKDIR /var/www/app

COPY package*.json .

RUN npm install

COPY . .

RUN npm run build

FROM nginx:stable-alpine as production

COPY --from=development /var/www/app/dist /usr/share/nginx/html

COPY nginx.conf /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]
