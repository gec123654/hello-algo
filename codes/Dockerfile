FROM ubuntu:latest

# Use Ubuntu image from Aliyun
RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list && \
    sed -i 's/security.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list && \
    sed -i 's/ports.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list

RUN apt-get update

# 设置需要安装的语言，使用空格隔开
# Set the languages to be installed, separated by spaces
ARG LANGS="python cpp"

# Available languages：python cpp java
RUN for LANG in $LANGS; do \
        case "$LANG" in \
            python) \
                apt-get install -y python3.10 && \
                update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1 ;; \
            cpp) \
                apt-get install -y g++ gdb ;; \
            java) \
                apt-get install -y openjdk-17-jdk ;; \
            # More languages...
            *) \
                echo "Warning: No installation workflow for $LANG" ;; \
        esac \
    done

WORKDIR /codes
COPY ./ ./

CMD ["/bin/bash"]
