#
# Copyright (C) 2013 Francisco Borges
# Copyright (C) 2011-2018 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Makefile taken from http://github.com/FranciscoBorges/openwrt-printing-packages

include $(TOPDIR)/rules.mk

PKG_NAME:=qpdf
PKG_VERSION:=8.2.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)
PKG_HASH:=f445d3ebda833fe675b7551378f41fa1971cc6f7a7921bbbb94d3a71a404abc9

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/qpdf
	SECTION:=utils
	CATEGORY:=Utilities
	DEPENDS:=+libjpeg +libpcre +zlib +libstdcpp
	TITLE:=PDF transformations utility
	URL:=http://qpdf.sourceforge.net/
	MAINTAINER:=Entware team, https://entware.net
endef

define Package/qpdf/description
 QPDF is a command-line program for transformations on PDF files.
endef

CONFIGURE_ARGS += \
	--with-random=/dev/urandom

define Package/qpdf/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/{qpdf,zlib-flate} $(1)/opt/bin
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libqpdf.so* $(1)/opt/lib
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/opt/include
	$(CP) $(PKG_INSTALL_DIR)/opt/include/qpdf $(1)/opt/include
	$(INSTALL_DIR) $(1)/opt/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/libqpdf.so* $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/opt/lib/pkgconfig/libqpdf.pc $(1)/opt/lib/pkgconfig
endef

$(eval $(call BuildPackage,qpdf))
