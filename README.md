# n8n with PostgreSQL and pgvector

A Docker Compose setup for running [n8n](https://n8n.io/) (workflow automation platform) with PostgreSQL database enhanced with [pgvector](https://github.com/pgvector/pgvector) extension for vector similarity search and AI/ML workflows.

## Features

- 🚀 **n8n Workflow Automation**: Visual workflow builder for automating tasks and integrations
- 🐘 **PostgreSQL with pgvector**: Vector database support for AI/ML use cases
- 🐳 **Docker Compose**: Easy deployment and orchestration
- 🔒 **Environment-based Configuration**: Secure configuration management
- 📦 **Persistent Data**: Volume mounting for data persistence

## Prerequisites

- Docker and Docker Compose installed
- Basic understanding of n8n workflows
- PostgreSQL knowledge (optional but helpful)

## Quick Start

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd n8n-pgvector
   ```

2. **Configure environment variables**
   ```bash
   cp .example.env .env
   # Edit .env file with your configuration
   ```

3. **Start the services**
   ```bash
   docker-compose up -d
   ```

4. **Access n8n**
   Open your browser and navigate to `http://localhost:5678`

## Configuration

### Environment Variables

Copy `.example.env` to `.env` and configure the following variables:

```env
# Database Configuration
DB_POSTGRESDB_HOST=postgres
DB_POSTGRESDB_PORT=5432
DB_POSTGRESDB_DATABASE=n8n
DB_POSTGRESDB_USER=n8n
DB_POSTGRESDB_PASSWORD=your_secure_password

# n8n Configuration
N8N_ENCRYPTION_KEY=your_encryption_key
```

### n8n Configuration

The setup includes the following n8n configurations:
- **Host**: Configured for `n8n.enso.sh` (update as needed)
- **Webhook URL**: `https://n8n.enso.sh/`
- **Runners**: Enabled for improved performance
- **Workflow Management**: Active for persistence

### Optional Configuration

Uncomment and configure these options in `docker-compose.yml` as needed:

- **HTTP Basic Auth**: Add basic authentication to n8n
- **Timezone**: Set your preferred timezone (default: America/Chicago)

## PostgreSQL with pgvector

This setup uses the `pgvector/pgvector:pg16` image which includes:
- PostgreSQL 16
- pgvector extension for vector operations
- Support for similarity search and embeddings

### Enabling PostgreSQL

To enable the PostgreSQL service:

1. Uncomment the `postgres` service section in `docker-compose.yml`
2. Uncomment the `depends_on` section in the n8n service
3. Update your `.env` file with database credentials

## Usage

### Starting Services

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

### Accessing Services

- **n8n Interface**: `http://localhost:5678`
- **PostgreSQL**: `localhost:5432` (when enabled)

### Data Persistence

Data is persisted using Docker volumes:
- `n8n_data`: n8n configuration and workflows
- `n8n-postgres-data`: PostgreSQL data (when enabled)

## Vector Operations with pgvector

With pgvector enabled, you can:
- Store and query vector embeddings
- Perform similarity searches
- Build AI/ML workflows with semantic search capabilities

Example use cases:
- Document similarity search
- Recommendation systems
- Semantic text analysis
- Image similarity matching

## Troubleshooting

### Common Issues

1. **Port conflicts**: Ensure ports 5678 and 5432 are not in use
2. **Permission issues**: Check Docker permissions and file ownership
3. **Database connection**: Verify PostgreSQL service is running and accessible

### Logs

Check service logs for debugging:
```bash
# n8n logs
docker-compose logs n8n

# PostgreSQL logs (if enabled)
docker-compose logs postgres
```

## Development

For development purposes:
1. Mount additional volumes for custom nodes or configurations
2. Use environment variables for different deployment stages
3. Consider using Docker networks for service isolation

## Security Considerations

- Change default passwords
- Use strong encryption keys
- Enable HTTPS in production
- Configure firewall rules appropriately
- Regularly update Docker images

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

[Add your license information here]

## Support

- [n8n Documentation](https://docs.n8n.io/)
- [pgvector Documentation](https://github.com/pgvector/pgvector)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

---

**Note**: This setup is configured for the domain `n8n.enso.sh`. Update the host and webhook URL configurations in `docker-compose.yml` to match your deployment environment.
