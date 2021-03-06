# Kbuild for the AVM NTFS filesystem.
#
# vim: set ft=make noet:

LIBNTFS_SRC := libntfs-3g

GIT_CMD = git -C $(src)
__avm_non_stable := $(shell $(GIT_CMD) rev-parse --abbrev-ref HEAD 2>/dev/null | grep -E '^(shared|p)/' || true)
__avm_antfs_tag = $(shell $(GIT_CMD) describe --tags | grep -o '^[0-9.]*')
__avm_antfs_commit = $(shell $(GIT_CMD) rev-parse --short HEAD)

ANTFS_LOGLEVEL_DEFAULT ?= $(if $(__avm_non_stable),ANTFS_LOGLEVEL_ERR_EXT,ANTFS_LOGLEVEL_ERR)
ANTFS_VERSION ?= $(if $(__avm_non_stable),$(__avm_antfs_commit),$(__avm_antfs_tag))

ccflags-y += -DANTFS_LOGLEVEL_DEFAULT=$(ANTFS_LOGLEVEL_DEFAULT)
ccflags-y += -DANTFS_VERSION='"$(ANTFS_VERSION)"'

ccflags-y += -I$(src)
ccflags-y += -I$(src)/include
ccflags-$(CONFIG_ANTFS_EXTRA_WARNINGS) += -Wextra -Wshadow -Werror -Wno-error=shadow

obj-$(CONFIG_ANTFS_FS) += antfs.o

antfs-y += dir.o
antfs-y += file.o
antfs-y += inode.o
antfs-y += super.o
antfs-y += $(LIBNTFS_SRC)/attrib.o
antfs-y += $(LIBNTFS_SRC)/attrlist.o
antfs-y += $(LIBNTFS_SRC)/bootsect.o
antfs-y += $(LIBNTFS_SRC)/collate.o
antfs-y += $(LIBNTFS_SRC)/compress.o
antfs-y += $(LIBNTFS_SRC)/device.o
antfs-y += $(LIBNTFS_SRC)/dir.o
antfs-y += $(LIBNTFS_SRC)/index.o
antfs-y += $(LIBNTFS_SRC)/inode.o
antfs-y += $(LIBNTFS_SRC)/lcnalloc.o
antfs-y += $(LIBNTFS_SRC)/linux_io.o
antfs-y += $(LIBNTFS_SRC)/logfile.o
antfs-y += $(LIBNTFS_SRC)/mft.o
antfs-y += $(LIBNTFS_SRC)/misc.o
antfs-y += $(LIBNTFS_SRC)/mst.o
antfs-y += $(LIBNTFS_SRC)/object_id.o
antfs-y += $(LIBNTFS_SRC)/reparse.o
antfs-y += $(LIBNTFS_SRC)/runlist.o
antfs-y += $(LIBNTFS_SRC)/unistr.o
antfs-y += $(LIBNTFS_SRC)/volume.o
