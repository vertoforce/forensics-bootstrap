# Taken from http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/


FROM ubuntu:14.04

RUN apt-get update && apt-get install -y firefox ssh

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer


# Remove root password line
RUN grep -v "PermitRootLogin" /etc/ssh/sshd_config | tee /etc/ssh/sshd_config
RUN echo "\nX11UseLocalhost no" >> /etc/ssh/sshd_config
RUN echo "\nPermitRootLogin yes" >> /etc/ssh/sshd_config
RUN echo "root:firefoxisolated" | chpasswd

# USER developer
# ENV HOME /home/developer
CMD service ssh start && tail -f /dev/null
# /usr/bin/firefox