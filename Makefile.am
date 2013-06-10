CFLAGS=
LDFLAGS=
SOVERSION = 2
lib_LTLIBRARIES = libdclass.la libdclassjni.la
AUTOMAKE_OPTIONS = foreign

libdclass_la_SOURCES = src/dtree_core.c    		  \
                       src/openddr_client.c		  \
                       src/dclass_file.c   		  \
                       src/dtree_mem.c     		  \
                       src/dtree_util.c    		  \
                       src/dclass_client.c 		  

libdclass_la_LDFLAGS = -D__X86_64__ -fPIC  -shared -DSHARED_OBJECT -Wl
libdclass_ladir = $(CURDIR)



libdclassjni_la_SOURCES = java-wikimedia/dclass-wrapper.c
libdclassjni_ladir = $(CURDIR)/.libs
#libdclassjni_la_LIBRARIES = libdclass.so
libdclassjni_la_CFLAGS  = -g -I$(CURDIR)/.libs -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/linux -Wall -I ./jni/ -I./src/ -ldclass


#libdclassjni_la_CFLAGS  = -g -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/linux -Wall -I ./jni/ -I./src/
#libdclassjni_la_LDFLAGS = -D__X86_64__ -fPIC  -shared -DSHARED_OBJECT -Wl

