FROM alpine:latest AS build
RUN apk add git wget curl unzip python3
ENV TF_RELEASE="0.15.5"
WORKDIR /tmp
RUN wget "https://releases.hashicorp.com/terraform/${TF_RELEASE}/terraform_${TF_RELEASE}_linux_amd64.zip"
RUN unzip "terraform_${TF_RELEASE}_linux_amd64.zip" && rm "terraform_${TF_RELEASE}_linux_amd64.zip" && mv -v terraform /usr/bin/terraform
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip "awscliv2.zip"
RUN ./aws/install -i /usr/local/aws-cli -b /usr/local/bin
RUN mkdir -pv /apps
WORKDIR /apps
COPY build/alpine/. .
RUN git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
WORKDIR /apps/learn-terraform-provision-eks-cluster
RUN /usr/bin/terraform init -upgrade

