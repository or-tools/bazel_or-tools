# Create a virtual environment with all tools installed
# ref: https://hub.docker.com/_/alpine
FROM alpine:edge AS env

# Install system build dependencies
ENV PATH=/usr/local/bin:$PATH
RUN apk add --no-cache git build-base linux-headers zlib-dev
RUN apk add --no-cache -X http://dl-cdn.alpinelinux.org/alpine/edge/testing bazel7

# Install OpenJDK17
# note: default-jvm will now point to java-17-openjdk
RUN apk add --no-cache openjdk17 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/
# Remove infinite loop since jre point to the current directory
# otherwise bazel issue an error and stop...
RUN rm /usr/lib/jvm/default-jvm/jre

ENV JAVA_HOME=/usr/lib/jvm/default-jvm
ENV PATH=$JAVA_HOME/bin:$PATH

# Install Python
RUN apk add --no-cache openssl python3-dev py3-pip py3-wheel
RUN python3 -m pip install --break-system-package absl-py mypy-protobuf

FROM env AS devel
WORKDIR /home/project
COPY . .

FROM devel AS build
RUN bazel version
RUN bazel build \
 -c opt \
 --host_javabase=@local_jdk//:jdk \
 ...

FROM build AS test
RUN bazel test \
 -c opt \
 --host_javabase=@local_jdk//:jdk \
 --test_output=all \
 ...
