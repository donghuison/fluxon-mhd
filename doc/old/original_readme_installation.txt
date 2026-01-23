There are two components to FLUX: a C simulation library (libflux.a) and a Perl module (Flux.pm, etc). Automake and Perl's ExtUtils::MakeMaker don't play nicely together, and libflux.a needs to be installed before the Perl module is built.  Therefore, we build and install the C and Perl components separately.

You should declare up to two environment variables, which are only needed for build and installation:

FL_PREFIX (required, defaults to /usr/local):
    Where the FLUX simulation library and include files should be installed.

PL_PREFIX (optional, no default):
    Where the Perl front-end module should be installed. This location should be in Perl's @INC list. Try doing ' perl -e "print join(qq|\n|,@INC,q||);" ' at the command line to see the contents of this list. If $PL_PREFIX/lib/perl5 is not included in @INC, then Perl will not be able to find the Flux module after installation. You can add $PL_PREFIX/lib/perl5 to your PERL5LIB environment variable to solve that problem.  Or you can just leave PL_PREFIX undefined and Perl will do the Right Thing.

After installation, some autoloading routines will be installed for you.  See the docs for PDL::AutoLoader (https://metacpan.org/pod/PDL::AutoLoader) for a description of this handy feature of PDL.  Instructions come at the end of the installation script.


0) The zeroth line exports the environment variables you have already declared.
1) The first line builds the simulation library. A copy of the library and include files will be installed into a directory named 'sandbox', so if you use that for the $FL_PREFIX, then nothing will be installed system wide. This may be good for testing.
2) The second line installs libflux.a and some header files into $FL_PREFIX/lib and $FL_PREFIX/include/flux, respectively.
3) The third line builds the Perl module (and prepares it to install in the location given by $PL_PREFIX).
4) The fourth line runs the test suite.
5) The fifth line installs Flux.pm, etc.
6) The sixth line is optional, and cleans up the local environment if desired (or you may just exit the shell).

Note the 'sudo' on lines 2 and [if required based on PL_PREFIX] 4

$ export FL_PREFIX PL_PREFIX
$ make libbuild
$ sudo make libinstall
$ make pdlbuild
$ make pdltest
$ [sudo] make pdlinstall
$ export -n FL_PREFIX PL_PREFIX

IFF both the library and the module are going to be installed in root-owned or user-owned locations, you can shortcut the above with

$ export PL_PREFIX FL_PREFIX
$ [sudo] make everything
$ export -n FL_PREFIX PL_PREFIX

for example, to install everything into your home directory /home/user/local/lib, /home/user/local/include, etc., you could do (making sure to substitute the user home directory path, without tildes):

$ export PL_PREFIX='/home/user/local'
$ export FL_PREFIX='/home/user/local'
$ make everything
