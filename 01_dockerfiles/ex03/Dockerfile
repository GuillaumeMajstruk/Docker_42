FROM ubuntu:16.04

#install dependencies
RUN apt-get update && \
	apt-get install -y curl openssh-server ca-certificates wget && \
	apt-get install -y postfix

#download and install gitlab-ce
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
	chmod 777 script.deb.sh && ./script.deb.sh && \
	apt-get install -y gitlab-ce

#To resolve a known bug about time and zone data
RUN apt update && apt install -y tzdata && \
	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 442 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

#run as --privileged and bind the ports
