ifeq ($(CONFIG_OF),y)

# SEA
dtb-$(CONFIG_ARCH_MT6735) += mt6737t_grandpplte_cis_ser_00.dtb \
	mt6737t_grandpplte_cis_ser_01.dtb \
	mt6737t_grandpplte_cis_ser_02.dtb \
	mt6737t_grandpplte_cis_ser_03.dtb \
	mt6737t_grandpplte_cis_ser_04.dtb

# LTN
dtb-$(CONFIG_ARCH_MT6735) += mt6737t_grandpplte_ltn_dtv_01.dtb \
	mt6737t_grandpplte_ltn_dtv_02.dtb \
	mt6737t_grandpplte_ltn_dtv_03.dtb \
	mt6737t_grandpplte_ltn_dtv_04.dtb

dtb-$(CONFIG_ARCH_MT6735) += mt6737t_grandpplte_ltn_open_01.dtb \
	mt6737t_grandpplte_ltn_open_02.dtb \
	mt6737t_grandpplte_ltn_open_03.dtb \
	mt6737t_grandpplte_ltn_open_04.dtb

# EUR
dtb-$(CONFIG_ARCH_MT6735) += titan6737t_phone_m_00.dtb \
	titan6737t_phone_m_01.dtb \
	titan6737t_phone_m_02.dtb \
	titan6737t_phone_m_03.dtb

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif

ifeq ($(strip $(CONFIG_BUILD_ARM_DTB_OVERLAY_IMAGE)), y)
DTB_LIST += $(addsuffix .dtb,$(subst $\",,$(CONFIG_BUILD_ARM_DTB_OVERLAY_IMAGE_NAMES)))
endif

targets += dtbs dtbs_install
targets += $(DTB_LIST)
endif

# *.dtb used to be generated in the directory above. Clean out the
# old build results so people don't accidentally use them.
dtbs: $(addprefix $(obj)/, $(DTB_LIST))
	$(Q)rm -f $(obj)/../*.dtb

clean-files := *.dtb

dtbs_install: $(addsuffix _dtbinst_, $(dtb-y))
