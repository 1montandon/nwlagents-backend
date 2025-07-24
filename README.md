# NWL Agents

Projeto desenvolvido durante o evento da Rocketseat, implementando uma API REST para gerenciamento de salas com suporte a vetores para funcionalidades de IA.

## 🚀 Tecnologias

- **Node.js** - Runtime JavaScript
- **TypeScript** - Tipagem estática
- **Fastify** - Framework web de alta performance
- **Drizzle ORM** - Object-Relational Mapping
- **PostgreSQL + pgvector** - Banco de dados com extensão para vetores
- **Zod** - Validação de schemas
- **Docker** - Containerização

## 📁 Estrutura do Projeto

```
src/
├── db/
│   ├── schema/         # Schemas do banco de dados
│   ├── migrations/     # Migrações do banco
│   ├── connection.ts   # Configuração da conexão
│   └── seed.ts        # Dados iniciais
├── http/
│   └── routes/        # Rotas da API
├── env.ts             # Configuração de variáveis de ambiente
└── server.ts          # Servidor principal
```

## 🛠️ Setup e Configuração

### Pré-requisitos

- Node.js (versão mais recente)
- Docker e Docker Compose

### Instalação

1. Clone o repositório
2. Instale as dependências:

   ```bash
   npm install
   ```

3. Configure as variáveis de ambiente:

   ```bash
   cp .env.example .env
   ```

4. Inicie o banco de dados:

   ```bash
   docker-compose up -d
   ```

5. Execute as migrações:

   ```bash
   npx drizzle-kit migrate
   ```

6. (Opcional) Execute o seed para dados iniciais:
   ```bash
   npm run db:seed
   ```

### Execução

- **Desenvolvimento:**

  ```bash
  npm run dev
  ```

- **Produção:**
  ```bash
  npm start
  ```

O servidor estará disponível em `http://localhost:3333`

## 🗄️ Banco de Dados

O projeto utiliza PostgreSQL com a extensão **pgvector** para suporte a vetores, permitindo funcionalidades avançadas de IA e busca semântica.

## 🔧 Ferramentas de Desenvolvimento

- **Biome** - Linter e formatador de código
- **Drizzle Kit** - Ferramentas de migração e introspection
- **TypeScript** - Compilação e tipagem

## 📝 API Endpoints

- `GET /health` - Health check
- `GET /rooms` - Lista todas as salas

---

_Desenvolvido durante o evento NLW da Rocketseat_ 🚀
