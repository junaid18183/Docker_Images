FROM junaid18183/ruby
MAINTAINER Juned Memon <junaid18183@gmail.com>


###############################################
# Install Dashing 
RUN /bin/bash -l -c 'gem install dashing'

#Create the dashing directory and create the dashing_demo project
RUN /bin/bash -l -c 'mkdir -p  /root/dashing-demo && cd /root/ && dashing new dashing-demo'
RUN /bin/bash -l -c 'cd /root/dashing-demo && bundle'

#Dashing requires nodejs and we require supervisor for managing it
RUN /bin/bash -l -c 'yum -y install nodejs supervisor.noarch'


# Change the workdir
WORKDIR /root/dashing-demo

#There are two options to start the daemon, 1) use supervisord and 2) use local script
#--------------------------------------------------------------------------------------#
#Option 1 use supervisord , not working for some reason
ADD supervisord-dashing.conf /etc/supervisord.conf
# Start supervisord in background when entering an interactive shell
#RUN echo "/usr/bin/supervisord" >> /etc/bash.bashrc  # for some reason /etc/bash.bashrc not working in centos 
#RUN echo "/usr/bin/supervisord" >> /etc/profile, however adding in /etc/profile ,container not starting
# Start supervisord as a foreground process when running without a shell i.e docker run  -p 49303:3030 -d -t junaid18183/dashing:latest
#CMD ["/usr/bin/supervisord", "-n"]
#--------------------------------------------------------------------------------------#
###Option 2 use local script, tested and works for both interactive and w/o shell
#for some reason /etc/bash.bashrc is not working 
# Start dashing with -d  in background when entering an interactive shell

RUN /bin/bash -l -c 'cd /root/dashing-demo && echo -e "source /etc/profile.d/rvm.sh\ndashing start -d" >> /etc/profile'

#execute the shell script when running without a shell i.e docker run  -p 49303:3030 -d -t junaid18183/dashing:latest
ADD run.sh /root/run.sh
CMD ["/root/run.sh"]
#--------------------------------------------------------------------------------------#
# open Dashing port
EXPOSE 3030 
