# Docker file for mmp-dyf-skat docker image found here: https://hub.docker.com/r/ttimbers/mmp-dyf-skat/
# Tiffany Timbers, April 5, 2016

# use ubuntu:14.04 as base image
FROM ubuntu:14.04

# install base R
RUN sudo sh -c 'echo "deb http://cran.rstudio.com/bin/linux/ubuntu trusty/" >> /etc/apt/sources.list'
RUN gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
RUN sudo apt-get update
RUN sudo apt-get -y install r-base

# download & install R packages
RUN wget https://cran.r-project.org/src/contrib/dplyr_0.4.3.tar.gz
RUN wget https://cran.r-project.org/src/contrib/fdrtool_1.2.15.tar.gz
RUN wget https://cran.r-project.org/src/contrib/plyr_1.8.3.tar.gz
RUN wget https://cran.r-project.org/src/contrib/Archive/SKAT/SKAT_1.0.9.tar.gz
RUN wget https://cran.r-project.org/src/contrib/stringr_1.0.0.tar.gz
RUN R CMD INSTALL dplyr_0.4.3.tar.gz
RUN R CMD INSTALL fdrtool_1.2.15.tar.gz
RUN R CMD INSTALL plyr_1.8.3.tar.gz
RUN R CMD INSTALL SKAT_1.0.9.tar.gz
RUN R CMD INSTALL stringr_1.0.0.tar.gz

# install git
RUN apt-get install -y make git

# install plink
RUN apt-get install -y wget
RUN wget https://www.cog-genomics.org/static/bin/plink160224/plink_linux_x86_64.zip
RUN mkdir /usr/bin/plink/plink
RUN mv plink_linux_x86_64.zip /usr/bin/plink/plink
RUN unzip /usr/bin/plink/plink/plink_linux_x86_64.zip

# modify .bash_rc to put plink in the path
RUN echo PATH="/usr/bin/plink:$PATH" >> ~/.bashrc

# pull code and data from github
RUN git clone https://github.com/ttimbers/Million-Mutation-Project-dye-filling-SKAT.git /home/Million-Mutation-Project-dye-filling-SKAT