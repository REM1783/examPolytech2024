FROM node:10 as builder

WORKDIR /app

COPY . .

RUN npm install 

RUN npm run build

FROM nginx

LABEL maintainer="remy"

COPY nginx/ /etc/nginx/

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh

RUN chmod +x /docker-entrypoint.d/entrypoint.sh

COPY --from=builder /app/dist/* /usr/share/nginx/html


