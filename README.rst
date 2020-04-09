================================================================================
  The pdflatex executable in a Docker Container
================================================================================

Dockerfile to create an image containing:

- pdflatex executable (from TinyTeX)
- tlmgr executable (from TinyTeX) for installing TeX dependencies
- Python 3 with Pygments installed so that the minted TeX package can shell out
  to Python for code example colorization.
- On Ubuntu 16

The goal of this environment is to allow for the reliable creation of PDFs from
LaTeX source documents that uses the minted TeX package (which requires Python
with the Pygments package.)

Build with tag ``pdflatex``::

    $ docker build -t pdflatex .

Suppose you have a LaTeX document at ``/path/to/tex/docs.tex`` from which you
want to create a PDF. Run::

    $ docker run -v "/path/to/tex:/mnt/tex" \
          pdflatex \
          sh -c "cd /mnt/tex/; pdflatex --shell-escape docs.tex"
