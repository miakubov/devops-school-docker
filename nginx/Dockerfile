FROM nginx:1.21

COPY ./nginx.conf /etc/nginx/conf.d/nginx.conf
EXPOSE 8085

ENTRYPOINT ["nginx", "-g", "daemon off;"]
