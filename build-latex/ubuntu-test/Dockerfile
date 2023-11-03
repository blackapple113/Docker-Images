FROM ubuntu:latest
WORKDIR /tmp
ENV TZ=Europe/Berlin
ENV DEBIAN_FRONTEND noninteractive

# set timezone
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# update system
RUN apt update && apt upgrade -y

# install latex and latexmk
RUN apt install -y texlive-xetex texlive-science texlive-publishers texlive-pstricks texlive-plain-generic texlive-pictures texlive-music texlive-metapost texlive-luatex texlive-latex-recommended texlive-latex-extra texlive-latex-base texlive-lang-spanish texlive-lang-german texlive-lang-english texlive-humanities texlive-games texlive-formats-extra texlive-fonts-recommended texlive-fonts-extra texlive-font-utils texlive-extra-utils texlive-bibtex-extra texlive-base texlive latexmk

# install pygments for latex package minted
RUN apt install -y python3-pygments

# install inkscape for latex package svg
RUN apt install -y inkscape

# install microsoft fonts to use with drawio svg graphics
RUN apt install -y ttf-mscorefonts-installer fontconfig