# Projeto de Ambiente Web com Docker Compose

## Descrição

Este projeto configura um ambiente web utilizando Docker Compose, incluindo os seguintes serviços:
- **WordPress**: Plataforma de criação e gestão de conteúdo.
- **Redis**: Banco de dados em memória utilizado para cache.
- **Prometheus**: Sistema de monitoramento e alertas.

## Pré-requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Instruções de Instalação

1. Clone o repositório:
    ```bash
    git clone https://github.com/Igorggwp/WordpressDocker.git
    cd WordpressDocker
    ```

2. Configure o Docker Daemon:
    - Encontre e edite o arquivo `daemon.json`:
        - **Linux**: O arquivo está localizado em `/etc/docker/daemon.json`
        - **Windows**: O arquivo está localizado em `C:\ProgramData\Docker\config\daemon.json`
        - **macOS**: O arquivo está localizado em `~/Library/Group Containers/group.com.docker/daemon.json`
    - Se o arquivo não existir, crie-o e adicione a seguinte configuração:
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

1. Acesse o painel de administração do WordPress em `http://localhost:8000/wp-admin`.
2. Faça login com as credenciais configuradas durante a instalação.
3. No menu lateral, vá para **Plugins** > **Adicionar novo**.
4. Pesquise pelo plugin que deseja instalar.
5. Clique em **Instalar agora** e, em seguida, em **Ativar**.

### Monitorando com Prometheus

- Abra o navegador e vá para `http://localhost:9090`.

## Configuração dos Serviços

### WordPress

O WordPress é configurado com as seguintes variáveis de ambiente:

- `WORDPRESS_DB_HOST`: Nome do host do banco de dados.
- `WORDPRESS_DB_USER`: Usuário do banco de dados.
- `WORDPRESS_DB_PASSWORD`: Senha do banco de dados.
- `WORDPRESS_DB_NAME`: Nome do banco de dados.

### Redis

O Redis é utilizado como serviço de cache e está acessível na porta `6379`.

### Prometheus

O Prometheus está configurado para monitorar os serviços e está acessível na porta `9090`.

