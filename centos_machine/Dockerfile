FROM centos:7

RUN yum -y install openssh-server

RUN useradd machine_1 && \
 echo "1234" | passwd machine_1 --stdin && \
 mkdir /home/machine_1/.ssh && \
 chmod 700 /home/machine_1/.ssh

COPY secret.pub /home/machine_1/.ssh/authorized_keys

RUN chown machine_1:machine_1 -R /home/machine_1/.ssh/ && \
 chmod 600 /home/machine_1/.ssh/authorized_keys

RUN ssh-keygen -A 

CMD /usr/sbin/sshd -D