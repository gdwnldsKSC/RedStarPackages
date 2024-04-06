# RedStarPackages
 Red Star OS 3.0 Updates and additional Packages

# Contents
Packages built (currently with GCC 6.2.0) for Red Star OS 3.0 to  
update system components and provide additional packages not   
included in the base system.  

Red Star OS 3.0 is loosely based on Fedora 11, so we can reuse a   
lot of the upstream spec files for RPM building and configuration  
to get sane approximations of what is included that we can't   
otherwise properly deduce.  

Each created package will have the matching SRPM to allow building  
for yourself, as red star did *not* include SRPMs.   

Anything below that does not list an RS3.0 default version was not  
included in the binary packages or distribution at all. Anything notated  
Included means that identical version was already there, but missing  
components.  

# Package List  
Applications/Internet/wget-1.14 - hand built before working RPM build process   
Applications/File/file-4.26 - FC10 version / RS 3.0 default version -    
Development/Tools/help2man-1.36.4 - FC10 version  
Applications/System/asciidoc-8.2.5 - FC10 version  
Applications/File/xz-4.999.9-0.2beta.20100401git - FC14 version (Included, rebuilt for -devel)  
Development/Tools/make-3.82 - FC14 version / RS 3.0 default version - 
Development/Tools/elfutils-0.149 - FC14 version (Included, rebuilt for -devel)  
Development/Tools/zlib-1.2.5 - FC14 version  / RS 3.0 default version - 1.2.3-23   
Applications/Archiving/sharutils-4.10 - FC14 version  
Development/System/redhat-rpm-config-9.0.3 - FC10 version / RS 3.0 default version - 8.0.40-1 (you don't need this until all RPM upgrade packages are available)  
System Environment/Shells/bash-3.2.39(1) - FC10 Version / RS 3.0 default version - 3.1.7(1)  
System Environment/Libraries/ncurses-5.7 - FC11 Version / RS 3.0 default version - 5.6   
Application/System/rpmreaper-0.1.5 - FC10 Version  
System Environment/Libraries/libtermcap-2.0.8-47 - FC8 Version / RS 3.0 default version - 2.0.8-45 (we will not need this soon)   
System Environment/Base/termcap-5.5 - FC8 Version / RS 3.0 default version - termcap 5.4 (we will not need this soon)   
 

# Install notes

Currently, there's some unresolved file conflicts, Eventually  
we will want to fix this with a higher version so that we can just upgrade  
straight from an online repo. For now we can force installations to get into  
a better 'known' sane state with these packages when upgrade time comes  
until we can get into such an online repo upgrade capability.  From the  
looks of things so far, I believe that will be when we can start tackling  
FC15 packages and have OpenSSL to a version past 0.9.8 which will involve a  
lot of rebuilds and broken packages initially.  
  
Any package without notes will just install via rpm -i or rpm -U as appropriate  
  
libtermcap and termcap should NOT be needed anymore, but because of RS3.0's very  
interesting mix of packages and versions .... we have to work around it until we   
get to a unified base of some type that allows us to remove them.  

File is built using standard fedora files, so we must due to conflicts  
use rpm -i --force for file-libs RPM, then rpm -U file will work. After  
file-devel and python-magic can install.   

Elfutils is another package that wants to have circular dependancies  
so we go anead and rpm -i --force --nodeps elfutils-* to ensure all  
packages are consistent and same version Even though currently we have  
the same exact version rebuilt that is included in RS3 anyway.  

For all else, some --force, --nodeps, or --replacefiles may be required as needed if   
not noted for now. Some things may be needed to uninstall such as the libtermcap  
and termcap items in order to allow newer installations such as ncurses to proceed.  

After forcing bash to be installed, I had to re-run rpm -U libtermcap to make it work  

