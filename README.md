# k8sOnboard

#Presenting
The objective of the file is presenting k8s onboard (toolling, configuration, urls)


##Content

## Machine configuration

### - Add user to sudoers file
1 - su + sua senha (For change your user)

2 - sudo nano /etc/sudoers (For edit the permition user file)

3 - A baixo da linha onde se encontra essa frase: ==> %sudo ALL=(ALL:ALL) ALL

Você escreve em baixo:

nomeUsuario ALL=(ALL) ALL (Agora seu user tem acesso root)

5 - Ctrl + O (Salvar) 6 - Ctrl + X (Fechar ) 7 - Ctrl + D (Sair do modo root) 

ref (https://cursos.alura.com.br/forum/topico-sugestao-resolvido-user-is-not-in-the-sudoers-file-this-incident-will-be-reported-259842)



## Tooling install

### - Git Install 
```
sudo apt install git
```

- ***Add pass***
    1. Create personal CESS token
        1. Generate new token
        1. Copy de token in your clipeboard
        1. Use in push


### - Vscode Install

```
sudo apt update
sudo apt install snapd
sudo snap install code --classic

```

https://www.golinuxcloud.com/install-visual-studio-code-ubuntu-22/


### - Instalação docker

1. Set up Docker's Apt repository

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
2. Install the Docker packages.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

```

3. Verify that the Docker Engine installation is successful by running the hello-world image.

```
sudo docker run hello-world
```

link: https://docs.docker.com/engine/install/ubuntu/


### Install Minikube

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

chmod +x ./minikube

sudo mv ./minikube /usr/local/bin/minikube

minikube version
```

### Install Kubectl

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

kubectl version --client
```


### Install Helm
```
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```


### Istio


1. Step #1: Add Istio repository to Helm

```
helm repo add istio https://istio-release.storage.googleapis.com/charts
```

```
helm repo update
```

2. Step #2: Install Istio base chart
```
helm install istio-base istio/base -n istio-system --create-namespace --set defaultRevision=default
```

3. Step #3: Install Istio control plane
```
helm install istiod istio/istiod -n istio-system --wait
```

4. Verify Istio base and Istiod deployment status

```
helm ls -n istio-system
```

```
kubectl get deployments -n istio-system -o wide
```

link: https://imesh.ai/blog/how-to-install-istio-using-helm-chart/