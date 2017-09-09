## CPAN/CPANM
Perl的Module在有网络的情况下使用cpan或cpanm，特别推荐cpanm可以很好的解决模块依赖问题，非常方便。
http://seisman.info/perlbrew-for-multiple-versions-of-perl.html

## INSTALL
但是如果没有网络就需要手动安装Module，如果依赖模块太多就悲剧了。通常手动安装的步骤为：
perl Makefile.PL
make
make test
make install
其中最后一步一般需要管理员权限，大部分原因是perl的lib库需要管理员权限才能访问。如果没有管理员权限也没问题，可以安装到自己的Module库中，改动第一步：
perl Makefile.PL PREFIX=~/mylib

## SOLARIS
但似乎上面的步骤在Solaris上依然有些问题，可是尝试以下安装步骤如下：
/usr/perl5/bin/perlgcc Makefile.PL PREFIX=~/mylib
/usr/sfw/bin/gmake
/usr/sfw/bin/gmake test
/usr/sfw/bin/gmake install
系统信息：SunOS sdc-fulmail1-e3 5.10 Generic_148888-01 sun4v sparc SUNW,SPARC-Enterprise-T5120 Solaris 
