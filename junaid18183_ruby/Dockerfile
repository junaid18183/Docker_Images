FROM centos:centos6
MAINTAINER Juned Memon <junaid18183@gmail.com>

ENV RUBY_VERSION 2.1.2

#VOLUME /dashing_demo
#EXPOSE 3030

#WORKDIR /dashing_demo
#CMD ["/run.sh"]
#########################################################################
#sh sucks for setting profile and environment,get rid of it or use RUN /bin/bash -l -c
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

#Centos 6 needs which and tar, nodejs will require for dashing
RUN yum install -y which tar

#Install rootfiles package which provides the basic required files for the root user's directory like /root/.bash_profile
RUN yum install -y rootfiles

#Install RVM
RUN curl -L https://get.rvm.io | bash -s stable

RUN echo "source /usr/local/rvm/scripts/rvm" >> /etc/bash.bashrc

#Make rvm available to all users 
RUN /bin/bash -l -c 'rvm user all'

# Install package dependencies
RUN /bin/bash -l -c 'rvm requirements'

# Install ruby
RUN /bin/bash -l -c 'rvm install 2.1.2'
RUN /bin/bash -l -c 'rvm use 2.1.2 --default'

# Install bundle 
RUN /bin/bash -l -c 'gem install bundle'
