include $(TOPDIR)/rules.mk

PKG_NAME:=kodo-kernel-network
PKG_VERSION:=2014-05-22
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=66252cad8cc1603325b340c9395ae15199e81be3

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
  FILES:=$(PKG_BUILD_DIR)/module/kodo-network.$(LINUX_KMOD_SUFFIX)
  AUTOLOAD:=$(call AutoLoad,50,kodo-network)
endef

MAKE_FLAGS += \
	KERNELPATH="$(LINUX_DIR)" \
	FIFIPATH="$(STAGING_DIR)/usr/include/kernel/kfifi" \
	KODOPATH="$(STAGING_DIR)/usr/include/kernel/kodo"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/module/ $(MAKE_FLAGS) all
endef

$(eval $(call KernelPackage,kodo-network))
