# Checkpoint 6 Microservice and Web Engineering

## I. Informações do Grupo

| Nome Completo | (RM) |
| :--- | :--- |
| Lucas de Alencar Pereira | 551720 |
| Miguel Stein Martins | 550901 |

## II. Visão Geral da Aplicação

O projeto implementa uma API para o recurso principal `Task`, que suporta as operações fundamentais de persistência de dados.

### 2.1. Endpoints Principais

A aplicação é exposta na porta `8080` e a rota base é `/api/tasks`.

| Método | Endpoint | Descrição da Funcionalidade |
| :--- | :--- | :--- |
| **POST** | `/api/tasks` | Cria um novo registro de tarefa. |
| **GET** | `/api/tasks` | Retorna a lista completa de todas as tarefas cadastradas. |
| **GET** | `/api/tasks/{id}` | Busca e retorna uma tarefa específica pelo seu ID. |
| **PUT** | `/api/tasks/{id}` | Atualiza o conteúdo e/ou o status de uma tarefa existente. |
| **DELETE** | `/api/tasks/{id}` | Remove permanentemente uma tarefa do banco de dados. |

### 2.2. Acesso à Documentação

A documentação interativa da API (Swagger UI) está acessível no navegador após a inicialização da aplicação:

`http://localhost:8080/swagger-ui.html`

## III. Instruções de Execução

### 3.1. Pré-requisitos

* Docker Desktop (instalado e em execução).
* Git.

### 3.2. Execução via Docker Compose (Ambiente de Desenvolvimento)

Este é o método recomendado para iniciar a aplicação juntamente com o serviço de banco de dados PostgreSQL.

1.  Clone o repositório e navegue até a raiz do projeto:
    ```bash
    git clone [https://github.com/alencasz/checkpoint3mc.git](https://github.com/alencasz/checkpoint3mc.git)
    cd checkpoint3mc
    ```
2.  Inicie o ambiente, que irá construir a imagem da API e subir o contêiner do PostgreSQL:
    ```bash
    docker-compose up --build
    ```
    *Aguarde a mensagem de log `Started Checkpoint3mcApplication in...` para confirmar que a API está operacional.*

### 3.3. Execução via Imagem Publicada (Docker Run)

Para executar apenas o contêiner da API, assumindo que um banco de dados PostgreSQL já esteja rodando separadamente:

```bash
docker run -p 8080:8080 \
  -e SPRING_DATASOURCE_URL=jdbc:postgresql://<ip_do_seu_banco>:5432/taskdb \
  -e SPRING_DATASOURCE_USERNAME=postgres \
  -e SPRING_DATASOURCE_PASSWORD=admin \
  alencaralho/checkpoint3mc:latest
