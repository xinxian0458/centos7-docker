FROM linker_centos:7

RUN yum -y install openssh-server openssh-clients sudo ntp; yum clean all; mkdir -p /root/.ssh

ADD authorized_keys /root/.ssh/authorized_keys

RUN systemctl enable sshd.service 
#    systemctl enable ntpd.service 

EXPOSE 22

CMD ["/usr/sbin/init"]
