FROM ubuntu:18.04

WORKDIR /root

# Install any needed packages specified in requirements.txt
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install apt-utils git-core curl -y
RUN git clone https://github.com/lab10-coop/sigma1 && \
    cd sigma1  && \
    ./download-parity.sh

RUN apt-get install net-tools -y

# Make port 80 available to the world outside this container
EXPOSE 40303
EXPOSE 8545
EXPOSE 8546

# Define environment variable
#ENV NAME World
WORKDIR /root/sigma1

VOLUME /root/sigma1/data

# Run app.py when the container launches
ENTRYPOINT ./parity -c node.toml --port=40303 --jsonrpc-interface=all --ws-interface=all $EXTRA_OPTS
#CMD ["/bin/sh"]