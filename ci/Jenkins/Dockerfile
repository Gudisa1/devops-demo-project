FROM jenkins/jenkins:lts-jdk17

# Switch to root to install Maven and Docker
USER root

# Install Maven
RUN apt-get update && apt-get install -y maven

# Ensure Maven is added to PATH permanently
RUN echo "export PATH=/usr/share/maven/bin:\$PATH" > /etc/profile.d/maven.sh && \
    chmod +x /etc/profile.d/maven.sh

# Install Docker
RUN apt-get update && \
    apt-get install -y \
    ca-certificates \
    curl \
    sudo \
    docker.io && \
    usermod -aG docker jenkins

# Switch back to Jenkins user
USER jenkins

# Expose Jenkins port
EXPOSE 8080
