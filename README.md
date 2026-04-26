# 🔐 Flask Auth API

API REST de autenticação e gerenciamento de usuários desenvolvida durante a **Formação Python** da [Rocketseat](https://rocketseat.com.br/).

## 📋 Sobre o projeto

A aplicação implementa um sistema de autenticação completo com controle de acesso baseado em roles (`admin` / `user`), utilizando Flask como framework web e MySQL como banco de dados.

## ✨ Funcionalidades

- Cadastro de usuários com senha criptografada
- Login e logout com gerenciamento de sessão
- CRUD completo de usuários
- Controle de acesso por nível de permissão:
  - `user` — pode atualizar apenas o próprio perfil
  - `admin` — pode deletar qualquer usuário (exceto a si mesmo)

## 🚀 Tecnologias

- **[Flask](https://flask.palletsprojects.com/)** — framework web
- **[Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/)** — ORM para o banco de dados
- **[Flask-Login](https://flask-login.readthedocs.io/)** — gerenciamento de sessões autenticadas
- **[bcrypt](https://pypi.org/project/bcrypt/)** — hash seguro de senhas
- **[MySQL](https://www.mysql.com/)** — banco de dados relacional
- **[Docker](https://www.docker.com/)** — containerização do banco de dados

## 🛠️ Como executar

### Pré-requisitos

- Python 3.x
- Docker e Docker Compose

### Passo a passo

1. Clone o repositório:
```bash
git clone https://github.com/leonardoprokopowiskii/flask-auth-api.git
cd flask-auth-api
```

2. Suba o banco de dados com Docker:
```bash
docker-compose up -d
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

4. Inicie a aplicação:
```bash
python app.py
```

A API estará disponível em `http://localhost:5000`.

## 📡 Endpoints

### Autenticação

| Método | Rota      | Descrição              | Auth |
|--------|-----------|------------------------|------|
| POST   | /login    | Realiza login          | ❌   |
| GET    | /logout   | Realiza logout         | ✅   |

### Usuários

| Método | Rota              | Descrição                        | Auth | Role  |
|--------|-------------------|----------------------------------|------|-------|
| POST   | /user             | Cria um novo usuário             | ❌   | —     |
| GET    | /user/`<id>`      | Retorna dados de um usuário      | ✅   | any   |
| PUT    | /user/`<id>`      | Atualiza a senha do usuário      | ✅   | own / admin |
| DELETE | /user/`<id>`      | Deleta um usuário                | ✅   | admin |

### Exemplos de requisição

**Cadastro de usuário**
```json
POST /user
{
  "username": "joao",
  "password": "minhasenha123"
}
```

**Login**
```json
POST /login
{
  "username": "joao",
  "password": "minhasenha123"
}
```