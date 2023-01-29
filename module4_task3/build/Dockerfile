FROM golang:1.15.8-buster
# hadolint ignore=DL3008,DL3009,DL3015
RUN apt-get update && apt-get install -y make wget curl
# hadolint ignore=DL3047
RUN wget https://github.com/gohugoio/hugo/releases/download/v0.109.0/hugo_extended_0.109.0_linux-amd64.deb
# hadolint ignore=DL3059
RUN dpkg -i hugo_extended_0.109.0_linux-amd64.deb
# hadolint ignore=DL3059
RUN rm -f hugo_extended_0.109.0_linux-amd64.deb
# hadolint ignore=DL3008,DL3015,DL4001,DL4006
RUN curl -fsSL https://deb.nodesource.com/setup_19.x | bash - && apt-get install -y nodejs
# hadolint ignore=DL3016
RUN npm install -g markdownlint-cli
# hadolint ignore=DL3016,DL3059
RUN npm install -g markdown-link-check
