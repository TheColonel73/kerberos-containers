FROM debian

EXPOSE 749 88 22

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -qq update
RUN apt-get -qq install locales krb5-kdc krb5-admin-server
RUN apt-get -qq install openssh-server
RUN apt-get -qq install vim 
RUN apt-get -qq clean

ENV REALM ${REALM:-EXAMPLE.COM}
ENV SUPPORTED_ENCRYPTION_TYPES ${SUPPORTED_ENCRYPTION_TYPES:-aes256-cts-hmac-sha1-96:normal}
ENV KADMIN_PRINCIPAL ${KADMIN_PRINCIPAL:-kadmin/admin}
ENV KADMIN_PASSWORD ${KADMIN_PASSWORD:-adminpassword}

COPY init-script.sh /tmp/
COPY sshd_config /etc/ssh/sshd_config
CMD /tmp/init-script.sh

