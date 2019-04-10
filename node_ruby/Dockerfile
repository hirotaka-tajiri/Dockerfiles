# node_ruby
#
# VERSION              0.0.2

FROM centos

LABEL name="node(express with passport) AND ruby cli
script(mysql2,rubyXL) Image" \
            license="GPLv2" \
            build-date="20190312"
# yum
RUN yum -y install curl wget which mariadb-devel && yum -y upgrade &&
yum clean all && mkdir -p /container_dat

# node
RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh 
| bash
RUN export NVM_DIR="$HOME/.nvm" && /bin/bash $HOME/.nvm/nvm.sh  &&
/bin/bash $HOME/.nvm/bash_completion
RUN source ~/.bash_profile && nvm install stable && npm update -g npm
&& cd /container_dat && npm install express express-flash
express-session body-parser cookie-parser cookie-session crypto
date-utils debug ejs http-errors morgan mysql mysql-model passport
passport-local serve-favicon -g

# rvm
RUN curl -sSL https://rvm.io/mpapis.asc | gpg2 --import - && curl -sSL
https://rvm.io/pkuczynski.asc | gpg2 --import - && curl -sSL
https://get.rvm.io | bash -s stable
RUN source /etc/profile.d/rvm.sh && source ~/.bash_profile &&
/usr/local/rvm/bin/rvm install ruby-2.6.0
RUN su -c "source /etc/profile.d/rvm.sh && rvm use ruby-2.6.0
--default && gem install -N bundler json rspec rubyXL mysql2 && gem
clean"

VOLUME /container_dat

EXPOSE 1337
CMD ["/container_dat/express/express_start.sh"]
