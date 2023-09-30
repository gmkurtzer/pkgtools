# pkgtools

These are some very rough scripts that I use for manipulating and patching RPM files. Feel free to use.

Prepare your system:
```
$ mkdir ~/bin
$ install -m 755 bin/pkg* ~/bin
$ sudo dnf groupinstall "Development Tools"

# If you want to build packages with Mock
$ sudo dnf install mock
$ sudo usermod -G mock `whoami`
```

Simple walkthrough...

```
$ dnf download --source kernel
$ pkgimport kernel*.src.rpm
$ cd kernel
$ pkgprep
$ cd _workdir/kernel*
$ echo "hello world" > testfile
$ cd ../..
$ pkgpatch > kernel-testfile.patch
$ vi SPECS/kernel.spec # edit specfile and add the above created patch
$ pkgbuild
```
