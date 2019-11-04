<div align="center">
    <h1>k8s-vagrant</h1>
    <img src="https://upload.wikimedia.org/wikipedia/commons/6/67/Kubernetes_logo.svg" width=50%></img>

<img src="https://www.vectorlogo.zone/logos/vagrantup/vagrantup-ar21.svg" width=20%><img>
<img src="https://www.vectorlogo.zone/logos/ansible/ansible-ar21.svg" width=20%></img>

<img src="https://img.shields.io/github/license/JoseCarlosNF/k8s-vagrant?style=for-the-badge"></img>

<img src="https://img.shields.io/github/forks/JoseCarlosNF/k8s-vagrant?style=flat-square"></img>
<img src="https://img.shields.io/github/stars/JoseCarlosNF/k8s-vagrant?style=flat-square"></img>
<img src="https://img.shields.io/github/issues/JoseCarlosNF/k8s-vagrant?style=flat-square"></img>
</div>

Provisionamento de cluster kubernetes, modelo bare-metal, para testes. Uma alternativa, ao minikube, mais próxima ao ambiente de produção.

## Requisitos

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-the-control-node)

## Arquivos

- [Vagrantfile](Vagrantfile)

- [Playbooks](Playbooks)
    - **Instalar Docker**
    - **Desabilitar *Swap***
    - **Instalar Kubernetes**: kubelet, kubeadm, kubectl
    - **Inicializar Cluster**: *apenas aplicável ao master*
    - **Configuração de Acesso ao cluster**: por questões de segurança, o acesso ao cluster deve ser feito por um usuario comun e não o *root*.
    - **Rede interna do cluster**: por meio de tal os conteiners do cluster poderão se comunicar.
    - **Adicionando Worker-Nodes**: Composto por duas etapas. A primeira é o registro de um comando no *Playbook*, e a segunda a execução desse comando individualmente por cada node a ser adicionado ao cluster.