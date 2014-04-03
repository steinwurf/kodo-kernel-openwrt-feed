include $(TOPDIR)/rules.mk

PKG_NAME:=kodo-kernel-network
PKG_VERSION:=2014-04-02
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=64d3e74fab04028620256544b8cd7f65a53ff24a

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:steinwurf-internal/kodo-kernel-network.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define KernelPackage/kodo-network
  SUBMENU:=Network Support
  TITLE:=Kodo inside the network stack
  DEPENDS:=+kmod-kfifi +kmod-kodo
  FILES:=$(PKG_BUILD_DIR)/kodo-network.$(LINUX_KMOD_SUFFIX)
  AUTOLOAD:=$(call AutoLoad,50,kodo-network)
endef

MAKE_FLAGS += \
	KERNELPATH="$(LINUX_DIR)" \
	FIFIPATH="$(STAGING_DIR)/usr/include/kernel/kfifi" \
	KODOPATH="$(STAGING_DIR)/usr/include/kernel/kodo"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/ $(MAKE_FLAGS) all
endef

$(eval $(call KernelPackage,kodo-network))
