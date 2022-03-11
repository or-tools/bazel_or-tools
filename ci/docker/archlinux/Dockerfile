# Create a virtual environment with all tools installed
# ref: https://hub.docker.com/_/archlinux/
FROM archlinux:latest AS env

# Install system build dependencies
ENV PATH=/usr/local/bin:$PATH
RUN pacman -Syu --noconfirm git base-devel bazel

FROM env AS devel
WORKDIR /home/project
COPY . .

FROM devel as build
RUN bazel version
RUN bazel build -c opt --cxxopt=-std=c++20 //main:template

FROM build as test
RUN bazel test --test_output=all -c opt --cxxopt=-std=c++20 //main:all
