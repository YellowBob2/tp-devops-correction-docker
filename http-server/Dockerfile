FROM node:12.16.3-stretch-slim AS front-build

WORKDIR /opt/front

COPY devops-front-main/src/ src/
COPY devops-front-main/public/ public/
COPY devops-front-main/package.json .
COPY devops-front-main/yarn.lock .
COPY devops-front-main/babel.config.js .
COPY devops-front-main/.env.production .

RUN npm install
RUN npm run build

FROM httpd:2.4

COPY my-httpd.conf /usr/local/apache2/conf/httpd.conf
COPY --from=front-build /opt/front/dist /usr/local/apache2/htdocs/
