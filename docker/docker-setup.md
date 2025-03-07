# Instale o Docker em menos de 3 minutos

Essa é a forma mais rápida e fácil de instalar o Docker no Ubuntu.

## Tutorial em vídeo
Os comandos abaixo foram usados no vídeo do meu canal `ABC DevOps`

## Antes de começar
Instale o `curl` se você não tiver 
```bash
sudo apt install curl
```

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

## Testando

### Conferindo se o docker está funcional
Rode o comando
```bash
docker run hello-world
```



## Fonte
https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script  
https://docs.docker.com/engine/install/linux-postinstall/  
https://docs.docker.com/compose/install/other/  