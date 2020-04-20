# csm-61c

The central repository for CSM 61C worksheets.

The repository is split up into two subsections. `src` denotes the current set
of worksheet templates which draw their questions from the pool of `topics`.

The style is provided by `commonheader.sty`.

## Deployed Handouts

* [Mentoring 3](https://csmberkeley.github.io/csm-61c/mentor03.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor03_sol.pdf))
* [Mentoring 4](https://csmberkeley.github.io/csm-61c/mentor04.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor04_sol.pdf))
* [Mentoring 5](https://csmberkeley.github.io/csm-61c/mentor05.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor05_sol.pdf))
* [Mentoring 6](https://csmberkeley.github.io/csm-61c/mentor06.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor06_sol.pdf)) 
* [Mentoring 7](https://csmberkeley.github.io/csm-61c/mentor07.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor07_sol.pdf)) 
* [Mentoring 8](https://csmberkeley.github.io/csm-61c/mentor08.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor08_sol.pdf))   
* [Mentoring 9](https://csmberkeley.github.io/csm-61c/mentor09.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor09_sol.pdf))   
* [Mentoring 10](https://csmberkeley.github.io/csm-61c/mentor10.pdf)
  ([Solution](https://csmberkeley.github.io/csm-61c/mentor10_sol.pdf)) 
  
## Making Handouts

To make an individual worksheet, run the following command in the repository's
root directory.

    make mentor00

To make multiple worksheets at once, modify the `Makefile` by adding the names
of the worksheets you'd like to make, and the solutions as necessary.

    RELEASED = mentor00 mentor01 mentor02
    SOLUTIONS = mentor00 mentor01

Then, run `make all` to build all the worksheets in the `published` directory.

If necessary, clean the local files with `make clean`.

## Contributing

### Get LaTeX

To contribute, first [get LaTeX](https://www.latex-project.org/get/). This
repository requires additional packages which may not be included in all basic
LaTeX distributions, especially the monospace font
[Inconsolata](https://www.ctan.org/pkg/inconsolata). In Ubuntu's TeXLive
distribution, the font can be found in the `texlive-latex-extra` package.

If you do not already have LaTeX installed and would prefer the most minimal
installation necessary, [obtain LaTeX from
CTAN](https://www.latex-project.org/get/#ctan) and adapt the `.texlive.sh`
script and `.texlive.profile` configuration for your needs.

For Mac, install Mactex (http://www.tug.org/mactex/).

### Branch off `master`

After cloning the repository and setting up LaTeX, pull in any updates from
Github `origin`.

    git checkout master
    git pull

Then, create a new branch off `master` and give it a descriptive name.

    git checkout -b fa17/mentor04

### Make changes

Make changes as you would normally and commit them incrementally. Write
descriptive commit messages and break larger changes into smaller parts.

Using patch mode is recommended when staging changes to ensure only that only
the desired diffs are included in the commit.

    git add -p

Start in the `src` directory and edit the handouts in question. Note that the
repository has split up handouts from their questions: all questions are stored
in individual files under `topics` for version control and maintainability.

After making a few changes, verify that the changes appear as expected by
re-making the handouts. The handouts build to the `published` directory.

    make clean && make mentor04 && make mentor04_sol

Once satisfied, push the branch to Github `origin`.

    git push -u origin fa17/mentor04

### Pull request

On the Github web interface, create a new pull request for the branch, assign
the current maintainers for review, apply relevant labels, and set the
milestone to the current release target.

Travis will automatically spin up a new build for the branch and perform a
status check to verify that the handouts compile successfully. If there are
errors, you may want to double check that all the handouts build locally.

    make src

Once the changes have been accepted by a maintainer, they can be merged into
the `master` branch. This will spin up another Travis build and automatically
publish the updated handouts to Github Pages within a few minutes.