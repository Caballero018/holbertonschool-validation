FROM alpine:3.13
WORKDIR /app
COPY ./dist/ ./dist/
COPY ./awesome-api .
# hadolint ignore=DL3018,DL3019
RUN apk add gcompat
ENTRYPOINT [ "/app/awesome-api" ]