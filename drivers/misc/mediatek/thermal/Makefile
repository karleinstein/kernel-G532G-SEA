#
# Copyright (C) 2015 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#

ccflags-y += -I$(srctree)

THERMAL_CHIP_DRIVER_DIR := $(srctree)/drivers/misc/mediatek/thermal/$(MTK_PLATFORM)
ccflags-y  += -I$(THERMAL_CHIP_DRIVER_DIR)/inc
ccflags-y  += -I$(srctree)/drivers/misc/mediatek/thermal/fakeHeader/

ifneq ($(CONFIG_ARCH_MT8173),y)
obj-$(CONFIG_THERMAL) += mtk_thermal_monitor.o
endif
obj-$(CONFIG_THERMAL) += mtk_cooler_shutdown.o
ifeq ($(CONFIG_MTK_LEDS), y)
    # setMaxbrightness() defined in mediatek/kernel/drivers/leds/leds_drv.c only built when CONFIG_MTK_LEDS is set
    ifeq ($(CONFIG_MTK_COOLER_LCD_SUPPORT),y)
    obj-$(CONFIG_THERMAL) += mtk_cooler_backlight.o
    endif
endif
obj-$(CONFIG_THERMAL) += mtk_cooler_kshutdown.o
#obj-$(CONFIG_THERMAL) += mtk_cooler_spkrvol.o
#obj-$(CONFIG_THERMAL) += mtk_cooler_dropcall.o
obj-$(CONFIG_THERMAL) += mtk_cooler_cam.o
obj-$(CONFIG_THERMAL) += mtk_cooler_vrt.o

ifeq (,$(filter $(CONFIG_ARCH_MT8173) $(CONFIG_ARCH_MT8163), y))
obj-y += common/
endif
obj-y += $(subst ",,$(CONFIG_MTK_PLATFORM))/

