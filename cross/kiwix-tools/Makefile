PKG_NAME = kiwix-tools
PKG_VERS = 3.7.0
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = https://github.com/kiwix/kiwix-tools/archive
PKG_DIST_FILE = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

REQUIRED_MIN_DSM = 7.0
UNSUPPORTED_ARCHS = comcerto2k

DEPENDS = cross/libkiwix

HOMEPAGE = https://www.kiwix.org/
COMMENT  = Command line Kiwix tools: kiwix-serve, kiwix-manage, ...
LICENSE  = GPLv3

include ../../mk/spksrc.cross-meson.mk
