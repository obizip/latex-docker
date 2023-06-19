FROM paperist/texlive-ja:debian

# XeTeX をインストールする場合の例
# RUN apt-get update \
#   && apt-get install -y \
#     libfontconfig1 \
#   && rm -rf /var/lib/apt/lists/*
# RUN tlmgr install collection-xetex ctex

ARG username=vscode
ARG useruid=1000
ARG usergid=${useruid}

RUN groupadd --gid ${usergid} ${username} && \
    useradd -s /bin/bash --uid ${useruid} --gid ${usergid} -m ${username}

RUN apt-get update \
  && apt-get install -y \
    locales locales-all \
    make cpanminus \
    texlive-extra-utils \
    --no-install-recommends

# RUN tlmgr update --self --all
RUN tlmgr install aligned-overset

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

# RUN cpanm Log::Dispatch::File YAML::Tiny File::HomeDir Unicode::GCString
RUN cpanm YAML::Tiny File::HomeDir
USER ${username}
