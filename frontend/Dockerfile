# Dockerfile for React Frontend
FROM node:16-alpine AS build

# Install git
RUN apk add --no-cache git

WORKDIR /app
COPY package.json ./
COPY package-lock.json ./
RUN npm install
COPY . ./
RUN npm run build

FROM nginx:alpine
#vite uses /app/dist NOT /app/build
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
