FROM ubuntu:latest
RUN apt update -y && apt install nginx -y
EXPOSE 80
Add index.html /var/www/html
CMD ["nginx","-g","daemon off;"]

