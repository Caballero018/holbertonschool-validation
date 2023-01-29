FROM golang:1.15.8-buster
RUN apt-get update && apt-get install -y make wget curl
RUN wget https://github.com/gohugoio/hugo/releases/download/v0.109.0/hugo_extended_0.109.0_linux-amd64.deb
RUN dpkg -i hugo_extended_0.109.0_linux-amd64.deb
RUN rm -f hugo_extended_0.109.0_linux-amd64.deb
RUN curl -fsSL https://deb.nodesource.com/setup_19.x | bash - && apt-get install -y nodejs
RUN npm install -g markdownlint-cli
RUN npm install -g markdown-link-check
