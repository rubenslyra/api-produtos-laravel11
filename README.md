# 🛍️ API de Produtos

[![PHP](https://img.shields.io/badge/PHP-8.2%2B-blue.svg)](https://php.net)
[![Laravel](https://img.shields.io/badge/Laravel-11.0-red.svg)](https://laravel.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Tests](https://img.shields.io/badge/tests-passing-brightgreen.svg)](tests)
[![Coverage Status](https://coveralls.io/repos/github/your-username/your-repo/badge.svg?branch=main)](https://coveralls.io/github/your-username/your-repo?branch=main)

API RESTful de gerenciamento de produtos desenvolvida com Laravel 11, implementando Factory Pattern, Repository Pattern e boas práticas de desenvolvimento.

## 🚀 Stack

- PHP 8.3+
- Laravel 11
- MySQL 8.30
- Redis (cache e queues)
- Docker

## 📋 Requisitos

- Docker e Docker Compose
- Git
- Composer (opcional - pode usar via Docker)

## 🔧 Instalação

1. Clone o repo e entre na pasta:
```bash
git clone https://github.com/seu-usuario/api-produtos.git
cd api-produtos
```

2. Configure o ambiente:
```bash
cp .env.example .env
```

3. Suba os containers:
```bash
docker-compose up -d
```

4. Instale as dependências:
```bash
# Via Docker
docker-compose exec app composer install

# Local
composer install
```

5. Gere a key da aplicação:
```bash
docker-compose exec app php artisan key:generate
```

6. Rode as migrations e seeders:
```bash
docker-compose exec app php artisan migrate --seed
```

## 🏃‍♂️ Rodando

Se tudo deu certo, a API estará disponível em:
```
http://localhost:8000/api/v1
```

Para acessar o container principal:
```bash
docker-compose exec app bash
```

## 📚 Documentação da API

### Endpoints Disponíveis

#### Produtos
```
GET /api/v1/products
GET /api/v1/products/{id}
POST /api/v1/products
PUT /api/v1/products/{id}
DELETE /api/v1/products/{id}
GET /api/v1/products/search
```

### Exemplos de Uso

#### Listar Produtos (com filtros)
```bash
curl -X GET 'http://localhost:8000/api/v1/products?category=Electronics&on_sale=true'
```

#### Criar Produto
```bash
curl -X POST http://localhost:8000/api/v1/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Smartphone XYZ",
    "description": "Um smartphone incrível",
    "price": 1999.99,
    "stock": 50,
    "sku": "PHONE123",
    "category": "Electronics",
    "attributes": {
      "color": "black",
      "storage": "128GB"
    }
  }'
```

## 🧪 Testes

Rodando os testes:
```bash
# Via Docker
docker-compose exec app php artisan test

# Local
php artisan test
```

Com coverage:
```bash
docker-compose exec app php artisan test --coverage
```

## 🔄 CI/CD

O projeto usa GitHub Actions para:
- Rodar testes
- Análise estática (PHPStan)
- Code style (PHP-CS-Fixer)
- Deploy automático

## 📦 Estrutura de Pastas

```
├── app
│   ├── Http
│   │   ├── Controllers
│   │   ├── Requests
│   │   └── Resources
│   ├── Models
│   ├── Repositories
│   └── Services
├── database
│   ├── factories
│   ├── migrations
│   └── seeders
├── docker
│   └── ...
├── tests
│   ├── Feature
│   └── Unit
└── ...
```

## 🔨 Comandos Úteis

```bash
# Limpar caches
php artisan optimize:clear

# Rodar as migrations fresh
php artisan migrate:fresh --seed

# Gerar nova factory
php artisan make:factory NomeFactory

# Logs em tempo real
docker-compose exec app tail -f storage/logs/laravel.log
```

## 💡 Boas Práticas

1. **GIT**
   - Commits semânticos
   - Feature branches
   - PR template

2. **Código**
   - PSR-12
   - SOLID
   - DRY

3. **API**
   - RESTful
   - Versionamento
   - Resource/Request pattern

## 🐛 Debug

### Logs
```bash
# Tempo real
tail -f storage/logs/laravel.log

# Último erro
tail -n 50 storage/logs/laravel.log
```

### Tinker
```bash
php artisan tinker
```

### Telescope
Disponível em `/telescope` em ambiente de desenvolvimento.

## 🚨 Troubleshooting

1. **Permission denied**
```bash
chmod -R 777 storage bootstrap/cache
```

2. **Container não sobe**
```bash
docker-compose down -v
docker-compose up -d --build
```

3. **Composer memory limit**
```bash
COMPOSER_MEMORY_LIMIT=-1 composer install
```

## 📝 TODO

- [ ] Implementar cache com Redis
- [ ] Adicionar autenticação JWT
- [ ] Melhorar cobertura de testes
- [ ] Documentação com Swagger
- [ ] Rate limiting
- [ ] Monitoramento com Sentry

## 👥 Contribuindo

1. Fork o projeto
2. Crie sua feature branch (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Add: MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## ✍️ Autor

Seu Nome - [@seutwitter](https://twitter.com/seutwitter)

## 🙏 Agradecimentos

- [Laravel](https://laravel.com)
- [PHP-FIG](https://www.php-fig.org)
- [Shields.io](https://shields.io)
