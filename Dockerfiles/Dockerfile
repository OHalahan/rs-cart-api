# Base node image
FROM node:12-alpine AS base
LABEL Name="cart-api-build"
LABEL Version="0.0.1"
WORKDIR /app

# Dependencies
FROM base AS dependencies
COPY package*.json ./
RUN npm install && npm cache clean --force

# Copy filed and build
FROM dependencies AS build
LABEL Name="chart-api-deploy"
LABEL Version="0.0.1"
WORKDIR /app
COPY . .
RUN npm run build

WORKDIR /app

USER node
ENV PORT=8080
EXPOSE 8080

CMD ["npm", "run", "start:prod"]
