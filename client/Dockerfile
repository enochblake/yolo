FROM node:16-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

RUN npm install webpack@latest react-scripts@latest

COPY . .

# RUN npm run build

# FROM nginx:alpine

# COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 3000

# CMD ["nginx", "-g", "daemon off;"]

CMD ["npm", "start"]