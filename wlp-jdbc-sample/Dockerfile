FROM 172.30.1.1:5000/myproject/wlp-centos:dudo

# Add binary deployment artifact to 'dropins' folder
# RUN wget --directory-prefix=/opt/ibm/wlp/usr/servers/defaultServer/dropins/ $BINARY_DEPLOYMENT_ARTIFACT_URL
COPY usr/shared/resources/mysql/* /opt/ibm/wlp/usr/shared/resources/mysql/
COPY usr/servers/defaultServer/* /opt/ibm/wlp/usr/servers/defaultServer/
COPY app/* /opt/ibm/wlp/usr/servers/defaultServer/dropins/

# IBM WebSphere Liberty license must be accepted
ENV LICENSE accept

USER 1001

