FROM debian

RUN apt-get update -y && apt-get upgrade -y && \
	apt-get install bzip2 wget -y && \
	wget http://dl.4players.de/ts/releases/3.4.0/teamspeak3-server_linux_amd64-3.4.0.tar.bz2 && \
	bunzip2 *.bz2 && \
	tar -xvf *.tar

ENTRYPOINT ["sh", "teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh"]

CMD ["license_accepted=1"]
