# Use the latest Ubuntu image as the base
FROM ubuntu:latest

# Set metadata using LABEL
LABEL name="nick-admin" \
      email="nik-r07@live.com"

# Environment variable for the Apache document root
ENV UBUNTU_HOME=/var/www/html/ \
    DEBIAN_FRONTEND=noninteractive

# Install necessary packages in a single RUN command to reduce layers
# and clean up in the same layer to keep the image size down
RUN apt-get update -y && \
    apt-get install -y tzdata apache2 && \
    # Clean up apt cache to reduce image size
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory to UBUNTU_HOME
WORKDIR ${UBUNTU_HOME}

# Copy the index.html file from your local 'environments/script' directory to the container
COPY environments/script/index.html ${UBUNTU_HOME}

# Expose port 80 for the web server
EXPOSE 80

# Use exec form of CMD to run Apache in the foreground
CMD ["apachectl", "-D", "FOREGROUND"]
