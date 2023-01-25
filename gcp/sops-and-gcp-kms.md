# Armazene seus secrets do Kubernetes de forma segura usando SOPS e GCP KMS

## Tutorial em vídeo
Os comandos abaixo foram usados no vídeo do meu canal `ABC DevOps`, confira: https://youtu.be/iaJiv4L-vVo



## Antes de você começar
1. Tenha certeza de ter o utilitário de linha de comando `gcloud` instalado e configurado com sua conta GCP

## Instalando o Mozilla SOPS 
1. Baixe o executável (aqui estou usando o AMD64, mas você encontra as [outras releases aqui](https://github.com/mozilla/sops/releases/download/v3.7.3/sops-v3.7.3.linux.amd64)
```bash
wget https://github.com/mozilla/sops/releases/download/v3.7.3/sops-v3.7.3.linux.amd64 -O /tmp/sops
```

2. Dê permissão de execução
```bash
chmod +x /tmp/sops
```

3. Coloque o executável numa pasta `bin` que esteja no path do seu SO
```bash
sudo mv /tmp/sops /usr/local/bin/sops
```

4. Verifique se está funcional
```bash
sops -v
```

Você deverá ter uma saída semelhante à essa
```bash
sops 3.7.3 (latest)
```


## Criando chave no Google KMS
Crie o keyring
```bash
gcloud kms keyrings create sops-keyring \
    --location global
```

Crie uma chave exclusiva para esse propósito
```bash
gcloud kms keys create sops \
    --keyring sops-keyring \
    --location global \
    --purpose "encryption"
```


## Criptografando
1. Se autentique com o `gcloud` para que o SOPS consiga usar suas credenciais
```bash
gcloud auth login
```

2. Criptografe
```bash
sops --encrypt --gcp-kms projects/<ID_PROJETO>/locations/global/keyRings/<NOME_KEYRING>/cryptoKeys/<NOME_CHAVE> secret-example.yaml > secret-example.enc.yaml
```


## Descriptografando
Para descriptografar você não precisa informar a chave, o SOPS consegue pegar o caminho dela.

> Você precisa ter as permissões adequadas para conseguir descriptografar, veja a próxima sessão

```bash
sops --decrypt secret-example.enc.yaml > secret-descriptografado.yaml
```


## Permissões (Roles)
### Criptografar
Para que usuário consiga criptografar usando a chave ele deve ter a seguinte permissõo:  
`cloudkms.cryptoKeyVersions.useToEncrypt`
Essa permissão pode ser encontrada na role `roles/cloudkms.cryptoKeyEncrypter`

### Descriptografar
Para que usuário consiga descriptografar usando a chave ele deve ter a seguinte permissõo:  
`cloudkms.cryptoKeyVersions.useToDecrypt`
Essa permissão pode ser encontrada na role `roles/cloudkms.cryptoKeyEncrypterDecrypter`


## Fontes
https://github.com/mozilla/sops  
https://cloud.google.com/kms/docs/create-key-ring  
https://cloud.google.com/kms/docs/create-key  
https://github.com/mozilla/sops#encrypting-using-gcp-kms  
https://cloud.google.com/kms/docs/encrypt-decrypt#before_you_begin  