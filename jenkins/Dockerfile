#v0.1 10/07/2023
FROM jenkins/jenkins:2.413
USER root
#installation de docker
RUN apt update && apt install ca-certificates curl gnupg -yqq
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN chmod a+r /etc/apt/keyrings/docker.gpg
RUN echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt update && apt install -yqq docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
#ajout de droits pour l'utilisateur jenkins
RUN usermod -aG docker jenkins
VOLUME /var/run/docker.sock:/var/run/docker.sock
RUN chgrp docker /var/run/docker.sock
#installation de kubectl
RUN curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | gpg --dearmor -o /etc/apt/keyrings/kubernetes-archive-keyring.gpg
RUN echo "deb [signed-by=/etc/apt/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list
RUN apt update && apt install kubectl
USER jenkins
