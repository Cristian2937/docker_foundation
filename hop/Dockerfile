FROM openjdk:11-jre-slim

WORKDIR /opt/hop
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    libgtk-3-0 \
    libx11-xcb1 \
    libxtst6 \
    libxrender1 \
    libxi6 \
    libfreetype6 \
    libxext6 \
    libwebkit2gtk-4.0-37 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://archive.apache.org/dist/hop/2.9.0/apache-hop-client-2.9.0.zip \
    && unzip apache-hop-client-2.9.0.zip -d /opt/hop \
    && rm apache-hop-client-2.9.0.zip


# Imposta la variabile di ambiente
ENV HOP_CONFIG_FOLDER=/opt/hop/hop/config_host
ENV HOP_HOME=/opt/hop/
ENV GDK_BACKEND=x11
ENV GDK_SYNCHRONIZE=1

# Imposta le opzioni Hop per aumentare la memoria heap massima
ENV HOP_OPTIONS="-Xms512m -Xmx4g"

EXPOSE 8080
ENTRYPOINT ["/opt/hop/hop/hop-gui.sh"]
