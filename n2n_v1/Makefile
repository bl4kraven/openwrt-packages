#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.


include $(TOPDIR)/rules.mk

PKG_NAME:=n2n
PKG_VERSION:=1.3.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/meyerd/n2n
PKG_SOURCE_VERSION:=d24fd5262f1a38bada6e836369cc31612b5b7607
PKG_MIRROR_HASH:=77d77c0b6dd69a96376511e2d1c5ab49d0bd041b67250a50f601108f301fe90a

include $(INCLUDE_DIR)/package.mk

define Package/n2n
  SECTION:=net
  CATEGORY:=Network
  TITLE:=VPN tunneling daemon
  DEPENDS:=+libpthread +kmod-tun
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/n2n_v1 $(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)" LDFLAGS="$(TARGET_LDFLAGS)" INSTALL_PROG=":"
endef

define Package/n2n/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d/

	$(INSTALL_BIN) ./files/n2n.init $(1)/etc/init.d/n2n
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/n2n_v1/edge $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,n2n))
