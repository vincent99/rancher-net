FROM rancher/agent-base:v0.2.0
ENV CNI v0.3.0-rancher4

ADD strongswan.tar.gz /
RUN mkdir -p /opt/cni/bin /etc/cni/net.d && \
    curl -sfSL https://github.com/rancher/cni/releases/download/${CNI}/cni-${CNI}.tar.gz | \
       tar xvzf - -C /tmp ./bridge ./loopback \
    && mkdir -p /opt/cni/bin \
    && mv /tmp/bridge /opt/cni/bin/rancher-bridge \
    && mv /tmp/loopback /opt/cni/bin/loopback && \
    curl -sfSL https://github.com/rancher/rancher-cni-ipam/releases/download/v0.1.0/rancher-cni-ipam.tar.gz | \
    tar xvzf - -C /opt/cni/bin

COPY start.sh start-vxlan.sh rancher-net /usr/bin/
CMD ["start.sh"]
