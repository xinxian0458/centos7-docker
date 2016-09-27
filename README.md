# centos7-docker

由于以下几个原因，docker的官方centos镜像中没有提供systemd服务:
systemd requires the CAP_SYS_ADMIN capability. This means running docker with --privileged. Not good for a base image.
systemd requires access to the cgroups filesystem.
systemd has a number of unit files that don’t matter in a container, and they cause errors if they’re not removed

但在可控环境下，我们还是希望使用systemd来管理我们的服务，如何开启systemd呢？
执行`docker build --rm -t centos:systemd .`来创建一个systemd base image.

执行`docker run -d -v /sys/fs/cgroup:/sys/fs/cgroup -e TERM=xterm --privileged centos:systemd`来启动一个带有systemd的centos容器.
