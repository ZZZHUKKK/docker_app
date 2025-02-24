FROM node:14-alpine as build
WORKDIR /opt/app
ADD *.json ./
RUN npm install
RUN npm install @babel/core@^7.16.0
ADD . .
RUN npm run build api

FROM node:14-alpine
WORKDIR /opt/app
ADD package.json ./
RUN npm install --only=prod
COPY --from=build /opt/app/dist/apps/api ./dist
CMD ["node", "./dist/main.js"]