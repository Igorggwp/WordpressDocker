# Projeto de Ambiente Web com Docker Compose

## Descrição

Este projeto configura um ambiente web utilizando Docker Compose, utilizando:
- **WordPress**: Plataforma de criação de conteudo.
- **Redis**: Banco de dados em memória utilizado para cache.
- **Prometheus**: Sistema de monitoramento.

## Pré-requisitos

Docker e Docker compose

## Instruções de Instalação

1. Clone o repositório:
    ```bash
    git clone https://github.com/Igorggwp/WordpressDocker.git
    cd WordpressDocker
    ```

2. Configure o Docker Daemon:
    - Encontre e edite o arquivo `daemon.json`:
        - O arquivo está localizado em `/etc/docker/daemon.json`, ou, .docker no diretório do seu usuário.
      ```json
      {
        "builder": {
          "gc": {
            "defaultKeepStorage": "20GB",
            "enabled": true
          }
        },
        "metrics-addr": "0.0.0.0:9323",
        "experimental": true
      }
      ```

3. Reinicie o serviço Docker para aplicar as novas configurações:
    ```bash
    sudo systemctl restart docker
    ```

4. Inicialize os containers:
    ```bash
    docker-compose up -d
    ```

## Uso

### Acessando o WordPress

- Abra o navegador e vá para `http://localhost:8000`.

### Instalando Plugins no WordPress

1. Acesse o painel de administração do WordPress.
2. Faça login com as credenciais configuradas durante a instalação.
3. No menu lateral, vá para **Plugins** > **Adicionar novo**.
4. Pesquise pelo plugin **Redis Object Cache**.
5. Clique em **Instalar agora** e, em seguida, em **Ativar**.

### Monitorando com Prometheus

- Abra o navegador e vá para `http://localhost:9090`.

Com esses serviços integrados o sistema esta pronto para utilizar!
