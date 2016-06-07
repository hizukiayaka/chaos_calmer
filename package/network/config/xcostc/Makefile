#
# Copyright (C) 2016-2017 wifiadv.com
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xcostc
PKG_VERSION:=2016-06-07
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@192.168.18.200:Randy/xcostc.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=53f13ec988d4eab0626d83b1ffdb0d3bc08b9d38
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MAINTAINER:=Randy Li <randy@soulik.info>
PKG_LICENSE:=GPLv2


include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xcostc
  SECTION:=net
  CATEGORY:=Base system
  TITLE:=WIFIADV traffic control
  DEPENDS:=+libubox +libuci +kmod-ipt-core +kmod-ipt-conntrack +kmod-ipt-nat +kmod-sched +kmod-sched-core
endef

define Package/xcostc/description
 This package provides a config-compatible C implementation of the UCI firewall.
endef

define Package/xcostc/conffiles
/etc/config/xcostc
endef

TARGET_CFLAGS += -ffunction-sections -fdata-sections
TARGET_LDFLAGS += -Wl,--gc-sections

define Package/xcostc/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/xcostc $(1)/usr/sbin/xcostc
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/xcostc.init $(1)/etc/init.d/xcostc
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_DATA) ./files/xcostc.config $(1)/etc/config/xcostc
endef

$(eval $(call BuildPackage,xcostc))
