# SPDX-License-Identifier: GPL-2.0+
#
# (C) Copyright 2000-2006
# Wolfgang Denk, DENX Software Engineering, wd@denx.de.
#
# Copyright (C) 2017 Andes Technology Corporation
# Rick Chen, Andes Technology Corporation <rick@andestech.com>

obj-$(CONFIG_CMD_BOOTM) += bootm.o
obj-$(CONFIG_CMD_BOOTI) += bootm.o image.o
obj-$(CONFIG_CMD_GO) += boot.o
obj-y	+= cache.o
obj-$(CONFIG_SIFIVE_CACHE) += sifive_cache.o
obj-$(CONFIG_SYS_CACHE_THEAD_CMO) += thead_cmo.o
ifeq ($(CONFIG_$(PHASE_)RISCV_MMODE),y)
obj-$(CONFIG_$(PHASE_)RISCV_ACLINT) += aclint_ipi.o
obj-$(CONFIG_ANDES_PLICSW) += andes_plicsw.o
else
obj-$(CONFIG_SBI) += sbi.o
obj-$(CONFIG_SBI_IPI) += sbi_ipi.o
endif
obj-y	+= interrupts.o
ifeq ($(CONFIG_$(PHASE_)SYSRESET),)
obj-y	+= reset.o
endif
obj-y   += setjmp.o
obj-$(CONFIG_$(PHASE_)SMP) += smp.o
obj-$(CONFIG_XPL_BUILD)	+= spl.o
obj-y   += fdt_fixup.o
obj-$(CONFIG_$(SPL)CMD_BDI) += bdinfo.o
obj-$(CONFIG_OF_BOARD) += board.o

# For building EFI apps
CFLAGS_NON_EFI := -fstack-protector-strong
CFLAGS_$(EFI_CRT0) := $(CFLAGS_EFI)
CFLAGS_REMOVE_$(EFI_CRT0) := $(CFLAGS_NON_EFI)

CFLAGS_$(EFI_RELOC) := $(CFLAGS_EFI)
CFLAGS_REMOVE_$(EFI_RELOC) := $(CFLAGS_NON_EFI)

obj-$(CONFIG_$(PHASE_)USE_ARCH_MEMSET) += memset.o
obj-$(CONFIG_$(PHASE_)USE_ARCH_MEMMOVE) += memmove.o
obj-$(CONFIG_$(PHASE_)USE_ARCH_MEMCPY) += memcpy.o
obj-$(CONFIG_$(PHASE_)USE_ARCH_STRLEN) += strlen_zbb.o
obj-$(CONFIG_$(PHASE_)USE_ARCH_STRCMP) += strcmp_zbb.o
obj-$(CONFIG_$(PHASE_)USE_ARCH_STRNCMP) += strncmp_zbb.o

obj-$(CONFIG_$(PHASE_)SEMIHOSTING) += semihosting.o
