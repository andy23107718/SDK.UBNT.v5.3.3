#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 9349 2007-10-18 18:46:37Z blogic $

include $(TOPDIR)/rules.mk

PKG_NAME:=fprobe-ulog
PKG_VERSION:=1.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/fprobe
PKG_MD5SUM:=cdb2e4edc47e8a3d5479eeabfb979ebc

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/fprobe-ulog
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread
  TITLE:=NetFlow probe (ulog-based)
  URL:=http://fprobe.sourceforge.net
endef

define Package/fprobe-ulog/description
	A NetFlow probe obtaining packets through linux netfilter code 
	(iptables ULOG target).
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--with-piddir=/var \
		--with-membulk=index8 \
		--with-hash=xor8 \
	)
endef

define Build/Compile	
	$(MAKE) -C $(PKG_BUILD_DIR)
endef

define Package/fprobe-ulog/install	
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/fprobe-ulog $(1)/usr/bin/
endef

$(eval $(call BuildPackage,fprobe-ulog))
