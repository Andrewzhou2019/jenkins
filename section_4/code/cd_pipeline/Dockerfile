# base image
FROM alpine:3.7

# Install python 3 and pip
RUN apk add --update python3

# Install Python modules needed by the Python app
COPY requirements.txt /usr/src/app/
RUN pip3 install --no-cache-dir -r /usr/src/app/requirements.txt

# Copy files required for the app to run
COPY app.py /usr/src/app/
COPY templates/index.html /usr/src/app/templates/

# Tell the port number the container should expose
EXPOSE 5000

RUN ls /bin

USER root

RUN ls /usr/sbin

RUN echo "hello"

# Download docker-cli and install it
RUN curl -o docker-ce-cli.deb https://download.docker.com/linux/debian/dists/stretch/pool/stable/amd64/docker-ce-cli_19.03.8~3-0~debian-stretch_amd64.deb && \
    dpkg -i docker-ce-cli.deb && \
    rm docker-ce-cli.deb
    
#RUN /usr/sbin/usermod -aG docker jenkins && \
#    /usr/sbin/usermod -aG root jenkins && \
#    /bin/chmod 644 /var/run/docker.sock

#RUN /usr/sbin/addgroup docker 

#RUN /bin/chgrp docker jenkins 

RUN /bin/chmod 777 /var/run/docker.sock

USER jenkins

# Run the application
CMD ["python3", "/usr/src/app/app.py"]
