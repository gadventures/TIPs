# TIP 8: Python Style Guide

* **TIP**: 8
* **Title**:  Python Style Guide
* **Author**: Bartek Ciszkowski
* **Status**: Accepted
* **Created**: July 9th, 2015
* **Updates**: N/A

A style guide? But don't we have [PEP 8](https://www.python.org/dev/peps/pep-0008/)? Yes, we do! But this document will discuss

* Recommended PEPs to ignore
* Integration of PEP Linters within your editor.
* Updating legacy code to PEP 8

Why should everyone follow PEP 8? Because when everyone writes code the same,
projects become more accessible, the barrier to entry is lowered, and it
creates a better sense of community within our code base. The less we can silo,
the better.

## Recommended PEPs to ignore

* **E501**: Line too long. By default, PEP 8 suggests lines max out at 80
    characters. We're in the 21st century, so we can spare more space. The
    suggested line length is 90 characters.
* **E121**: Wrong hanging indentation. This has historically felt very finnicky
    in editors and unnecessarly loud.

## Deprecation Warnings, Be Loud!

When developing, we should be well aware of what is soon to be deprecated. This helps all developers write code that won't become stale in the next version of a project, and brings to light important issues around security.

The simplest way to follow this, is to run Python with loud warnings. Just add the following argument to each shell session:

    python -Wall
   
## Integration with your editor

In this guide, we'll focus on two editors. Atom, and Vim. Please feel free to
edit this document to add your favourite editor.

### Atom

The most active linter seems to be [linter-pep8](https://github.com/AtomLinter/linter-pep8).

You'll want to update `maxLineLength` to be set to 90, as proposed in the `E501`
rule above.

### Vim

The recommended linter for Vim is without a doubt,
[Syntastic](https://github.com/scrooloose/syntastic). Installation works with
Pathogen or Vundle, and is easy to configure. Once installed, add these to your `.vimrc`
to be setup for Python editing!

    let g:syntastic_check_on_open = 1  " Automatically check when opening and saving files
    let g:syntastic_check_on_wq = 0    " Recommended: don't check when exiting vim with 'wq'
    let g:syntastic_python_checkers=['flake8']
    let g:syntastic_python_flake8_post_args="--ignore=E501,E121"

### Sublime Text

For Sublime Text 2 or 3 the recommended linter is [Sublime Linter 3](http://www.sublimelinter.com/en/latest/). Sublime Linter 3 can be installed via Sublime's package manager or by cloning the [github repository](https://github.com/SublimeLinter/SublimeLinter3) into the package directory.

## Updating legacy code to PEP 8

Any code you touch should be updated to PEP 8. Although this is rarer today, it
ensures we keep our code base clean for the future.

When you are updating legacy code, it is best to commit all PEP 8 changes in a
separate commit.

For example, if you are fixing a bug, first, you'll commit the bug fix. Then,
you will have a second commit containing your PEP 8 changes.

The title of said commit can simply be `PEP 8`
