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

# Package List  
Applications/Internet/wget-1.14   
Applications/File/file-4.26   
Development/Tools/help2man-1.36.4 - FC10 version  
Applications/System/asciidoc-8.2.5 - FC10 version  
Applications/File/xz-4.999.9-0.2beta.20100401git - FC14 version (already in RS3, rebuilt for -devel)  
Development/Tools/make-3.82 - FC14 version   
Development/Tools/elfutils-0.149 - FC14 version (already in RS3, rebuilt for -devel)  

# Install notes
File is built using standard fedora files, so we must due to conflicts  
use rpm -i --force for file-libs RPM, then rpm -U file will work. After  
file-devel and python-magic can install.   

Elfutils is another package that wants to have circular dependancies  
so we go anead and rpm -i --force --nodeps elfutils-* to ensure all  
packages are consistent and same version Even though currently we have  
the same exact version rebuilt that is included in RS3 anyway.  