FROM ubuntu:trusty
MAINTAINER Giulio Marin

# Install latex
RUN apt-get update -q
RUN apt-get install -qy texlive-full

# Create script to run application with xvfb
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
  > /bin/biblatex
RUN chmod 777 /bin/biblatex

RUN mkdir -p /latex/tmp

# Set working dir
WORKDIR /latex/source
