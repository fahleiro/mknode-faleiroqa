# [CRIANDO DATABASE SQL SERVER COM DOCKER E LINUX - SOMENTE CLI](https://youtu.be/IL-lfihmfw4?si=Gt5DORx6nySGZyma)

<iframe width="560" height="315" src="https://www.youtube.com/embed/IL-lfihmfw4" 
title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Objetivos
- Iniciar uma base de dados utilizando a imagem docker oficial do SQL SERVER MICROSOFT;
- Conectar-se à base de dados utilizando um SGBD a partir de outra máquina na rede;

## Comandos apresentados durante o vídeo
- `sudo` - comando para executar comandos com permissão de super usuário: _"super user do"_
- `docker image ls` - listar as imagens docker disponíveis localmente
- `docker ps` - listar os containers em execução
- `docker logs container-name` - listar os logs do container
- `docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=Password=102030" -p 1433:1433 --name sqlserver-container -d mcr.microsoft.com/mssql/server:2022-latest`
    - `docker run` - executa um novo container
    - `-e` - seta variáveis
    - `"ACCEPT_EULA=Y"` - aceita o contrato de licença
    - `"SA_PASSWORD=Password=102030"` - seta senha do usuário sysadmin (sa)
    - `-p` - mapeia a porta do host para porta do container
    - `--name` - seta nome do container
    - `-d` - inicia o container em modo 2 plano ( detached mode)
    - `mcr.microsoft.com/mssql/server:2022-latest` - nome da imagem docker no formato _"nome:versao"_
