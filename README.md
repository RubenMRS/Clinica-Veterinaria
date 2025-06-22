
# Clínica Veterinária - API RESTful

<p align="center">
  <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="200" alt="Laravel Logo">
</p>

## Descrição

Este projeto é uma API RESTful desenvolvida com Laravel para gerir os utilizadores, animais, conteúdos e consultas de uma clínica veterinária. A API utiliza autenticação JWT para proteger as rotas e garantir diferentes níveis de acesso (administrador e utilizador comum).

## Funcionalidades

- Registo, login e logout de utilizadores com JWT.
- Gestão de utilizadores (CRUD) — apenas para administradores.
- Gestão de animais, conteúdos e consultas (CRUD) — para utilizadores autenticados.
- Proteção de rotas via middleware `auth:sanctum`.
- Validação robusta de dados e tratamento claro de erros.
- Estrutura organizada para facilitar manutenção e expansão.

## Tecnologias

- Laravel 12.x
- PHP 8.2+
- MySQL
- Sanctum para autenticação JWT
- Composer para gestão de dependências

## Requisitos

- PHP 8.2 ou superior
- Servidor MySQL
- Composer instalado
- Extensões PHP necessárias: PDO, OpenSSL, Mbstring, Tokenizer, XML, Ctype, JSON

## Instalação e Configuração

1. Clona o repositório:

```bash
git clone https://github.com/RubenMRS/Clinica-Veterinaria
cd clinica-veterinaria
```

2. Instala as dependências:

```bash
composer install
```

3. Copia o ficheiro de ambiente e configura:

```bash
cp .env.example .env
```

Edita o `.env` para ajustar a ligação à base de dados ~

DB_CONNECTION=mysql.
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=ClinicaVet
DB_USERNAME=root
DB_PASSWORD=

4. Gera a chave da aplicação:

```bash
php artisan key:generate
```

5. Executa as migrações para criar as tabelas:

```bash
php artisan migrate
```

6. (Opcional) Adiciona dados de teste com seeders, se existirem:

```bash
php artisan db:seed
```

7. Inicia o servidor local Laravel:

```bash
php artisan serve
```

A API estará disponível em: `http://localhost:8000`

---

## Uso da API

### Autenticação

- **POST** `/api/register` — regista novo utilizador

  ```json
  {
    "name": "João Silva",
    "email": "joao@example.com",
    "password": "senha123",
    "password_confirmation": "senha123"
  }
  ```

- **POST** `/api/login` — efetua login e retorna token JWT

  ```json
  {
    "email": "joao@example.com",
    "password": "senha123"
  }
  ```

  Resposta de sucesso:

  ```json
  {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
  }
  ```

### Autorização

Para chamadas às rotas protegidas, adiciona o header:

```
Authorization: Bearer {token}
```

### Endpoints Principais

#### Utilizadores (Admin)

- `GET /api/users` — listar utilizadores
- `POST /api/users` — criar utilizador
- `PUT /api/users/{id}` — atualizar utilizador
- `DELETE /api/users/{id}` — apagar utilizador

#### Animais (Autenticado)

- `GET /api/animais` — listar animais
- `POST /api/animais` — criar animal
- `GET /api/animais/{id}` — ver detalhes
- `PUT /api/animais/{id}` — atualizar
- `DELETE /api/animais/{id}` — apagar

#### Conteúdos (Autenticado)

- `GET /api/contents` — listar conteúdos
- `POST /api/contents` — criar conteúdo
- `GET /api/contents/{id}` — ver detalhes
- `PUT /api/contents/{id}` — atualizar
- `DELETE /api/contents/{id}` — apagar

---

## Validação e Tratamento de Erros

- Validação dos dados é realizada no backend usando Requests e regras personalizadas.
- Mensagens claras e padrões de resposta JSON são utilizados para facilitar o consumo da API.
- Código HTTP apropriado é retornado (ex: 422 para erros de validação, 401 para não autorizado).

---

## Testar com Postman

1. Regista um utilizador via `/api/register`.
2. Faz login via `/api/login` para obter o token JWT.
3. Usa o token para fazer chamadas autenticadas às rotas protegidas, adicionando o header:

```
Authorization: Bearer {token}
```

4. Testa CRUD de utilizadores, animais e conteúdos conforme necessidade.

---

## Contribuir

Sinta-se livre para contribuir com melhorias! Por favor, faça fork do projeto e envie pull requests.

---

## Licença

Este projeto está licenciado sob a licença MIT. Veja o ficheiro LICENSE para detalhes.

---

## Contacto

Para dúvidas ou sugestões, contacte: a046582@ipmaia.pt

