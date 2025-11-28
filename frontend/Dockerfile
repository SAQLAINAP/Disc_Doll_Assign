# Stage 1: Build the Angular application
FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy built artifacts from build stage
# Note: The build output directory is usually dist/<project-name>. 
# Based on package.json name 'angular-15-crud', checking dist/angular-15-crud
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html

# Copy custom Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
