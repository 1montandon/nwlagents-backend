# NLW Agents Backend 🚀

_Developed during Next Level Week Agents by Rocketseat_

## Description

NLW Agents Backend is a powerful TypeScript-based REST API that enables real-time audio transcription and intelligent question generation using Google Gemini AI. The application processes audio uploads, transcribes them to Portuguese (Brazil), generates vector embeddings for similarity search, and creates intelligent questions based on room content.

This project demonstrates modern backend development practices with type-safe APIs, database management with vector search capabilities, and AI integration for content processing and question generation.

## Features

- **🎙️ Audio Processing**: Upload and transcribe audio files using Google Gemini AI
- **🤖 AI-Powered Questions**: Generate intelligent questions based on room content
- **🏠 Room Management**: Create and manage rooms with descriptions
- **📊 Vector Search**: Store and query audio transcriptions using pgvector embeddings
- **⚡ Real-time API**: Fast and efficient REST API built with Fastify
- **🔒 Type Safety**: Full TypeScript support with Zod validation
- **🐘 PostgreSQL**: Robust database with vector extension support
- **📝 Audio Transcription**: Convert audio to text in Portuguese (Brazil)

## Technologies Used

### Backend Framework & Runtime

- **Node.js** - JavaScript runtime with experimental TypeScript support
- **Fastify** - High-performance web framework
- **TypeScript** - Type-safe JavaScript development

### Database & ORM

- **PostgreSQL** with **pgvector** extension - Vector database for embeddings
- **Drizzle ORM** - Type-safe database toolkit
- **Drizzle Kit** - Database migrations and schema management

### AI & Processing

- **Google Gemini AI** - Audio transcription and text generation
- **Vector Embeddings** - Semantic search capabilities

### Validation & Type Safety

- **Zod** - Schema validation
- **fastify-type-provider-zod** - Type-safe API routes

### Development Tools

- **Biome** - Fast linter and formatter
- **Docker Compose** - Development environment setup
- **Ultracite** - Development utilities

## Installation

### Prerequisites

- **Node.js** (v18 or higher)
- **Docker** and **Docker Compose**
- **Google Gemini API Key**

### Step-by-step Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/1montandon/nwlagents-backend.git
   cd nwlagents-backend
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env` file in the root directory:

   ```env
   PORT=3333
   DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

4. **Start the PostgreSQL database**

   ```bash
   docker-compose up -d
   ```

5. **Run database migrations**

   ```bash
   npm run db:migrate
   ```

6. **Seed the database (optional)**

   ```bash
   npm run db:seed
   ```

7. **Start the development server**
   ```bash
   npm run dev
   ```

The API will be available at `http://localhost:3333`

## Usage

### API Endpoints

#### Health Check

```http
GET /health
```

Returns server status.

#### Room Management

**Create a Room**

```http
POST /rooms
Content-Type: application/json

{
  "name": "Meeting Room 1",
  "description": "Weekly team meeting discussions"
}
```

**Get All Rooms**

```http
GET /rooms
```

**Get Room Questions**

```http
GET /rooms/{roomId}/questions
```

#### Audio Processing

**Upload Audio**

```http
POST /rooms/{roomId}/audio
Content-Type: multipart/form-data

[Audio file in the request body]
```

#### Question Generation

**Create Question**

```http
POST /rooms/{roomId}/questions
Content-Type: application/json

{
  "content": "What were the main topics discussed in the meeting?"
}
```

### Example Usage Flow

1. **Create a room** for organizing content
2. **Upload audio files** to the room for transcription
3. **Generate questions** based on the transcribed content
4. **Query room questions** to retrieve AI-generated responses

### Development Commands

```bash
# Start development server with hot reload
npm run dev

# Start production server
npm start

# Generate database schema
npm run db:generate

# Run database migrations
npm run db:migrate

# Seed database with sample data
npm run db:seed
```

## Configuration

### Environment Variables

| Variable         | Description                           | Required | Default |
| ---------------- | ------------------------------------- | -------- | ------- |
| `PORT`           | Server port number                    | No       | `3333`  |
| `DATABASE_URL`   | PostgreSQL connection string          | Yes      | -       |
| `GEMINI_API_KEY` | Google Gemini API key for AI features | Yes      | -       |

### Database Configuration

The application uses PostgreSQL with the pgvector extension for vector similarity search. The database schema includes:

- **Rooms**: Store room information and descriptions
- **Audio Chunks**: Store transcribed audio with vector embeddings
- **Questions**: Store generated questions and AI responses

### CORS Configuration

CORS is configured to allow requests from `http://localhost:5173` (typical Vite development server). Modify the CORS settings in `src/server.ts` for production use.

## Contributing

We welcome contributions to improve the NLW Agents Backend! Here's how you can help:

### Reporting Bugs

1. Check existing issues to avoid duplicates
2. Create a detailed issue with:
   - Clear description of the bug
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment details (Node.js version, OS, etc.)

### Suggesting Features

1. Open an issue with the "feature request" label
2. Describe the feature and its benefits
3. Provide use cases and examples

### Pull Requests

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes** with clear, descriptive commits
4. **Add tests** for new functionality
5. **Run linting**: `npx biome check .`
6. **Test your changes** thoroughly
7. **Submit a pull request** with:
   - Clear description of changes
   - Link to related issues
   - Screenshots (if applicable)

### Development Guidelines

- Follow existing code style and conventions
- Write descriptive commit messages
- Add appropriate TypeScript types
- Include proper error handling
- Update documentation as needed

## License

This project is licensed under the **ISC License**.

## Contact/Support

### Getting Help

- **GitHub Issues**: For bug reports and feature requests
- **Documentation**: Check this README and code comments
- **Community**: Connect with other Rocketseat students

### Project Information

- **Developed during**: Next Level Week Agents by Rocketseat
- **Repository**: [nwlagents-backend](https://github.com/1montandon/nwlagents-backend)
- **Maintainer**: [@1montandon](https://github.com/1montandon)

### Rocketseat Community

This project was created as part of the **Next Level Week Agents** event by [Rocketseat](https://rocketseat.com.br/), a Brazilian programming education platform focused on modern web technologies.

---

**Built with ❤️ during NLW Agents by Rocketseat**
