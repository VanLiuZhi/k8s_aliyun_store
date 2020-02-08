FROM centos:centos7
LABEL author="liuzhi<1441765847@qq.com>"

# install related packages
ENV ENVIRONMENT DOCKER_PROD
RUN cd / && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
  && yum makecache \
  && yum install -y wget aclocal automake autoconf make gcc gcc-c++ python-devel mysql-devel bzip2 libffi-devel epel-release \
  && yum clean all

# install python 3.6.5
RUN wget https://npm.taobao.org/mirrors/python/3.6.5/Python-3.6.5.tar.xz \
  && tar -xvf Python-3.6.5.tar.xz -C /usr/local/ \
  && rm -rf Python-3.6.5.tar.xz \
  && cd /usr/local/Python-3.6.5 \
  && ./configure && make && make install

# install related packages
RUN yum install -y python-pip \
  && pip3 install --upgrade pip -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com \
  && pip3 install psutil \
  && pip3 install rrdtool \
  && yum clean all

# expost port
EXPOSE 15731