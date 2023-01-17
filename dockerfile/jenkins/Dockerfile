FROM jenkinsci/blueocean:latest
COPY requirs.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/requirs.txt
