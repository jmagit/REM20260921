FROM jenkins/jenkins:latest
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
USER jenkins
RUN jenkins-plugin-cli --plugins "cloudbees-folder antisamy-markup-formatter build-timeout credentials-binding timestamper ws-cleanup ant gradle workflow-aggregator github-branch-source pipeline-github-lib pipeline-graph-view git ssh-slaves matrix-auth ldap email-ext mailer dark-theme blueocean docker-workflow coverage htmlpublisher sonar job-dsl maven-plugin pipeline-maven thinBackup"
