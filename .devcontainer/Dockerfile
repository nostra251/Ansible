# Utiliser une image de base compatible ARM 
FROM arm64v8/debian:bullseye-slim

# Installer les dépendances de base
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip python3-venv \
    sshpass \
    git \
    openssh-client \
    curl \
    vim \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Installer Ansible via pip
RUN pip3 install --no-cache-dir ansible

# Configuration de l'utilisateur pour SSH (optionnel)
RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# Configurer le prompt pour afficher l'emplacement actuel
RUN echo 'export PS1="\u@\h:\w\$ "' >> /etc/bash.bashrc

# Définir un point d'entrée par défaut pour utiliser Ansible
ENTRYPOINT ["ansible"]

# Créer et configurer un répertoire de travail pour Ansible
WORKDIR /ansible

# Configurer les permissions (optionnel, utile si vous partagez des volumes avec des permissions spécifiques)
RUN mkdir -p /ansible && chmod 755 /ansible


