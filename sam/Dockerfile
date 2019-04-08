FROM mobingi/aws-codebuild-docker-images:latest

RUN useradd -m -s /bin/bash builduser

USER builduser
ENV LANG=C
WORKDIR /home/builduser
ENV HOME=/home/builduser

RUN git clone --depth 1 https://github.com/Homebrew/brew ~/.linuxbrew/Homebrew \
  &&  mkdir ~/.linuxbrew/bin \
  && ln -s ../Homebrew/bin/brew ~/.linuxbrew/bin \
  && eval $(~/.linuxbrew/bin/brew shellenv) \
  && brew tap aws/tap \
  && brew install aws-sam-cli \
  && test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile \
  && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.profile
