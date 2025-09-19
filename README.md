# Central Controle - Infraestrutura

Este repositório contém a infraestrutura Docker para a aplicação **Central Controle**, composta por:

* **usuario-service**: Backend em Java/Gradle
* **web**: Frontend em React/Vite
* **nginx**: Proxy reverso para o frontend e backend

---

## Pré-requisitos

* Docker
* Docker Compose

---

## Variáveis de ambiente

Crie um arquivo `.env` com as seguintes variáveis:

```env
# Caminhos dos serviços
URL_USUARIO_SERVICE=
URL_WEB=
URL_NGINX_CONF=

# Credenciais do admin
ADMIN_USERNAME=
ADMIN_PASSWORD=

# Configurações JWT
JWT_SECRET=

# Banco de dados do usuário
USUARIO_DB_URL=
USUARIO_DB_USERNAME=
USUARIO_DB_PASSWORD=
USUARIO_SCHEMA=
```

> Os caminhos (`URL_*`) devem apontar para os diretórios dos projetos e para o arquivo `nginx.conf`.

---

## Executando a infraestrutura

No terminal, dentro do diretório do repositório:

```bash
docker-compose up --build
```

Isso irá:

* Construir as imagens do `usuario-service` e do `web`
* Iniciar os containers `usuario-service`, `web` e `nginx`
* Expor o frontend na porta `8081`

---

## Configuração do Nginx

O arquivo `nginx/nginx.conf` já vem configurado como proxy reverso:

* `/` → Frontend (React/Vite)
* `/api/usuario/` → Backend (`usuario-service`)

---
