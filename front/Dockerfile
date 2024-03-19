FROM node:12-alpine AS build
RUN apk add --no-cache git
RUN git clone https://github.com/Nyzzh/doodlestudent.git
WORKDIR /doodlestudent/front
RUN npm install
RUN npm run build

FROM nginx:1-alpine
COPY --from=build /doodlestudent/front/dist/tlcfront /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
