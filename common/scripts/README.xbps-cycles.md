# Cycle detector for cereus-pkgs

This script enumerates dependencies for packages in a
[cereus-pkgs repository](https://codeberg.org/cereus-linux/cereus-pkgs)
and identifies build-time dependency cycles.

For command syntax, run `xbps-cycles.py -h`. Often, it may be sufficient to run
`xbps-cycles.py` with no arguments. By default, the script will look for a
repository at `$XBPS_DISTDIR`; if that variable is not defined, the current
directory is used instead. To override this behavior, use the `-d` option to
provide the path to your desired cereus-pkgs clone.

The standard behavior will be to spawn multiple processes, one per CPU, to
enumerate package dependencies. This is by far the most time-consuming part of
the execution. To override the degree of parallelism, use the `-j` option.

Dependencies can be cached on disk, one file per package, in directory
passed with `-c` option. On next execution with same option, dependencies are
read from file rather than computed.

Failures should be harmless but, at this early stage, unlikely to be pretty or
even helpful.
