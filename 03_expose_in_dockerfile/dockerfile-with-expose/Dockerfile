FROM ubuntu
ENTRYPOINT ["tail", "-f", "/dev/null"]
RUN apt-get update && apt-get install -y nginx
RUN apt-get install -y curl
EXPOSE 80
