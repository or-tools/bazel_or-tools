# Create a virtual environment with all tools installed
# ref: https://hub.docker.com/_/alpine
FROM alpine:edge AS env

# Install system build dependencies
ENV PATH=/usr/local/bin:$PATH
RUN apk add --no-cache git build-base linux-headers zlib-dev
RUN apk add --no-cache -X http://dl-cdn.alpinelinux.org/alpine/edge/testing bazel6

# Install OpenJDK17
# note: default-jvm will now point to java-17-openjdk
RUN apk add --no-cache openjdk17 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/
# Remove infinite loop since jre point to the current directory
# otherwise bazel issue an error and stop...
RUN rm /usr/lib/jvm/default-jvm/jre

ENV JAVA_HOME=/usr/lib/jvm/default-jvm
ENV PATH=$JAVA_HOME/bin:$PATH

FROM env AS devel
WORKDIR /home/project
COPY . .

FROM devel as build
RUN bazel version
RUN bazel build \
 -c opt \
 --host_javabase=@local_jdk//:jdk \
 //main:all

FROM build as test
RUN bazel test \
 -c opt \
 --host_javabase=@local_jdk//:jdk \
 --test_output=all \
 //main:all
