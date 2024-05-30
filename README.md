## Deploying-Cloud-Native-Applications

### WSL(Windows Subsystem for Linux)

https://learn.microsoft.com/ko-kr/windows/wsl/install

    # Command Prompt
    wsl --update
    wsl --list --online
    wsl --install Ubuntu-22.04
    # Reboot

### Visual Stdio Code & Extensions

Install Visual Studio Code(https://code.visualstudio.com/download)

    WSL(or Remote - SSH) - Extension
    # Create Ubunt-22.04
    # After jdk 17
    Extension Pack for Java - Extension
    Gradle for Java - Extension
    Spring Boot Extension Pack - Extension

### Init & Java

    $ sudo apt install zip nano vim git
    $ curl -s "https://get.sdkman.io" | bash
    $ sdk list java
    $ sdk install java 17.0.3-tem
    $ sdk default java 17.0.3-tem
    $ java --version
    $ sdk use java 17.0.3-tem
    $ sdk current java
    $ nano ~/.bashrc
    export JAVA_HOME=/home/user1/.sdkman/candidates/java/current

### Docker

https://docs.docker.com/engine/install/ubuntu/

    # Add Docker's official GPG key:
    sudo apt-get update
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc

    # Add the repository to Apt sources:
    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
      $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update

    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    sudo docker run hello-world

https://docs.docker.com/engine/install/linux-postinstall/

    $ sudo groupadd docker
    $ sudo usermod -aG docker $USER
    # Logout -> Login
    $ newgrp docker
    $ docker run hello-world

    # Security Issues
    $ sudo chmod 666 /var/run/docker.sock
    
    $ docker login
    $ docker pull ubuntu:22.04

### Minikube

https://minikube.sigs.k8s.io/docs/start/

    $ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    $ sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
    
    $ minikube start --driver=docker
    $ minikube config set driver docker

### Kubectl

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

    $ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    $ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
    
    $ kubectl get nodes

### Checklist for example execution

    $ cd ~/cloud-native-spring-in-action-sb-3-main
    $ find ./ -type f -name 'gradlew' -exec chmod 755 {} \;

### Httpie

https://httpie.io/

https://httpie.io/docs/cli/debian-and-ubuntu

    # Install httpie
    curl -SsL https://packages.httpie.io/deb/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/httpie.gpg
    echo "deb [arch=amd64 signed-by=/usr/share/keyrings/httpie.gpg] https://packages.httpie.io/deb ./" | sudo tee /etc/apt/sources.list.d/httpie.list > /dev/null
    sudo apt update
    sudo apt install httpie

    # Upgrade httpie
    sudo apt update && sudo apt upgrade httpie

    $ http pie.dev/get

### grype 

https://github.com/anchore/grype

    $ curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sudo sh -s -- -b /usr/local/bin

### Tilt

https://docs.tilt.dev/install.html

    $ curl -fsSL https://raw.githubusercontent.com/tilt-dev/tilt/master/scripts/install.sh | bash

### Octant

https://reference.octant.dev/?path=/story/docs-intro--page

    # download https://github.com/vmware-archive/octant/releases
    # sudo dpkg -i octant_0.x.x_Linux-64bit.deb
    $ sudo dbkg -i octant_0.25.1_Linux-64bit.deb

### Kubeval

https://github.com/instrumenta/kubeval(deprecated)

https://github.com/yannh/kubeconform?tab=readme-ov-file

    # download https://github.com/yannh/kubeconform/releases
    $ tar xvfz kubeconform-linux-amd64.tar.gz
    $ sudo mv kubeconform /usr/local/bin

### Knative

https://knative.dev/docs/install/quickstart-install/#before-you-begin

    $ mv <path-to-binary-file> kn
    $ chmod +x kn
    $ sudo mv kn /usr/local/bin
    $ kn version
    
### Sources

https://github.com/ThomasVitale/cloud-native-spring-in-action/tree/sb-3-main

