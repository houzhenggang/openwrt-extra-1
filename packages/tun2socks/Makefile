include $(TOPDIR)/rules.mk

PKG_NAME:=tun2socks
PKG_VERSION:=1.999.130.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_URL:=https://github.com/ravageralpha/badvpn/releases/download/$(PKG_VERSION)
PKG_SOURCE:=badvpn-$(PKG_VERSION).tar.gz
PKG_MD5SUM:=b784ea6d284d24b9fba2495d3c52dae3
	
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/badvpn-$(PKG_VERSION)

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS=-DBUILD_TUN2SOCKS=1 \
	-DBUILD_NOTHING_BY_DEFAULT=1 \
	-DCMAKE_BUILD_TYPE=Release

define Package/tun2socks/Default
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=tun2socks
  DEPENDS:=+kmod-tun +ip +librt
endef

define Package/tun2socks
  $(call Package/tun2socks/Default)
endef

define Package/tun2socks/description
tun2socks - the title said all
endef

define Package/tun2socks/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/tun2socks
endef

$(eval $(call BuildPackage,tun2socks))
