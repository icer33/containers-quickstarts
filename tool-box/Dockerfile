FROM fedora:latest

ENV OC_CLIENT_MIRROR https://mirror.openshift.com/pub/openshift-v3/clients/3.11.98/linux/oc.tar.gz
ENV HOME /home/tool-box

RUN dnf -y update && \
    INSTALL_PKGS="git tree vim unzip python-pip jq origin-clients" && \
    dnf -y install $INSTALL_PKGS && \
    dnf clean all && \
    mkdir -m 775 $HOME && \
    chmod 775 /etc/passwd && \
    pip install git+https://github.com/ansible/ansible.git@stable-2.6

WORKDIR $HOME

ADD ./root /

RUN chmod u+x /usr/local/bin/run

USER 1001

ENTRYPOINT ["/usr/local/bin/run"]
CMD ["sleep", "infinity"]
