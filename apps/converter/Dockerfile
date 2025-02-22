FROM node:14-alpine as build
WORKDIR /opt/app
ADD *.json ./
RUN npm install
RUN npm install @babel/core@^7.16.0  # Установить нужную версию babel
ADD . .
RUN npm run build converter

FROM node:14-alpine
WORKDIR /opt/app
ADD package.json ./
RUN npm install --only=prod
COPY --from=build /opt/app/dist/apps/converter ./dist
CMD ["node", "./dist/main.js"]