# docker build -t heaplab:ubuntu18.04 .
# docker run --rm -v $PWD:/pwd --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -d --name heaplab_18 -i heaplab:ubuntu18.04
# docker exec -it heaplab_18 /bin/bash

FROM ubuntu:18.04
ENV LC_CTYPE C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive
RUN dpkg --add-architecture i386 && \
apt-get update && \
apt-get install -y build-essential strace ltrace gcc netcat gcc-multilib net-tools vim gdb gdb-multiarch python python3 python3-pip python3-dev libssl-dev libffi-dev git make procps libpcre3-dev libdb-dev libxt-dev libxaw7-dev python-pip libc6:i386 libncurses5:i386 libstdc++6:i386 && \
pip install pwntools && \
git clone https://github.com/pwndbg/pwndbg && cd pwndbg && ./setup.sh 