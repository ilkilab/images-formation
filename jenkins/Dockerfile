#v0.1 10/07/2023
FROM jenkins/jenkins:2.413
USER root
RUN apt update && apt install ca-certificates curl gnupg -yqq
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN chmod a+r /etc/apt/keyrings/docker.gpg
RUN echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt update && apt install -yqq docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
RUN usermod -aG docker jenkins
USER jenkins
