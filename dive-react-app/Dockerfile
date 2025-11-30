# Stage 1: Build Stage
FROM node:22.21.0-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5173
RUN npm run build
# Stage 2: Production Stage
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
