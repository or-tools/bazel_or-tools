# Create a virtual environment with all tools installed
# ref: https://hub.docker.com/_/fedora
FROM fedora:latest AS env

# Install system build dependencies
ENV PATH=/usr/local/bin:$PATH
RUN dnf -y update \
&& dnf -y install git \
&& dnf -y groupinstall "Development Tools" \
&& dnf -y install gcc-c++ zlib-devel \
&& dnf -y install dnf-plugins-core \
&& dnf -y copr enable vbatts/bazel \
&& dnf -y install bazel4 \
&& dnf clean all

FROM env AS devel
WORKDIR /home/project
COPY . .

FROM devel as build
RUN bazel version
RUN bazel build -c opt --cxxopt=-std=c++20 //main:template

FROM build as test
RUN bazel test --test_output=all -c opt --cxxopt=-std=c++20 //main:all
