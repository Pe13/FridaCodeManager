# Makefile
#
# Compile all FridaCodeManager essentials
# :3
#

export SDKROOT := sdk

export CC := clang
export CF := -target arm64-apple-ios15 -arch arm64 -I$(ROOTDIR)/include

export COBJ_DIR := tmp/out/c
export MOBJ_DIR := tmp/out/m

# fishy patch
export uuid := uuid

all: libfcm-compile libdycall-compile libsean-compile #libcheck-compile

prepare:
	@rm -rf lib/build
	@mkdir -p lib/build

%-compile: prepare
	@$(MAKE) -C $* all || $(MAKE) -C $* clean
	@cp $*/tmp/lib/$*.a lib/build/$*.a
	@$(MAKE) -C $* clean

#libfcm-compile: prepare
#	@$(MAKE) -C libfcm all
#	@cp libfcm/tmp/lib/libfcm.a lib/build/libfcm.a
#	@$(MAKE) -C libfcm clean
#
#libsean-compile: prepare
#	@$(MAKE) -C libsean all
#	@cp libsean/tmp/lib/libsean.a lib/build/libsean.a
#	@$(MAKE) -C libsean clean
#
#libdycall-compile: prepare
#	@$(MAKE) -C libdycall all
#	@cp libdycall/tmp/lib/libdycall.a lib/build/libdycall.a
#	@$(MAKE) -C libdycall clean
#
#libcheck-compile: prepare
#	@$(MAKE) -C libcheck all
#	@cp libcheck/tmp/lib/libcheck.a lib/build/libcheck.a
#	@$(MAKE) -C libcheck clean

clean:
	@rm -rf lib/build
