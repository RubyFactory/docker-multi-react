FROM node:alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 3000
COPY --from=builder /app/build /user/share/nginx/html