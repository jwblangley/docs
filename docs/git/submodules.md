# Submodules

Submodules are a powerful git feature that allows other git repositories to be used with a super-repository whilst maintaining individual version control.

These commands will help to quickly start using git submodules

* `git submodule add <remote>`: add a new git submodule
* `git submodule update`: checkout commited index of submodules
    * `--init`: also initialise git submodules. This is required after a new `git clone`
    * `--remote`: checkout the most recent commit for the submodules rather than the one in the index

Simply `cd` into the respective submodule directory to access git commands respective to that submodule.
