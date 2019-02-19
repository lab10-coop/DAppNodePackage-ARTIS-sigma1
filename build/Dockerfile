# Get Sigma1 config and scripts from github
FROM ubuntu:18.04 as builder

WORKDIR /root

RUN apt-get update
RUN apt-get install apt-utils git-core curl -y
RUN git clone https://github.com/lab10-coop/sigma1 && \
    cd sigma1  && \
    ./download-parity.sh

# Pull Parity binary and ARTIS sigma1 config files into new deployment container. 
FROM ubuntu:18.04

EXPOSE 40303
EXPOSE 8545
EXPOSE 8546

RUN mkdir /root/sigma1
COPY --from=builder /root/sigma1/node.toml /root/sigma1
COPY --from=builder /root/sigma1/bootnodes.txt /root/sigma1
COPY --from=builder /root/sigma1/spec.json /root/sigma1
COPY --from=builder /root/sigma1/parity /root/sigma1

WORKDIR /root/sigma1

VOLUME /root/sigma1/data

ENTRYPOINT ./parity -c node.toml --port=40303 --jsonrpc-interface=all --jsonrpc-apis=all --jsonrpc-hosts=all --jsonrpc-cors=all --ws-interface=all --ws-apis=all --ws-origins=all --ws-hosts=all $EXTRA_OPTS