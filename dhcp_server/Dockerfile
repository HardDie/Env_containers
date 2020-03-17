# docker build -t my/dhcp_server .
#
# dhcp_server() {
# 	docker run --rm -d \
# 		--net host \
# 		--name dhcp_server \
# 		my/dhcp_server
# }

FROM networkboot/dhcpd

COPY dhcpd.conf /data/dhcpd.conf

ENTRYPOINT [ "/entrypoint.sh" ]
