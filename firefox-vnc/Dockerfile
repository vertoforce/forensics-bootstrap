# Taken from https://github.com/creack/docker-firefox/blob/master/Dockerfile
# with a few changes

# Firefox over VNC
#
# VERSION               0.1
# DOCKER-VERSION        0.2

FROM	debian:sid

RUN	apt-get update

# Install vnc, xvfb in order to create a 'fake' display and firefox
RUN	apt-get install -y x11vnc xvfb firefox
RUN	mkdir /root/.vnc
# Setup a password
RUN	x11vnc -storepasswd 1234 /root/.vnc/passwd
# Autostart firefox (might not be the best way to do it, but it does the trick)
RUN	bash -c 'echo "firefox" >> /root/.bashrc'

CMD x11vnc -forever -usepw -create