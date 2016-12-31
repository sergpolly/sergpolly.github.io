---
layout: post
title:  "Setting up a system"
date:   2016-12-28 17:13:43 -0500
categories: jekyll update
---

Python installation:

Assuming one already have an up to date python installation with the pip package manager, following commands should work just fine:

{% highlight bash %}
pip install --prefix=/home/USER_NAME/usr/local numpy;
pip install --prefix=/home/USER_NAME/usr/local scipy;
pip install --prefix=/home/USER_NAME/usr/local matplotlib;
pip install --prefix=/home/USER_NAME/usr/local pandas;
pip install --prefix=/home/USER_NAME/usr/local scipy;
pip install --prefix=/home/USER_NAME/usr/local sympy;
pip install --prefix=/home/USER_NAME/usr/local ipython;
pip install --prefix=/home/USER_NAME/usr/local biopython;
{% endhighlight %}


ViennaRNA:

ViennaRNA requires nice perl environment - so, make sure you have one, or load corresponding module for HPCC.

{% highlight bash %}
wget http://www.tbi.univie.ac.at/RNA/download/sourcecode/2_3_x/ViennaRNA-2.3.1.tar.gz
tar -xzf ViennaRNA-2.3.1.tar.gz
cd ViennaRNA-2.3.1

# configure, make, install ...
./configure --prefix=/home/USER_NAME/usr/local
{% endhighlight %}



To be updated to include other stuff ...




<!-- 
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes

configure: WARNING: "Can't find libgsl. Falling back to default implementation."

configure: WARNING: dot command not found on your system!
configure: WARNING: deactivating graph output in reference manual!

config.status: creating tests/Makefile
config.status: creating tests/RNApath.py
config.status: creating tests/RNApath.pm
config.status: creating misc/Makefile
config.status: creating interfaces/Makefile
config.status: creating Makefile
config.status: creating RNAlib2.pc
config.status: creating src/Utils/Makefile
config.status: creating src/bin/Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating src/ViennaRNA/Makefile
config.status: creating doc/Makefile
config.status: creating man/cmdlopt.sh
config.status: creating packaging/viennarna.spec
config.status: creating packaging/PKGBUILD
config.status: creating packaging/win_installer_archlinux_i686.nsi
config.status: creating packaging/win_installer_archlinux_x86_64.nsi
config.status: creating packaging/win_installer_fedora_i686.nsi
config.status: creating packaging/win_installer_fedora_x86_64.nsi
config.status: creating config.h


sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$ echo $LDFLAGS
-L/share/pkg/gsl/1.16/lib
sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$ #vim Makefile
sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$ echo $LDFLAGS
-L/share/pkg/gsl/1.16/lib
sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$ #CPPFLAGS=-I/share/pkg/gsl/1.16/include
sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$ echo $CPPFLAGS
-I/share/pkg/gsl/1.16/include
sv49w@very_big_computer:~/ViennaRNA-2.3.1/src/ViennaRNA$







 -->