ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.22
FROM ${BUILD_FROM}

RUN apk add --no-cache python3

COPY run.py /run.py

CMD ["python3", "/run.py"]
