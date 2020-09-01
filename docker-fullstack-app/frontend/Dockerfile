FROM node:alpine as builder
WORKDIR /app
COPY ./package*.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx
EXPOSE 3000
# default 설정 복사
COPY nginx ./etc/nginx/conf.d/default.conf
# build된 파일 옮기기
COPY --from=builder /app/build /usr/share/nginx/html