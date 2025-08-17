# NLW Agents - Backend 🚀

[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8+-blue.svg)](https://www.typescriptlang.org/)
[![Fastify](https://img.shields.io/badge/Fastify-5.4+-blue.svg)](https://fastify.dev/)
[![Docker](https://img.shields.io/badge/Docker-Compose-blue.svg)](https://www.docker.com/)

Uma aplicação backend poderosa desenvolvida durante a **20ª Edição do NLW (Next Level Week)** da Rocketseat, focada em **Agentes de IA**. Este projeto integra inteligência artificial com funcionalidades avançadas de transcrição de áudio, geração de embeddings e busca semântica.

## 📋 Descrição

O NLW Agents Backend é uma API REST robusta que oferece funcionalidades de:

- **Transcrição inteligente de áudio** usando Google Gemini AI
- **Geração de embeddings semânticos** para busca avançada
- **Sistema de salas para organização de conteúdo**
- **Q&A inteligente** baseado em contexto de transcrições
- **Armazenamento vetorial** com PostgreSQL + pgvector

## 🛠 Tecnologias Utilizadas

| Tecnologia                 | Versão | Uso                                |
| -------------------------- | ------- | ---------------------------------- |
| **Node.js**          | 18+     | Runtime JavaScript                 |
| **TypeScript**       | 5.8+    | Linguagem de programação         |
| **Fastify**          | 5.4.0   | Framework web performático        |
| **Drizzle ORM**      | 0.44.2  | ORM para banco de dados            |
| **PostgreSQL**       | 17      | Banco de dados principal           |
| **pgvector**         | -       | Extensão para busca vetorial      |
| **Google Gemini AI** | 1.14.0  | IA para transcrição e embeddings |
| **Zod**              | 4.0.5   | Validação de schemas             |
| **Docker**           | -       | Containerização                  |
| **Biome**            | 2.0.6   | Linter e formatter                 |

## 📁 Estrutura do Projeto

```
nwlagents-backend/
├── 📄 docker-compose.yml          # Configuração do PostgreSQL
├── 📄 drizzle.config.ts           # Configuração do Drizzle ORM
├── 📄 package.json                # Dependências e scripts
├── 📄 tsconfig.json               # Configuração TypeScript
├── 📄 biome.jsonc                 # Configuração do Biome
├── 🐳 docker/
│   └── setup.sql                  # Script inicial do banco
├── 🎯 src/
│   ├── 📄 server.ts               # Servidor principal
│   ├── 📄 env.ts                  # Configuração de ambiente
│   ├── 🗄️ db/
│   │   ├── connection.ts          # Conexão com banco
│   │   ├── seed.ts                # Dados iniciais
│   │   ├── migrations/            # Migrações do banco
│   │   └── schema/                # Schemas das tabelas
│   ├── 🌐 http/
│   │   └── routes/                # Rotas da API
│   └── 🤖 services/
│       └── gemini.ts              # Integração com Gemini AI
```

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- **Node.js** (versão 18 ou superior)
- **Docker** e **Docker Compose**
- **Git**
- Uma **chave de API do Google Gemini** ([obter aqui](https://makersuite.google.com/app/apikey))

## 🚀 Configuração e Setup

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd nwlagents-backend
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
# Porta do servidor
PORT=3333

# Banco de dados
DATABASE_URL="postgresql://docker:docker@localhost:5432/agents"

# Google Gemini AI
GEMINI_API_KEY=sua_chave_api_aqui
```

### 4. Inicie o banco de dados

```bash
docker-compose up -d
```

### 5. Execute as migrações

```bash
npm run db:migrate
```

### 6. (Opcional) Popule o banco com dados iniciais

```bash
npm run db:seed
```

### 7. Inicie o servidor

```bash
# Modo desenvolvimento
npm run dev

# Modo produção
npm start
```

O servidor estará rodando em `http://localhost:3333`

## 📡 Principais Endpoints

### 🏠 Health Check

```http
GET /health
```

Verifica se a API está funcionando.

### 🏢 Salas (Rooms)

```http
# Listar todas as salas
GET /rooms

# Criar nova sala
POST /rooms
Content-Type: application/json
{
  "name": "Aula de React",
  "description": "Conceitos fundamentais do React" // opcional
}

# Obter perguntas de uma sala
GET /rooms/{roomId}/questions
```

### 🎵 Upload de Áudio

```http
# Fazer upload e transcrição de áudio
POST /rooms/{roomId}/audio
Content-Type: multipart/form-data
[arquivo de áudio]
```

### ❓ Perguntas

```http
# Criar pergunta inteligente baseada no contexto
POST /rooms/{roomId}/questions
Content-Type: application/json
{
  "question": "O que são React Hooks?"
}
```

## 🧪 Scripts Disponíveis

| Script                  | Descrição                               |
| ----------------------- | ----------------------------------------- |
| `npm run dev`         | Inicia o servidor em modo desenvolvimento |
| `npm start`           | Inicia o servidor em modo produção      |
| `npm run db:generate` | Gera migrações do banco                 |
| `npm run db:migrate`  | Executa migrações pendentes             |
| `npm run db:seed`     | Popula banco com dados iniciais           |

## 🔄 Fluxo da Aplicação

1. **Criação de Sala**: Usuario cria uma sala temática
2. **Upload de Áudio**: Upload de arquivo de áudio (aula, palestra, etc.)
3. **Transcrição IA**: Gemini AI transcreve o áudio para texto
4. **Geração de Embeddings**: Criação de vetores semânticos
5. **Armazenamento**: Dados salvos no PostgreSQL com pgvector
6. **Consultas Inteligentes**: Perguntas são respondidas com base no contexto

## 🗃️ Banco de Dados

O projeto utiliza PostgreSQL com a extensão **pgvector** para busca semântica:

### Principais Tabelas:

- **rooms**: Salas organizacionais
- **audio_chunks**: Transcrições e embeddings dos áudios
- **questions**: Perguntas e respostas geradas pela IA

## 🤖 Integração com IA

### Google Gemini AI

- **Transcrição de Áudio**: Modelo `gemini-2.5-flash`
- **Embeddings**: Modelo `text-embedding-004`
- **Geração de Respostas**: Baseada em contexto das transcrições

## 🔧 Desenvolvimento

### Gerando novas migrações:

```bash
npm run db:generate
```

### Aplicando migrações:

```bash
npm run db:migrate
```

### Executando seed:

```bash
npm run db:seed
```

## 📄 Licença

Este projeto foi desenvolvido durante a **20ª Edição do NLW** da [Rocketseat](https://rocketseat.com.br) e é livre para uso educacional e pessoal.

**Desenvolvido com ❤️ durante o NLW Agents da Rocketseat**

