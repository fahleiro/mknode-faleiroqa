# [CRIANDO DATABASE POSTGRES UTILIZANDO INIT.SQL COM DOCKERFILE E LINUX - TABELAS + FUNCTIONS + TRIGGERS]()

## Objetivos
- Criar uma imagem docker personalizada a partir da imagem oficial do POSTGRES;
- Iniciar o database com configurações pré-definidas pelo init.sql e arquivos de setup;
- Conectar-se à base de dados utilizando o SGBD POSTGRES a partir de outra máquina na rede;

## Comandos apresentados durante o vídeo
- `sudo` - comando para executar comandos com permissão de super usuário: _"super user do"_
- `nano nome-arquivo` - comando para criação de arquivos de texto no linux (pacote pode ser adicionado via comando `sudo apt-get install nano`)
- `docker image ls` - listar as imagens docker disponíveis localmente
- `docker ps` - listar os containers em execução
- `docker logs container-name` - listar os logs do container
- `sudo chmod +x reimage.sh` - torna o script executável



## Scripts utilizados
- **Dockerfile**
    ```
    # Usar a imagem oficial do PostgreSQL
    FROM postgres:latest

    # Definir variáveis de ambiente para o banco de dados
    ENV POSTGRES_USER=user
    ENV POSTGRES_PASSWORD=102030
    ENV POSTGRES_DB=db_name

    # Copiar os scripts SQL para o diretório de inicialização do PostgreSQL
    COPY setup/ /docker-entrypoint-initdb.d/

    # Expor a porta padrão do PostgreSQL
    EXPOSE 5432
    ```

- **Script de reinicialização do container e imagem**
    ```
    #!/bin/bash

    # Para facilitar o debugging
    set -e

    # Passo 1: Parar e remover o container e a imagem
    sudo docker stop postgres-db-container || echo "Container não está em execução."
    sudo docker rm postgres-db-container || echo "Container já foi removido."
    sudo docker image rm postgres-db || echo "Imagem já foi removida."

    echo "Container e imagem removidos."

    # Passo 2: Construir a imagem
    sudo docker build -t postgres-db .
    echo "Imagem postgres-db criada."

    # Passo 3: Rodar o container
    sudo docker run -d --name postgres-db-container -p 5432:5432 postgres-db
    echo "Container postgres-db-container iniciado."

    # Passo 4: Verificar o status do container e aguardar a inicialização
    echo "Aguardando inicialização do container..."
    while ! sudo docker exec postgres-db-container pg_isready -q >/dev/null 2>&1; do
    echo "Esperando serviço PostgreSQL..."
    sleep 2
    done

    echo "Container postgres-db-container está pronto."
    ```
- **init.sql**
    ```
    -- Executa os scripts de criação de tabelas na ordem desejada
    \i /docker-entrypoint-initdb.d/tables/t_user.sql

    -- Executa os scripts de triggers
    \i /docker-entrypoint-initdb.d/trg/trg_function_after_insert_t_user.sql

    -- Executa o script de funções
    \i /docker-entrypoint-initdb.d/func/func_update_t_use.sql
    ```
- **t_user.sql**
    ```
    -- Criar tabela t_user
    CREATE TABLE IF NOT EXISTS t_user (
        user_id SERIAL PRIMARY KEY, 
        user_number VARCHAR(9) NOT NULL UNIQUE,
        user_name VARCHAR(30) NOT NULL
    );
    ```