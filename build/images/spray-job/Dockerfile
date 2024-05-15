ARG SPRAY_TAG=v0.2.1
ARG REPO=kubean-io
FROM ghcr.m.daocloud.io/${REPO}/spray-job:${SPRAY_TAG}

WORKDIR /kubespray

COPY playbooks/ /kubespray/
COPY main.yml /kubespray/roles/kubernetes/preinstall/handlers/main.yml
