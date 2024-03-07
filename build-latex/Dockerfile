FROM ubuntu:latest
WORKDIR /tmp
ENV TZ=Europe/Berlin
ENV DEBIAN_FRONTEND noninteractive

# set timezone
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# update system and install necessary software
RUN apt-get update && apt-get install -y \
    fontconfig \
    git \
    inkscape \
    python3-pygments \
    sudo \
    ttf-mscorefonts-installer \
    wget \
 && rm -rf /var/lib/apt/lists/* \
 && apt-get upgrade -y

# install texlive with medium scheme
RUN wget https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz; \
    zcat < install-tl-unx.tar.gz | tar xf -; \
    cd install-tl-202*; \
    perl ./install-tl --scheme=medium --no-doc-install --no-src-install --no-interaction; \
    cd ..; \
    rm -rf install-tl-202*; \
    rm -rf install-tl-unx.tar.gz;

ENV MANPATH="/usr/local/texlive/2023/texmf-dist/doc/man:${MANPATH}"
ENV INFOPATH="/usr/local/texlive/2023/texmf-dist/doc/info:${INFOPATH}"
ENV PATH="/usr/local/texlive/2023/bin/x86_64-linux:${PATH}"

# install necessary latex packages
RUN tlmgr install \
    biber \
    biblatex \
    biblatex-ieee \
    blindtext \
    cmbright \
    csquotes \
    enumitem \
    environ \
    glossaries \
    glossaries-german \
    minted \
    mnsymbol \
    ninecolors \
    pdfcol \
    pgfplots \
    pict2e \
    svg \
    tabularray \
    tcolorbox \
    tikzfill \
    todonotes \
    transparent \
    upquote \
    was \
    wrapfig2 \
    xurl

# create sudo user latex and use it
RUN useradd -m latex -s /bin/bash \
    && echo "latex:latex" | chpasswd \
    && adduser latex sudo \
    && echo 'latex ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
    
USER latex