FROM       continuumio/anaconda3:latest
MAINTAINER Dennis Ludl "https://github.com/noboevbo/machine-learning-docker"

RUN apt-get update

RUN conda install -c menpo opencv 

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

#ENV Variables for SSH access
RUN echo "export PATH=${PATH}" >> /root/.bashrc

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]