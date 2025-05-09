FROM paperist/texlive-ja:latest
RUN apt update && apt install -y git && apt install -y build-essential
RUN cpan -i App::cpanminus && cpanm YAML::Tiny && cpanm File::HomeDir
RUN wget -P "/sty" "https://raw.githubusercontent.com/h-kitagawa/plistings/master/plistings.sty"
RUN tlmgr update --self
RUN tlmgr install latexindent
CMD [ "bin/bash" ]
