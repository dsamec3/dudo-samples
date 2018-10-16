FROM 172.30.1.1:5000/myproject/wlp-centos:dudo

# Add binary deployment artifact to 'dropins' folder
# RUN wget --directory-prefix=/opt/ibm/wlp/usr/servers/defaultServer/dropins/ $BINARY_DEPLOYMENT_ARTIFACT_URL
# COPY jvm.options /config/jvm.options
COPY bootstrap.properties /config/bootstrap.properties
COPY usr/ /opt/ibm/wlp/usr/
COPY app/* /opt/ibm/wlp/usr/servers/defaultServer/dropins/

# IBM WebSphere Liberty license must be accepted
ENV LICENSE $LICENSE

USER 1001

