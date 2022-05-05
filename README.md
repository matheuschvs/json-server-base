<h1 align="center">json-server-base</h1>

**baseUrl:** `https://cards-and-episodes.herokuapp.com`

<p align = "center">
Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.</p>

<h2 align="center">Endpoints</h2>

<p align = "center">
Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.</p>

<h3 align="center">Cadastro</h3>

- POST /register
- POST /signup
- POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

<h3 align="center">Login</h3>

- POST /login
- POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

### Rotas que não precisam de autenticação

<h3 align="center">Listando Cards</h3>

Qualquer usuário, registrado ou não, pode ver os cards que já foram cadastrados, e quem os cadastrou.

`GET /cards`
_exemplo de resposta:_
```json
  [
  	{
  		"userId": 1,
  		"name": "cubone",
  		"value": 150,
  		"id": 1
  	}
  ]
```

É ainda possível expandir o usuário que cadastrou o card utilizando o endpoint abaixo:

`GET /cards?_expand=user`
_exemplo de resposta:_
```json
  [
  	{
  		"userId": 1,
  		"name": "cubone",
  		"value": 150,
  		"id": 1,
  		"user": {
  			"email": "kenzinho@mail.com",
  			"password": "$2a$10$YQiiz0ANVwIgpOjYXPxc0O9H2XeX3m8OoY1xk7OGgxTnOJnsZU7FO",
  			"name": "Kenzinho",
  			"age": 38,
  			"id": 1
  		}
  	}
  ]
```

### Rotas que precisam de autenticação
**É necessário um token de autorização**

<h3 align="center">Criando Cards</h3>

Qualquer usuário registrado pode cadastrar novos cards.

`POST /cards`
_exemplo de corpo da requisição:_
```json
  {
  	"userId": 1,
  	"name": "cubone",
  	"value": 150
  }
```

<h3 align="center">Listando Episódios</h3>

Qualquer usuário logado pode ver a lista de episódios.

`GET /episodes`
_exemplo de resposta:_
```json
  [
  	{
  		"title": "Quando Regiões se Enfrentam!",
  		"season": "2001",
  		"number": 43
  	}
  ]
```