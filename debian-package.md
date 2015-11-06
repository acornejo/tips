# Debian-Package

## To build a package from source

    apt-get build-dep packagename
    apt-get source -b packagename

OR

    apt-get build-dep packagename
    apt-get source packagename
    dpkg-buildpackage -rfakeroot -us -uc

OR

    apt-get build-dep packagename
    apt-get source packagename
    debuild -b -us -uc

OR

    wget http://server/package.tbz2
    tar -xjvf package.tbz2
    cd package
    make
    checkinstall -D make install

OR

    wget http://server/package.orig.tar.gz
    wget http://server/package.diff.gz
    tar -xzvf package.orig.tar.gz
    pushd package
    zcat ../package.diff.gz | patch -p1
    fakeroot debian/rules binary
    popd

## To install the package

    dpkg -i packagename.deb

## To list files in the package

    dpkg -L packagename

## To remove the package (use -P instead of -r to purge):

    dpkg -r packagename

## To see to which package a file belongs

    dpkg -S file

## To extract the files of a package

    dpkg-deb -x packagename.deb outputdir

## To extract the control files of a package

    dpkg-deb -e packagename.deb outputdir
