# Stage 1: Build the React application
FROM node:15.6.0-alpine3.10 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Create the production image
FROM nginx:1.19.6
WORKDIR /usr/share/nginx/html
COPY --from=build /app/build .
RUN chown -R nginx:nginx /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]