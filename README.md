# N8N_SELF_HOSTING
N8N Self hosting kit
# Self-Hosted AI Stack with N8N Integration

This project combines TimescaleDB, Ollama, pgAI, and N8N to create a powerful self-hosted AI automation stack. The setup includes vector database capabilities, AI model serving, and workflow automation.

## 🚀 Features

- **TimescaleDB**: PostgreSQL 17 with vector extensions
- **Ollama**: AI model serving with GPU support
- **pgAI**: Vector operations and AI integration
- **N8N**: Workflow automation with worker support
- **Redis**: Job queue management
- **pgAdmin**: Database management interface

## 📋 Prerequisites

- Docker and Docker Compose
- NVIDIA GPU (optional, for AI acceleration)
- NVIDIA Container Toolkit (if using GPU)

## 🛠 Installation

1. Clone the repository:
```bash
git clone https://github.com/kuldeeptp/N8N_SELF_HOSTING.git
cd N8N_SELF_HOSTING
```

2. Create a `.env` file with the following content:
```properties
# PostgreSQL Configuration
POSTGRES_USER=root
POSTGRES_PASSWORD=password
POSTGRES_DB=n8n
POSTGRES_PORT=5432

# N8N Configuration
N8N_HOST=localhost
N8N_PORT=5678
N8N_PROTOCOL=http
N8N_ENCRYPTION_KEY=super-secret-key
N8N_USER_MANAGEMENT_JWT_SECRET=even-more-secret

# PgAdmin Configuration
PGADMIN_EMAIL=admin@admin.com
PGADMIN_PASSWORD=admin

# Redis Configuration
REDIS_PORT=6379
REDIS_PASSWORD=redis_password

# Ollama Configuration
OLLAMA_PORT=11434
```

3. Start the services:
```bash
docker compose up -d
```

## 🌐 Service Access

- **N8N**: `http://localhost:5678`
- **pgAdmin**: `http://localhost:5050`
- **Database**: `localhost:5432`
- **Ollama API**: `http://localhost:11434`
- **Redis**: `localhost:6379`

## 📁 Project Structure

```
.
├── docker-compose.yml    # Service definitions
├── .env                 # Environment variables
└── README.md           # This file
```

## 🔧 Service Details

### TimescaleDB (Database)
- PostgreSQL 17 with TimescaleDB extension
- Includes pgvector and pg_embedding for vector operations
- Persistent data storage
- Health checks enabled

### Vectorizer Worker
- Handles vector operations for AI functionality
- Connects to TimescaleDB
- Automatic polling for new tasks

### Ollama
- AI model serving
- GPU support enabled
- Persistent model storage
- API exposed for integration

### N8N
- Main automation service and worker process
- PostgreSQL backend for data storage
- Redis-based job queue
- Secure encryption and JWT configuration

### Redis
- Job queue management
- Password protection
- Persistence enabled
- Health monitoring

### pgAdmin
- Web-based database management
- Persistent configuration storage
- Direct database access

## 📊 Data Persistence

All services use Docker named volumes for data persistence:
- `postgres_data`: Database files
- `ollama_data`: AI model files
- `pgadmin_data`: pgAdmin configuration
- `n8n_data`: N8N workflows and data
- `n8n_worker_data`: Worker-specific data
- `redis_data`: Queue and job data

## ⚙️ Configuration

### Environment Variables
Modify the `.env` file to customize:
- Database credentials
- Service ports
- N8N security settings
- Redis password
- pgAdmin access

### Security Notes
- Change all default passwords before deployment
- Use strong encryption keys
- Keep `.env` file secure
- Never commit sensitive data to version control

## 🔐 Production Deployment

For production environments:
1. Use strong passwords and encryption keys
2. Enable SSL/TLS
3. Configure proper network security
4. Regular backup of volumes
5. Monitor service health
6. Update images regularly

## 📝 License

[Add your license information here]

## 👥 Contributing

[Add contribution guidelines here]

## 📫 Support

[Add support contact information here]
