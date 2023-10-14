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

### - Vscode Install

```
sudo apt update
sudo apt install snapd
sudo snap install code --classic

```

https://www.golinuxcloud.com/install-visual-studio-code-ubuntu-22/

