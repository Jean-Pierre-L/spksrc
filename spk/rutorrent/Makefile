SPK_NAME = rutorrent
SPK_VERS = 3.6
SPK_REV = 6
SPK_ICON = src/rutorrent.png
DSM_UI_DIR = app

DEPENDS  = cross/rtorrent cross/rutorrent cross/rutorrent-plugins cross/busybox cross/screen cross/procps-ng cross/mediainfo

MAINTAINER = SynoCommunity
DESCRIPTION = ruTorrent is a front-end for the popular Bittorrent client rTorrent. rTorrent is a BitTorrent client for ncurses, using the libtorrent library. The client and library is written in C++ with emphasis on speed and efficiency, while delivering equivalent features to those found in GUI based clients in an ncurses client.
ADMIN_URL = /rutorrent/
RELOAD_UI = yes
STARTABLE = yes
DISPLAY_NAME = ruTorrent
CHANGELOG = "1. DSM 5.0 compatibility"
BETA = 1

HOMEPAGE   = http://code.google.com/p/rutorrent/
LICENSE    = GPLv3

WIZARDS_DIR = src/wizard/

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh

INSTALL_DEP_SERVICES = apache-web
START_DEP_SERVICES = apache-web
INSTUNINST_RESTART_SERVICES = apache-web

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = rutorrent_extra_install

BUSYBOX_CONFIG = usrmng daemon nice
ENV += BUSYBOX_CONFIG="$(BUSYBOX_CONFIG)"

include ../../mk/spksrc.spk.mk

.PHONY: rutorrent_extra_install
rutorrent_extra_install:
	install -m 755 -d $(STAGING_DIR)/var
	install -m 644 src/.rtorrent.rc $(STAGING_DIR)/var/
	install -m 755 -d $(STAGING_DIR)/var/.session
	install -m 755 -d $(STAGING_DIR)/etc
	install -m 644 src/cacert.pem $(STAGING_DIR)/etc/
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48 72; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
