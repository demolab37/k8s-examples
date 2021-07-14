FROM alpine:latest AS build
RUN apk add git wget curl unzip aws-cli
ENV TF_RELEASE="0.15.5"
WORKDIR /tmp
RUN wget "https://releases.hashicorp.com/terraform/${TF_RELEASE}/terraform_${TF_RELEASE}_linux_amd64.zip"
RUN curl https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 -O
RUN mv -v jq-linux64 /usr/bin/jq
RUN chmod 755 /usr/bin/jq
RUN unzip "terraform_${TF_RELEASE}_linux_amd64.zip" && rm "terraform_${TF_RELEASE}_linux_amd64.zip" && mv -v terraform /usr/bin/terraform
RUN mkdir -pv /apps
WORKDIR /apps
COPY build/alpine/. .
#RUN git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
#WORKDIR /apps/learn-terraform-provision-eks-cluster
#RUN /usr/bin/terraform init -upgrade

