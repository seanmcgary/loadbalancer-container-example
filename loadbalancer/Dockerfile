FROM fedora:21

# install haproxy
RUN yum makecache fast
RUN yum install -y haproxy.x86_64

# enable it so that it starts on boot
RUN systemctl enable haproxy.service

# download the pre-compiled confd binary
RUN curl -L https://github.com/kelseyhightower/confd/releases/download/v0.9.0/confd-0.9.0-linux-amd64 > /usr/local/bin/confd
RUN chmod +x /usr/local/bin/confd

# add our confd directory to /etc
ADD confd /etc/

# add and enable our confd unit file
ADD confd.service /etc/systemd/system/
RUN systemctl enable confd.service