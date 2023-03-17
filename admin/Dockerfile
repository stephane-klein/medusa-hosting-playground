FROM node:18.15.0

WORKDIR /app/admin/

RUN apt-get update -y
RUN apt install -y git
RUN git clone https://github.com/medusajs/admin.git . --depth 1
RUN yarn install
RUN yarn run build

FROM nginx:1.23.3

COPY --from=0 /app/admin/public/ /usr/share/nginx/html/
