FROM node:16-bullseye-slim AS build

WORKDIR /app

COPY package*.json ./

RUN npm install --legacy-peer-deps

COPY . .

RUN node -v

RUN npm run build

FROM nginx:alpine

COPY --from=build /app/docs /usr/share/nginx/html

EXPOSE 80

CMD ["nginx","-g","daemon off;"]