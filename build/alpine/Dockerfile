FROM alpine:latest AS build
RUN apk add git wget curl unzip aws-cli
ENV TF_RELEASE="0.15.5"
ENV HELM_RELEASE="v3.6.3"
WORKDIR /tmp
RUN wget "https://releases.hashicorp.com/terraform/${TF_RELEASE}/terraform_${TF_RELEASE}_linux_amd64.zip"
RUN unzip "terraform_${TF_RELEASE}_linux_amd64.zip" && rm "terraform_${TF_RELEASE}_linux_amd64.zip" && mv -v terraform /usr/bin/terraform
RUN curl "https://get.helm.sh/helm-${HELM_RELEASE}-linux-amd64.tar.gz -O && tar -xzvf helm-${HELM_RELEASE}-linux-amd64.tar.gz" && mv -v linux-amd64/helm /usr/bin
RUN mkdir -pv /apps
WORKDIR /apps
COPY build/alpine/. .

#RUN git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
#WORKDIR /apps/learn-terraform-provision-eks-cluster
#RUN /usr/bin/terraform init -upgrade

