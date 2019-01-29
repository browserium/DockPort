FROM centos:latest

MAINTAINER corefinder89 "soumyajit.basu62@gmail.com"

# Execute to install python dependencies and set up the container
RUN yum install -y epel-release \
    yum -y groupinstall "Development tools" \
    yum update -y  && yum install -y \
        which \
        mesa-dri-drivers \
        libexif \
        libcanberra-gtk2 \
        libcanberra \
        python-devel \
        python-pip \
        python-wheel \
        python-setuptools && \
    yum upgrade -y python-setuptools

# Install chrome
WORKDIR opt
ADD https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm /root/google-chrome-stable_current_x86_64.rpm
RUN yum -y install /root/google-chrome-stable_current_x86_64.rpm; yum clean all

RUN cd ..

# Install firefox
RUN yum -y install firefox

# Run the pip configurations
RUN pip install --upgrade pip \
                docutils

# Install module browserium
RUN pip install browserium==1.2.2

# Check if chrome and firefox is completely installed
RUN which firefox
RUN which google-chrome

CMD ["/bin/bash"]
