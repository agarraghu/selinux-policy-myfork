# -*- Mode: makefile; indent-tabs-mode: t -*-
# SPDX-FileCopyrightText: © 2021 Dominick Grift <dominick.grift@defensec.nl>
# SPDX-License-Identifier: Unlicense

include $(TOPDIR)/rules.mk

PKG_NAME:=selinux-policy-XXXX
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://XXXX/selinux-policy-XXXX.git
PKG_SOURCE_DATE:=XXXX-XX-XX
PKG_SOURCE_VERSION:=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
# use 'make package/selinux-policy-XXXX/check V=s' to generate, or 'skip'
PKG_MIRROR_HASH:=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
PKG_BUILD_DEPENDS:=secilc/host policycoreutils/host

PKG_LICENSE:=Unlicense
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=XXXX <XXXX@XXXX>
PKG_CPE_ID:=cpe:/a:XXXX:selinux-policy-XXXX

include $(INCLUDE_DIR)/package.mk

define Package/selinux-policy-XXXX
	SECTION:=system
	CATEGORY:=Base system
	TITLE:=XXXX SELinux policy for OpenWrt
	URL:=https://XXXX/
	PKGARCH:=all
endef

define Package/selinux-policy-XXXX/description
	XXXX SELinux security policy designed specifically for OpenWrt
	and written in Common Intermediate Language.
endef

define Build/Compile
#       Do stuff here, for example change tunable defaults
#       sed -i 's/true)/false)/' $(PKG_BUILD_DIR)/src/selinuxbool/loadpolicyselinuxbool.cil
#       sed -i 's/true)/false)/' $(PKG_BUILD_DIR)/src/selinuxbool/volatileoverlayselinuxbool.cil
	$(call Build/Compile/Default,policy)
endef

define Package/selinux-policy-XXXX/conffiles
/etc/selinux/config
endef

define Package/selinux-policy-XXXX/install
	$(INSTALL_DIR) $(1)/etc/selinux/$(PKG_NAME)/contexts/files/
	$(INSTALL_DIR) $(1)/etc/selinux/$(PKG_NAME)/policy/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/customizable_types $(1)/etc/selinux/$(PKG_NAME)/contexts/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/file_contexts.subs_dist $(1)/etc/selinux/$(PKG_NAME)/contexts/files/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/file_contexts $(1)/etc/selinux/$(PKG_NAME)/contexts/files/
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/policy.* $(1)/etc/selinux/$(PKG_NAME)/policy/
	$(INSTALL_DATA) ./files/selinux-config $(1)/etc/selinux/config
endef

$(eval $(call BuildPackage,selinux-policy-XXXX))
