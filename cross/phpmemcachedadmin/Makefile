PKG_NAME = phpmemcachedadmin
PKG_EXT = tar.gz
PKG_GIT_HASH = aaf3d16a2a1e3dff72dd358f1758d96f0f174cb3
PKG_DIST_NAME = $(PKG_GIT_HASH).$(PKG_EXT)
PKG_DIST_SITE = https://github.com/elijaa/phpmemcachedadmin/archive
PKG_DIST_FILE = $(PKG_NAME)-$(PKG_GIT_HASH).$(PKG_EXT)
PKG_DIR = phpmemcachedadmin-$(PKG_GIT_HASH)

# Unfortunately only version 1.3.0 is officially released, but
# we need the commit aaf3d16 of 12 Jun 2020 for memcached 1.6.x
# Issue #19: fix mem_requested key change in Memcached 1.5.17

DEPENDS =

HOMEPAGE = https://github.com/elijaa/phpmemcachedadmin
COMMENT  = Graphic stand-alone administration for memcached to monitor and debug purpose.
LICENSE  = Apache 2.0

EXTRACT_PATH = $(WORK_DIR)
INSTALL_TARGET = phpmemcachedadmin_install

include ../../mk/spksrc.install-resources.mk

CONFIG_FOLDER = var/phpmemcachedadmin.config

.PHONY: phpmemcachedadmin_install
# link the Config folder into var for backup/restore on package update
# and for on demand creation of the default config on DSM 7.
phpmemcachedadmin_install:
	@$(MSG) "Extract web app to folder: share/$(PKG_NAME)"
	@mkdir -p $(STAGING_INSTALL_PREFIX)/share/$(PKG_NAME)
	@tar -cf - -C $(WORK_DIR)/$(PKG_DIR) --exclude Config . | tar -xf - -C $(STAGING_INSTALL_PREFIX)/share/$(PKG_NAME)
	@$(MSG) "Install config to folder: $(CONFIG_FOLDER)"
	@install -d -m 755 $(STAGING_INSTALL_PREFIX)/$(CONFIG_FOLDER)
	@install -m 755 $(WORK_DIR)/$(PKG_DIR)/Config/* $(STAGING_INSTALL_PREFIX)/$(CONFIG_FOLDER)/
	@cd $(STAGING_INSTALL_PREFIX)/share/$(PKG_NAME) && ln -sf $(INSTALL_PREFIX_VAR)/phpmemcachedadmin.config Config
