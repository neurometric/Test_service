FROM node:16-alpine3.15 AS build
WORKDIR /app
COPY package*.json ./ 
RUN npm install && npm cache clean --force 
COPY . .
RUN npm run ng build

FROM nginx:1.28.0-alpine
COPY --from=build /app/dist/frontend /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf 
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]