HOST = $(shell hostname -s)
REGISTRY_URI ?= nexus.instantlinux.net
SERVICES = dhcpd-dns-pxe etcd mt-daapd mythtv-backend ntpd nut-upsd samba \
    samba-dc weewx

# Before starting etcd, see notes in etcd/docker-compose.yml.

default: $(HOST)

mckinley: dhcpd-dns-pxe etcd mt-daapd mythtv-backend ntpd nut-upsd weewx
vinson: dhcpd-dns-pxe etcd mt-daapd samba-dc
denali: dhcpd-dns-pxe etcd nut-upsd samba

$(SERVICES)::
	@echo Starting $@
	@if [ $@ != "etcd" ] && [ $@ != 'ntpd' ]; then \
           docker pull $(REGISTRY_URI)/$@:latest; \
        fi
	cd $@ ; docker-compose up -d
