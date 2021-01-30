PKG_NAME = racket
PKG_VERS = 7.9
PKG_EXT = tgz
PKG_DIST_NAME = $(PKG_NAME)-minimal-$(PKG_VERS)-src-builtpkgs.$(PKG_EXT)
PKG_DIST_SITE = https://download.racket-lang.org/releases/$(PKG_VERS)/installers/
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

#DEPENDS = cross/ncursesw

HOMEPAGE = https://racket-lang.org/
COMMENT  = Racket programming language - minimal installation.
LICENSE  = MIT

GNU_CONFIGURE = 1
CONFIGURE_ARGS = --enable-bcdefault --enable-shared

CONFIGURE_TARGET = racket_configure

#PRE_COMPILE_TARGET = zsh_pre_compile

#ifeq ($(ZSH_STATIC_MODULES),true)
#	BUILD_MSG = "Building zsh with statically linked modules."
#	POST_CONFIGURE_TARGET = link-zsh-modules
#else
#	BUILD_MSG = "Building zsh with dynamically linked modules."
#endif

#INSTALL_TARGET = zsh_install

include ../../mk/spksrc.cross-cc.mk

#.PHONY: link-zsh-modules
#link-zsh-modules:
#	@$(RUN) sed -i 's/link=no/link=static/' config.modules
#	# gdbm is not available, so don't try to compile it.
#	@$(RUN) sed -i 's|\(name=zsh/db/gdbm.*\)link=static|\1link=no|' config.modules

.PHONY: racket_configure
racket_configure:
	$(RUN) BUILD_DIR = $(WORK_DIR)/$(PKG_DIR)/build
	mkdir -p $(BUILD_DIR)
	echo $(pwd)
	cd $(BUILD_DIR) 
	echo $(pwd)
	$(WORK_DIR)/$(PKG_DIR)/src/configure $(REAL_CONFIGURE_ARGS)

#	@$(MSG) $(BUILD_MSG)

#.PHONY: zsh_install
#zsh_install:
#	umask 022; $(RUN) $(MAKE) install DESTDIR=$(INSTALL_DIR)
