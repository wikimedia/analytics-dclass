CFLAGS=
LDFLAGS=
SOVERSION = 2
lib_LTLIBRARIES = libdclass.la libdclassjni.la
AUTOMAKE_OPTIONS = foreign

JAVAC = /usr/bin/javac
JAVAH = /usr/bin/javah
JAR = /usr/bin/jar

DISTCLEANFILES = $(CURDIR)/java/jni/dclass_java.h $(CURDIR)/dclass.jar

####################################
# Building libdclass
####################################

libdclass_la_SOURCES = src/dtree_core.c    		  \
                       src/openddr_client.c		  \
                       src/dclass_file.c   		  \
                       src/dtree_mem.c     		  \
                       src/dtree_util.c    		  \
                       src/dclass_client.c

libdclass_la_LDFLAGS = -fPIC  -shared -DSHARED_OBJECT
libdclass_ladir = $(CURDIR)

####################################
# Generating dclass_java.h which
# will be used to compile libdclassjni
####################################


BUILT_SOURCES = dclass_java.h

dclass_java.h: dClass.class
	$(JAVAH) -o java/jni/dclass_java.h -classpath ./java dclass.dClass

dClass.class: java/dclass/dClass.java
	$(JAVAC) -classpath ./java java/dclass/dClass.java

####################################
# Building libdclassjni
####################################

libdclassjni_la_SOURCES = java/jni/dclass_java.c
libdclassjni_la_CFLAGS  = -g -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/linux -I$(CURDIR)/java/jni/ -I$(CURDIR)/src/ -ldclass


######################################
# Building the .class and .jar
# (later to be put in libdclass-java
######################################

javadir = java/dclass

dist_java_JAVA = java/dclass/dClass.java java/dclass/dClassLoader.java java/dclass/dClassMain.java
dist_java_DATA = dclass.jar

all-local: dclass.jar

dclass.jar: $(dist_java_JAVA) classjava.stamp
	$(JAR) -cfm dclass.jar java/dclass/manifest.txt dclass/


