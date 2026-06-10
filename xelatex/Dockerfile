# syntax=docker/dockerfile:1.4
#
# rmd-xelatex -- R Markdown to PDF render image.
#
# Extends rocker/tidyverse with a system TeX Live installation.
# Uses Debian texlive packages rather than TinyTeX: no lazy downloads,
# no tlmgr calls at render time, fully deterministic in CI.
#
# Packages installed:
#   texlive-xetex             xelatex engine and unicode/font support
#   texlive-latex-extra       booktabs, lineno, setspace, xcolor, fancyhdr,
#                             enumitem, and several hundred others
#   texlive-fonts-recommended lm, cm-super, and standard font sets
#   texlive-plain-generic     etoolbox, xkeyval, and low-level generics
#
# Usage (render a single report):
#   docker run --rm \
#     -v /path/to/project:/project \
#     -w /project/analysis/report/01-slug \
#     ghcr.io/rgt47/rmd-xelatex:4.6.0 \
#     Rscript -e "rmarkdown::render('report.Rmd', output_format='pdf_document')"

ARG R_VERSION=4.6.0
FROM rocker/tidyverse:${R_VERSION}

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      texlive-xetex \
      texlive-latex-extra \
      texlive-fonts-recommended \
      texlive-plain-generic \
 && rm -rf /var/lib/apt/lists/*

RUN R -e "install.packages('renv')"
