#
# ビルドステージ
#
FROM paperist/texlive-ja:latest AS builder
RUN apt update && apt install -y --no-install-recommends git perl cpanminus build-essential 
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
FROM paperist/texlive-ja:latest
COPY --from=builder /usr/local/texlive /usr/local/texlive
COPY --from=builder /usr/local/share/perl /usr/local/share/perl
RUN apt update && apt install -y --no-install-recommends git gnupg2
CMD [ "bin/sh" ]
