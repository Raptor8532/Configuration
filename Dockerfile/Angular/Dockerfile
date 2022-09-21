#Stage 1
FROM node:16.15-alpine3.15 as build
# Create app directory
WORKDIR /app
#COPY package*.json  /app/
COPY ./ /app/
RUN npm install -g npm@8.5.5
RUN npm install -g @angular/cli
RUN npm ci
RUN npm run build

#Stage 2
FROM nginx:alpine
COPY --from=build /app/dist/ /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
