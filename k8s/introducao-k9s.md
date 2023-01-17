# Introdução ao K9s

## Instalação

### Baixe o executável compactado
Faça o download do executável compactado no formato `.tar.gz` para a pasta temporária
```bash
wget https://github.com/derailed/k9s/releases/download/v0.26.7/k9s_Linux_x86_64.tar.gz -O /tmp/k9s.tar.gz
```

### Extraia
Vamos extrair o executável de dentro do pacote `.tar.gz` para a pasta /tmp para não fazer bagunça na nossa `Home`
```bash
tar -zxvf /tmp/k9s.tar.gz --directory /tmp/
```

### Permissão de executar
Dê a permissão `execute` para o executável do K9s, senão ele vai ser só um amontado inútil de bytes rsrsrs
```bash
chmod +x /tmp/k9s
```

### Mova o executável
Pra que você consiga invocar o comando `k9s` de qualquer lugar/diretório, você precisa mover ele pra uma pasta que esteja no `PATH` da sua máquina.  
Nesse caso, movi para `/usr/local/bin/`

> Não se esqueça do sudo na hora de mover !!!

```bash
sudo mv /tmp/k9s /usr/local/bin/k9s
```