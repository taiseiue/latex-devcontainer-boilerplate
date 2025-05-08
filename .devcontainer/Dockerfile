FROM paperist/texlive-ja:latest
RUN wget -P "/sty" "https://raw.githubusercontent.com/h-kitagawa/plistings/master/plistings.sty"
RUN tlmgr update --self
RUN apt update && apt install -y git
CMD [ "bin/bash" ]
