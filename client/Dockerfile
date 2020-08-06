FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
RUN rm /usr/share/nginx/html/*
RUN rm  /etc/nginx/conf.d/default.conf
RUN (cd  /etc/nginx/conf.d/) && (ls -lrt)
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html