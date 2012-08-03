all: installed


GIT_DIR = build/sicktoolbox-trunk
GIT_URL = https://github.com/hawesie/sicktoolbox.git
GIT_PATCH =  
#TARBALL_PATCH = stdlib_include.patch power_delay.patch 
GIT_REVISION = #-


include $(shell rospack find mk)/git_checkout.mk

installed: wiped $(GIT_DIR)
        # extra stuff from autoconf version
	cd $(GIT_DIR) && libtoolize
	cd $(GIT_DIR) && aclocal -I m4
	cd $(GIT_DIR) && autoheader
	cd $(GIT_DIR) && automake --add-missing
	cd $(GIT_DIR) && autoconf
	cd $(GIT_DIR) && ./configure --prefix=`rospack find sicktoolbox`/sicktoolbox
	cd $(GIT_DIR) && make && make install
	touch installed

wiped: Makefile
	make wipe
	touch wiped

clean:
	-rm -rf sicktoolbox-trunk sicktoolbox
	rm -f *~ installed

.PHONY : clean wipe

wipe: clean
	rm -rf $(GIT_DIR)
