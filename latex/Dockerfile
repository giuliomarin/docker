FROM ubuntu:trusty
MAINTAINER Giulio Marin

# Install latex
RUN apt-get update -q
RUN apt-get install -qy texlive-full

# Create script to run application with xvfb
RUN echo 'pdflatex "$@"; bibtex "$@"; pdflatex "$@"; pdflatex "$@"' > /bin/biblatex
RUN chmod 777 /bin/biblatex

# Set working dir
WORKDIR /home
