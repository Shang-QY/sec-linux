Display Subsystem:(default FBdev)

Steps switch to DRM:
1、Disable fbdev,close below config items：
CONFIG_FB_STARFIVE=y
CONFIG_FB_STARFIVE_HDMI_TDA998X=y
CONFIG_FB_STARFIVE_VIDEO=y

2、open DRM hdmi pipeline,enable items:
CONFIG_DRM_I2C_NXP_TDA998X=y
CONFIG_DRM_I2C_NXP_TDA9950=y
CONFIG_DRM_STARFIVE=y
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_PHY_M31_DPHY_RX0=y

Precautions：when use DRM hdmi pipeline,please make sure CONFIG_DRM_STARFIVE_MIPI_DSI is disable ,
			 or will cause color abnormal.

3、open DRM mipi pipeline

enable items:
	CONFIG_DRM_STARFIVE_MIPI_DSI=y



install libdrm:
make buildroot_initramfs-menuconfig
choose:
BR2_PACKAGE_LIBDRM=y
BR2_PACKAGE_LIBDRM_RADEON=y
BR2_PACKAGE_LIBDRM_AMDGPU=y
BR2_PACKAGE_LIBDRM_NOUVEAU=y
BR2_PACKAGE_LIBDRM_ETNAVIV=y
BR2_PACKAGE_LIBDRM_INSTALL_TESTS=y

