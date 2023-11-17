FROM alpine:latest AS build
RUN apk add git wget curl unzip aws-cli
RUN apk upgrade
ENV TF_RELEASE="1.6.3"
ENV HELM_RELEASE="v3.13.2"
WORKDIR /tmp
RUN wget "https://releases.hashicorp.com/terraform/${TF_RELEASE}/terraform_${TF_RELEASE}_linux_amd64.zip"
RUN unzip "terraform_${TF_RELEASE}_linux_amd64.zip" && rm "terraform_${TF_RELEASE}_linux_amd64.zip" && mv -v terraform /usr/bin/terraform
RUN wget "https://get.helm.sh/helm-${HELM_RELEASE}-linux-amd64.tar.gz" && tar -xzvf "helm-${HELM_RELEASE}-linux-amd64.tar.gz" 
RUN mv -v linux-amd64/helm /usr/bin
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && mv -v kubectl /usr/bin && chmod 755 /usr/bin/kubectl
RUN mkdir -pv /apps
WORKDIR /apps
COPY build/alpine/sample_file.txt .

