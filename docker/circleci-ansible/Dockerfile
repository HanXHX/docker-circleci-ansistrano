FROM cimg/python:3.9

USER root

RUN apt-get update && sudo apt-get install -y git rsync && \
    pip3 install ansible pycrypto cryptography && \
    apt-get autoremove -y && \
	rm -rf /var/cache/apt/*

USER circleci

RUN ansible-galaxy install ansistrano.deploy ansistrano.rollback

CMD ["/bin/sh"]
