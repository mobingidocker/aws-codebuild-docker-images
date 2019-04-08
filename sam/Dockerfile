FROM mobingi/aws-codebuild-docker-images:latest

RUN apt-get install -y locales
RUN useradd -m -s /bin/bash builduser
RUN echo "LC_ALL=en_US.UTF-8" >> /etc/environment \
  && echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
  && echo "LANG=en_US.UTF-8" > /etc/locale.conf \
  && locale-gen en_US.UTF-8

USER builduser
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
