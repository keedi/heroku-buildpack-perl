Heroku buildpack: Perl
======================

This is a Heroku buildpack that runs Mojolicious based web applications using Perloku executable file.

Usage
-----

Example usage:

    $ ls -F
    Perloku*
    app.pl*
    cpanfile

    $ cat cpanfile
    requires 'Mojolicious', '7.14';

    $ cat Perloku
    #!/bin/sh
    ./app.pl daemon --listen http://*:$PORT

    $ heroku create --stack cedar --buildpack https://github.com/keedi/heroku-buildpack-perl.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Perloku app detected
    -----> Installing dependencies

The buildpack will detect that your app has an `Perloku` in the root.

Libraries
---------

Dependencies can be declared using `cpanfile` (recommended) or more traditional `Makefile.PL`, `Build.PL` and `META.json` (whichever you can install with `cpanm --installdeps`), and the buildpack will install these dependencies using [cpanm](http://cpanmin.us) into `./local` directory.

