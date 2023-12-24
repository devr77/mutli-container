# Production Environment

# Specify a base image
FROM node:alpine as builder

WORKDIR '/app'

# install some dependencies
COPY package*.json ./
RUN npm install

COPY . .

# Default command | build phase
RUN npm run build


FROM nginx:stable-alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY --from=builder /app/nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]



