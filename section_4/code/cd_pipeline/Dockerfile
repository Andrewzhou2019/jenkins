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

USER root

SHELL ["/bin/bash", "-c"]
RUN echo $SHELL

RUN ls /usr/sbin

RUN /usr/sbin/usermod -aG docker jenkins && \
    /usr/sbin/usermod -aG root jenkins && \
    /bin/chmod 644 /var/run/docker.sock

USER jenkins

# Run the application
CMD ["python3", "/usr/src/app/app.py"]
