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

COMPILE_TARGET = racket_compile

INSTALL_TARGET = racket_install

include ../../mk/spksrc.cross-cc.mk

.PHONY: racket_configure
racket_configure:
	$(RUN) mkdir -p $(WORK_DIR)/$(PKG_DIR)/build
	cd $(WORK_DIR)/$(PKG_DIR)/build && ../src/configure $(REAL_CONFIGURE_ARGS)

.PHONY: racket_compile
racket_compile:
	$(RUN) && cd $(WORK_DIR)/$(PKG_DIR)/build && $(MAKE) $(COMPILE_MAKE_OPTIONS)

.PHONY: racket_install
racket_install:
	$(RUN) && cd $(WORK_DIR)/$(PKG_DIR)/build && $(MAKE) DESTDIR=$(INSTALL_DIR) install prefix=$(INSTALL_PREFIX)
