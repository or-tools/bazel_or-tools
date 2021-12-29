# Create a virtual environment with all tools installed
# ref: https://hub.docker.com/r/opensuse/tumbleweed
FROM opensuse/tumbleweed AS env
LABEL maintainer="corentinl@google.com"
# Install system build dependencies
ENV PATH=/usr/local/bin:$PATH
RUN zypper update -y \
&& zypper install -y git gcc gcc-c++ zlib-devel bazel \
&& zypper clean -a
ENV CC=gcc CXX=g++

FROM env AS devel
WORKDIR /home/lib
COPY . .

FROM devel as build
RUN bazel version
RUN bazel build -c opt --cxxopt=-std=c++17 //main:template

FROM build as test
RUN bazel test --test_output=all -c opt --cxxopt=-std=c++17 //main:all
