# Diff-Patches

Directories:

    diff -upr dir dir.fixed > changes.patch
    cp -a dir dir.patched
    cd dir.patched
    patch -p1 -i ../mychanges.patch

Files:

    diff -up file file.new > changes.patch
    patch -i changes.patch
