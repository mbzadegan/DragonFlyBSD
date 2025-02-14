# How compile new release 

The nrelease framework is used to build our release and snapshot images
(ISO and IMG).

To build a custom image with extra packages (For example: gcc13, lapack, blas, openblas), just do:
```
$ cd /usr/src/nrelease
$ make release binpkgs \
       DPORTS_EXTRA_PACKAGES="lang/gcc13 math/lapack math/blas
math/openblas"
```
When it finishes, the ISO and IMG images are at **/usr/obj/release**.

You can find the available nrelease targets and options with:
```
$ make -f /usr/src/nrelease/Makefile
```
and it current shows:

```
Targets:
   release     - full build from scratch
   quick       - attempt to do an incremental rebuild
   realquick   - attempt to restart after world & kernel
   restartpkgs - attempt to restart at the pkg building stage

Optional targets:
   nopkgs      - do not install any packages
   binpkgs     - use binary packages with pkg(8)
   gui         - do a GUI release

Variables:
   DPORTS_EXTRA_PACKAGES: add additional packages
   GITURL_SRC: override the Git URL to source repository
   GITURL_DPORTS: override the Git URL to dports repository
   IMGSIZE: override the size of .img (in 512-byte sectors)
   IMGSIZE_MB: override the size of .img (in units of MB)
   NREL_MAKE_JOBS: override the default value (sysctl hw.ncpu)
   PKG_<port>: specify the package name for port <port>
   WITHOUT_SRCS: do not package source code if set

```
