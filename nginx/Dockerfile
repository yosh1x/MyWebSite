FROM nginx:latest

RUN apt-get update && apt-get install -y curl

RUN curl -LO https://github.com/nginxinc/nginx-prometheus-exporter/releases/download/v1.0.0/nginx-prometheus-exporter_1.0.0_linux_amd64.tar.gz && \
    tar -xzf nginx-prometheus-exporter_1.0.0_linux_amd64.tar.gz && \
    mv nginx-prometheus-exporter /usr/bin/nginx-prometheus-exporter && \
    chmod +x /usr/bin/nginx-prometheus-exporter && \
    rm nginx-prometheus-exporter_1.0.0_linux_amd64.tar.gz

COPY index.html /usr/share/nginx/html/

EXPOSE 80

EXPOSE 9113

CMD ["nginx", "-g", "daemon off;"]
CMD ["nginx-prometheus-exporter", "--nginx.scrape-uri", "http://localhost/stub_status"]

