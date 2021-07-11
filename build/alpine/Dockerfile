FROM alpine:latest AS build
RUN apk add git wget unzip
WORKDIR /tmp
RUN wget https://releases.hashicorp.com/terraform/0.15.5/terraform_0.15.5_linux_amd64.zip -O
RUN unzip "terraform*.zip" && rm "terraform*.zip" && mv -v terraform /usr/bin/terraform
RUN mkdir -pv /apps
WORKDIR /apps
COPY . .

