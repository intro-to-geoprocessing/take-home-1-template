FROM jupyterhub/singleuser:1.2.1

# binder dep
# RUN pip install --no-cache-dir notebook==5.* jupyterhub

# ARG NB_USER=jovyan
# ARG NB_UID=1000
# ENV USER ${NB_USER}
# ENV NB_UID ${NB_UID}
# ENV HOME /home/${NB_USER}

# RUN adduser --disabled-password \
#     --gecos "Default user" \
#     --uid ${NB_UID} \
#     ${NB_USER}

USER root
WORKDIR ${HOME}

# System deps:
RUN apt-get update && apt-get install -y libspatialindex-dev

# Python deps:
COPY requirements.txt ${HOME}
RUN pip install --no-cache-dir -r requirements.txt

# Copy project files
COPY . ${HOME}
RUN chown -R ${NB_UID} ${HOME}
USER ${NB_USER}