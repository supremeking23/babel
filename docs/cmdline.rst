.. -*- mode: rst; encoding: utf-8 -*-

.. _cmdline:

======================
Command-Line Interface
======================

Babel includes a command-line interface for working with message catalogs,
similar to the various GNU ``gettext`` tools commonly available on Linux/Unix
systems.


When properly installed, Babel provides a script called ``pybabel``::

    $ pybabel --help
    usage: pybabel command [options] [args]

    options:
      --version       show program's version number and exit
      -h, --help      show this help message and exit
      --list-locales  print all known locales and exit
      -v, --verbose   print as much as possible
      -q, --quiet     print as little as possible

    commands:
      compile  compile message catalogs to MO files
      extract  extract messages from source files and generate a POT file
      init     create new message catalogs from a POT file
      update   update existing message catalogs from a POT file

The ``pybabel`` script provides a number of sub-commands that do the actual
work. Those sub-commands are described below.


compile
=======

The ``compile`` sub-command can be used to compile translation catalogs into
binary MO files::

    $ pybabel compile --help
    usage: pybabel compile [options]

    compile message catalogs to MO files

    options:
      -h, --help            show this help message and exit
      -D DOMAIN, --domain=DOMAIN
                            domain of MO and PO files (default 'messages')
      -d DIR, --directory=DIR
                            base directory of catalog files
      -l LOCALE, --locale=LOCALE
                            locale of the catalog
      -i FILE, --input-file=FILE
                            name of the input file
      -o FILE, --output-file=FILE
                            name of the output file (default
                            '<output_dir>/<locale>/LC_MESSAGES/<domain>.mo')
      -f, --use-fuzzy       also include fuzzy translations (default False)
      --statistics          print statistics about translations

If ``directory`` is specified, but ``output-file`` is not, the default filename
of the output file will be::

    <directory>/<locale>/LC_MESSAGES/<domain>.mo

If neither the ``input_file`` nor the ``locale`` option is set, this command
looks for all catalog files in the base directory that match the given domain,
and compiles each of them to MO files in the same directory.


extract
=======

The ``extract`` sub-command can be used to extract localizable messages from
a collection of source files::

    $ pybabel extract --help
    usage: pybabel extract [options] dir1 <dir2> ...

    extract messages from source files and generate a POT file

    options:
      -h, --help            show this help message and exit
      --charset=CHARSET     charset to use in the output (default "utf-8")
      -k KEYWORDS, --keyword=KEYWORDS
                            keywords to look for in addition to the defaults. You
                            can specify multiple -k flags on the command line.
      --no-default-keywords
                            do not include the default keywords
      -F MAPPING_FILE, --mapping=MAPPING_FILE
                            path to the extraction mapping file
      --no-location         do not include location comments with filename and
                            line number
      --omit-header         do not include msgid "" entry in header
      -o OUTPUT, --output=OUTPUT
                            path to the output POT file
      -w WIDTH, --width=WIDTH
                            set output line width (default 76)
      --no-wrap             do not break long message lines, longer than the
                            output line width, into several lines
      --sort-output         generate sorted output (default False)
      --sort-by-file        sort output by file location (default False)
      --msgid-bugs-address=EMAIL@ADDRESS
                            set report address for msgid
      --copyright-holder=COPYRIGHT_HOLDER
                            set copyright holder in output
      -c TAG, --add-comments=TAG
                            place comment block with TAG (or those preceding
                            keyword lines) in output file. One TAG per argument
                            call


init
====

The `init` sub-command creates a new translations catalog based on a PO
template file::

    $ pybabel init --help
    usage: pybabel init [options]

    create new message catalogs from a POT file

    options:
      -h, --help            show this help message and exit
      -D DOMAIN, --domain=DOMAIN
                            domain of PO file (default 'messages')
      -i FILE, --input-file=FILE
                            name of the input file
      -d DIR, --output-dir=DIR
                            path to output directory
      -o FILE, --output-file=FILE
                            name of the output file (default
                            '<output_dir>/<locale>/LC_MESSAGES/<domain>.po')
      -l LOCALE, --locale=LOCALE
                            locale for the new localized catalog


update
======

The `update` sub-command updates an existing new translations catalog based on
a PO template file::

    $ pybabel update --help
    usage: pybabel update [options]

    update existing message catalogs from a POT file

    options:
      -h, --help            show this help message and exit
      -D DOMAIN, --domain=DOMAIN
                            domain of PO file (default 'messages')
      -i FILE, --input-file=FILE
                            name of the input file
      -d DIR, --output-dir=DIR
                            path to output directory
      -o FILE, --output-file=FILE
                            name of the output file (default
                            '<output_dir>/<locale>/LC_MESSAGES/<domain>.po')
      -l LOCALE, --locale=LOCALE
                            locale of the translations catalog
      --ignore-obsolete     do not include obsolete messages in the output
                            (default False)
      -N, --no-fuzzy-matching
                            do not use fuzzy matching (default False)
      --previous            keep previous msgids of translated messages (default
                            False)

If ``output_dir`` is specified, but ``output-file`` is not, the default
filename of the output file will be::

    <directory>/<locale>/LC_MESSAGES/<domain>.mo

If neither the ``output_file`` nor the ``locale`` option is set, this command
looks for all catalog files in the base directory that match the given domain,
and updates each of them.
