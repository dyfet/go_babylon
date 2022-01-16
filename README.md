# What is Babylon?

The Babylon project is a re-creation of many of my original PBX network
integration tools from the early 1990's, in go.  Many of these were originally
written in C for QNX, and then ported to Linux. This will eventually include
the F9600 mml server, a Panasonic PAPI DBS server, an smdi server, the SPO256
speaker, cdr logging servers, a cdr collection server, and other odd things.

One reason for this project is simply to help me decide best practices for
developing enterprise services in golang going forward.  This project will
eventually directly support building for traditional os packaging, offer
ansible deployment, or docker creation, using a single top level Makefile.

## Installation

Make "install" is sufficient to install these tools and daemons on a generic
posix system. This installs to /usr/local by default, and can be overridden
with a PREFIX setting, such as ''make PREFIX=/usr install''. The Makefile also
makes it easy to cross-compile, as well as managing separate debug and release
builds. It also should be easy to integrate with traditional OS packaging.

In git checkouts I manage a vendor directory outside of git.  This is because
it may generate different content when you update the go.mod file. Generating
a vendor branch means it also can get into the stand-alone dist tarball, and
that can then be used in network isolated build systems.  Since the builds are
cached anyway without a vendor directory, this has no impact on performance.
The vendor directory is only refreshed if the go.sum file changes.

