ARG SPRAY_TAG=v0.2.1
ARG REPO=kubean-io
FROM ghcr.m.daocloud.io/${REPO}/spray-job:${SPRAY_TAG}

WORKDIR /kubespray

COPY playbooks/ /kubespray/
COPY build/images/spray-job/main.yml /kubespray/roles/kubernetes/preinstall/handlers/main.yml
# 需要手动修改的地方
# 1、修改os-release文件
  #ID="fedora"
  #NAME="Fedora"
  #VERSION="2.00.00.00 (hardknott)"
  #VERSION_ID="8"
  #PRETTY_NAME="CentOS Linux"

#3、修改/etc/sysctl.d/99-sysctl.conf 注释掉 net/ipv4/tcp_syncookies=1
  #
#4、关闭ntp，修改ntp_enabled=false
# 适配acore-linux安装k8s
COPY playbooks/acore-linux/reset-main.yml /kubespray/roles/reset/tasks/main.yml
COPY playbooks/acore-linux/runc-main.yml /kubespray/roles/container-engine/runc/tasks/main.yml
COPY playbooks/acore-linux/bootstrap-centos.yml  /kubespray/roles/bootstrap-os/tasks/bootstrap-centos.yml
COPY playbooks/acore-linux/0010-swapoff.yml /kubespray/roles/kubernetes/preinstall/tasks/0010-swapoff.yml
COPY playbooks/acore-linux/0070-system-packages.yml /kubespray/roles/kubernetes/preinstall/tasks/0070-system-packages.yml
COPY playbooks/acore-linux/0062-networkmanager-unmanaged-devices.yml /kubespray/roles/kubernetes/preinstall/tasks/0062-networkmanager-unmanaged-devices.yml
