FROM bcit/centos:7
LABEL maintainer="jesse@weisner.ca"
LABEL build_id="1569537821"

ENV RUNUSER none
ENV HOME /
ENV _BUILDAH_STARTED_IN_USERNS=""
ENV BUILDAH_ISOLATION=chroot

VOLUME /var/lib/containers

RUN yum -y --setopt tsflags=nodocs --setopt timeout=5 install \
    buildah \
    podman \
 && rm -rf \
    /var/cache/* \
    /var/log/dnf* \
    /var/log/yum.* \
 && sed -i -e 's|^#mount_program|mount_program|g' -e '/additionalimage.*/a "/var/lib/shared",' /etc/containers/storage.conf \
 && mkdir -p /var/lib/shared/overlay-images /var/lib/shared/overlay-layers \
 && touch /var/lib/shared/overlay-images/images.lock \
 && touch /var/lib/shared/overlay-layers/layers.lock

