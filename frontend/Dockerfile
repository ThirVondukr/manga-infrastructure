FROM node:16-bullseye-slim as build

WORKDIR app

COPY src/package.json src/yarn.lock ./
RUN yarn install

COPY src/ .
COPY environment.prod.ts src/environments/
RUN yarn run build

FROM nginx:latest

COPY --from=build /app/dist/AngularApp /usr/share/nginx/html
COPY nginx.conf /etc/nginx

EXPOSE 80
