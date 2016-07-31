FROM ubuntu:trusty
MAINTAINER Giulio Marin

# Install latex
RUN apt-get update -q
RUN apt-get install -qy texlive-full

# Compile files with bibliography
RUN echo \
  'pdflatex --output-directory=/latex/tmp "$1";\
  echo ---------------------;\
  cp ./*.bib /latex/tmp/;\
  cp ./*.bst /latex/tmp/;\
  cd /latex/tmp;\
  bibtex "$1";\
  cd /latex/source;\
  echo ---------------------;\
  pdflatex --output-directory=/latex/tmp "$1";\
  echo ---------------------;\
  pdflatex --output-directory=/latex/tmp "$1";\
  cp /latex/tmp/"$1".pdf /latex/source/'\
  > /bin/mybiblatex
RUN chmod 777 /bin/mybiblatex

# Compile without bibliography
RUN echo \
  'pdflatex --output-directory=/latex/tmp "$1";\
  cp /latex/tmp/"$1".pdf /latex/source/'\
  > /bin/mypdflatex
RUN chmod 777 /bin/mypdflatex

RUN mkdir -p /latex/tmp

# Set working dir
WORKDIR /latex/source
