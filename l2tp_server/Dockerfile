# docker build -t my/l2tp_server .
#
# l2tp_server() {
# 	docker run --rm -d \
# 		--privileged \
# 		--net host \
# 		--name l2tp_server \
# 		my/l2tp_server
# }

FROM ubuntu:latest

RUN apt-get update && apt-get -y install xl2tpd

RUN mkdir /var/run/xl2tpd

COPY xl2tpd.conf /etc/xl2tpd/xl2tpd.conf
COPY chap-secrets /etc/ppp/chap-secrets
COPY options.l2tpd /etc/ppp/options.l2tpd

ENTRYPOINT [ "xl2tpd" ]
CMD [ "-Dv" ]
