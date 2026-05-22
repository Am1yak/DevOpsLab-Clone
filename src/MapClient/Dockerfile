FROM node:20-alpine as build
WORKDIR /app

COPY . .
RUN npm install
RUN npm run build

FROM nginx:alpine as runtime
COPY --from=build /app/dist /usr/share/nginx/html
RUN rm -f /usr/share/nginx/html/config.json

EXPOSE 3000
CMD [ "nginx", "-g", "daemon off;" ]