# JupyterHub with support for OSG.
#
# For use with Zero to JupyterHub for Kubernetes (https://z2jh.jupyter.org/).

FROM jupyterhub/k8s-hub:0.11.1

USER root

RUN apt-get update \
    && apt-get upgrade -y \
    #
    && apt-get install -y git \
    && git clone \
         ## For https://github.com/jupyterhub/oauthenticator/pull/503.
         https://github.com/jupyterhub/oauthenticator.git \
         /build/oauth \
    && python3 -m pip install -U --no-cache-dir /build/oauth \
    && rm -rf /build/ \
    && apt-get remove -y git \
    #
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --no-cache-dir osg-jupyter==1.0.0

USER jovyan
