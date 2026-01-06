#
# ビルドステージ
#
FROM paperist/texlive-ja:2024-debian AS builder
RUN apt-get update && apt-get install -y --no-install-recommends git perl cpanminus build-essential
# 関係するcpanモジュールをインストール
RUN cpanm --notest App::cpanminus YAML::Tiny File::HomeDir
# plistings.styをインストール
RUN mkdir -p /usr/local/texlive/texmf-local/tex/latex/local \
    && wget -O /usr/local/texlive/texmf-local/tex/latex/local/plistings.sty "https://raw.githubusercontent.com/h-kitagawa/plistings/master/plistings.sty"
# TexLiveのパッケージをインストール
RUN mktexlsr \
    && tlmgr update --self --all \
    && tlmgr install algorithms algorithmicx algpseudocodex latexindent

#
# DevContainer向けステージ
#
FROM paperist/texlive-ja:2024-debian

ARG USER=latex

RUN apt-get update && \
    apt-get install -y --no-install-recommends sudo git gnupg2 openssh-client chktex

# Create user and set up sudoers
RUN groupadd -g 1000 ${USER} && \
    useradd -m -u 1000 -g ${USER} ${USER} && \
    echo "${USER} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/${USER} && \
    chmod 0440 /etc/sudoers.d/${USER}

COPY --from=builder --chown=${USER}:${USER} /usr/local/texlive /usr/local/texlive
COPY --from=builder --chown=${USER}:${USER} /usr/local/share/perl /usr/local/share/perl

USER ${USER}
CMD [ "bin/sh" ]
