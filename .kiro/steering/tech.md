# Technology Stack

## Core Framework

- **Streamlit 1.35.0**: Web application framework for building data apps

## Dependencies

- **Python 3.9**: Runtime environment
- **pandas 2.2.2**: Data manipulation library
- **altair 5.3.0**: Declarative visualization library

## Infrastructure

- **Docker**: Containerization using python:3.9-slim base image
- **SSL/TLS**: Self-signed certificates for HTTPS support
- **GitLab CI/CD**: Automated pipeline with build, test, and deploy stages

## Common Commands

### Local Development

```bash
# Run the app locally with SSL
streamlit run app.py --server.port=443 --server.address=0.0.0.0 --server.sslKeyFile=ssl/key.pem --server.sslCertFile=ssl/cert.pem

# Generate new SSL certificates
openssl req -x509 -newkey rsa:4096 -nodes -out ssl/cert.pem -keyout ssl/key.pem -days 365
```

### Docker

```bash
# Build the Docker image
docker build -t streamlit-container-app .

# Run the container
docker run -d --name streamlit-app -p 443:443 streamlit-container-app
```

### Documentation

```bash
# Build/serve MkDocs documentation
mkdocs serve
mkdocs build
```

## Deployment

- Application runs on port 443 (HTTPS)
- Health check endpoint: `http://localhost:8501/_stcore/health`
- GitLab CI/CD pipeline handles automated deployment to production
