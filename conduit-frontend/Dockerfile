
# --- STAGE 1: Build ---
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npx ng build angular-conduit --configuration production

# --- STAGE 2: Run (NGINX) ---
FROM nginx:alpine

COPY --from=build /app/dist/angular-conduit /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
