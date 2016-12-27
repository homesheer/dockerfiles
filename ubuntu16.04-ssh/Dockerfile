# ==============================================================================
# homesheer/ubuntu16.04-ssh
#
# 有ssh的ubuntu16.04基础镜像
# ==============================================================================

FROM ubuntu:16.04
#FROM registry.mirrors.aliyuncs.com/library/ubuntu:16.04

MAINTAINER homesheer <homesheer@qq.com>

# ------------------------------------------------------------------------------
# 配置apt源为阿里云源
# ------------------------------------------------------------------------------
RUN mv /etc/apt/sources.list /etc/apt/sources.list.backup
ADD sources.list /etc/apt/sources.list
RUN apt-get clean
RUN apt-get update

# ------------------------------------------------------------------------------
# 安装SSH服务
# ------------------------------------------------------------------------------
RUN apt-get install -y openssh-server
RUN mkdir -p /var/run/sshd

# ------------------------------------------------------------------------------
# 密码登陆
# ------------------------------------------------------------------------------
#RUN echo 'root:666666' | chpasswd
#RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
#RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

# ------------------------------------------------------------------------------
# 认证登陆
# ------------------------------------------------------------------------------
RUN sed -ri 's/session    required     pam_loginuid.so/#session    required     pam_loginuid.so/g' \
    /etc/pam.d/sshd
RUN mkdir -p /root/.ssh
ADD authorized_keys /root/.ssh/authorized_keys

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
