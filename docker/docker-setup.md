# Instale o Docker em menos de 3 minutos

Essa é a forma mais rápida e fácil de instalar o Docker no Ubuntu.

## Tutorial em vídeo
Os comandos abaixo foram usados no vídeo do meu canal `ABC DevOps`, confira:


## Instalando Docker
Baixe o script
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

Rode o instalador
```bash
sudo sh get-docker.sh
```


### Adicionando usuário no grupo Docker
Rode o seguinte comando
```bash
sudo usermod -aG docker $USER
```

Para fazer efeito, faça logout do seu usuário ou reiniciei sua máquina.

> Caso você não faça o procedimento, terá que rodar o comando `docker` com `sudo`

## Instalando Docker Compose
Você tem duas opções na hora de instalar o Docker Compose

1. Instalar usando `apt`
```bash
sudo apt update && sudo apt install -y docker-compose
```

2. Baixando o executável diretamente
```bash
sudo curl -SL https://github.com/docker/compose/releases/download/v2.15.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```


## Testando

### Conferindo se o docker está funcional
Rode o comando
```bash
sudo docker -v
```

Você terá uma saída similar à essa:
```bash
Docker version 20.10.14, build a224086
```

### Conferindo se o docker-compose está funcional
Rode o comando
```bash
docker-compose -v
```

Você terá uma saída similar à essa
```bash
docker-compose version 1.29.2, build 5becea4c
```


## Fontes
https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script  
https://docs.docker.com/engine/install/linux-postinstall/  
https://docs.docker.com/compose/install/other/  