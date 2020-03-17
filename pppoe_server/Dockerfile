# docker build -t my/pppoe_server .
#
# pppoe_server() {
# 	docker run --rm -dt \
# 		--privileged \
# 		--net host \
# 		--name pppoe_server \
# 		my/pppoe_server
# }

FROM ubuntu:latest

RUN apt-get update && apt-get -y install ppp pppoe pppoeconf

COPY allip /etc/ppp/allip
COPY chap-secrets /etc/ppp/chap-secrets
COPY options.pppoe /etc/ppp/options.pppoe

ENTRYPOINT pppoe-server -I ap_wan -L 10.80.1.7 -O /etc/ppp/options.pppoe -p /etc/ppp/allip & bash
