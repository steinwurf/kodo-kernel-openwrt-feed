include $(TOPDIR)/rules.mk

PKG_NAME:=kodo-kernel-module
PKG_VERSION:=2014-05-23
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=a24597124a8e78a9cf71b456fb3e024dfc082c71

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:steinwurf-internal/kodo-kernel-module.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define KernelPackage/kodo
  SUBMENU:=Libraries
  TITLE:=Network Coding Algorithms
  DEPENDS:=+kmod-kfifi
  FILES:=$(PKG_BUILD_DIR)/module/kodo.$(LINUX_KMOD_SUFFIX)
  AUTOLOAD:=$(call AutoLoad,11,kodo)
endef

MAKE_FLAGS += \
	KERNELPATH="$(LINUX_DIR)" \
	FIFIPATH="$(STAGING_DIR)/usr/include/kernel/kfifi"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/module/ $(MAKE_FLAGS) all
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/kernel/kodo/
	$(CP) $(PKG_BUILD_DIR)/module/include $(1)/usr/include/kernel/kodo/
endef

$(eval $(call KernelPackage,kodo))
