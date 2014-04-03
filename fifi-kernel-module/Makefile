include $(TOPDIR)/rules.mk

PKG_NAME:=fifi-kernel-module
PKG_VERSION:=2014-03-15
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=79d7560aa1a9cf02b59d60246227c269e088fa78

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:steinwurf-internal/fifi-kernel-module.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define KernelPackage/kfifi
  SUBMENU:=Libraries
  TITLE:=Finite field arithmetics
  FILES:=$(PKG_BUILD_DIR)/module/kfifi.$(LINUX_KMOD_SUFFIX)
  AUTOLOAD:=$(call AutoLoad,10,kfifi)
endef

MAKE_FLAGS += \
	KERNELPATH="$(LINUX_DIR)"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/module/ $(MAKE_FLAGS) all
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/kernel/kfifi/
	$(CP) $(PKG_BUILD_DIR)/module/include $(1)/usr/include/kernel/kfifi/
endef

$(eval $(call KernelPackage,kfifi))
