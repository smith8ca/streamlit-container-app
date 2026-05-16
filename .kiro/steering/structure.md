# Project Structure

## Root Directory Layout

```
.
├── app.py                 # Main Streamlit application entry point
├── requirements.txt       # Python dependencies
├── Dockerfile            # Container configuration
├── .gitlab-ci.yml        # CI/CD pipeline definition
├── mkdocs.yml            # Documentation site configuration
├── README.md             # Project documentation and setup instructions
├── .dockerignore         # Docker build exclusions
├── .gitignore            # Git exclusions
├── ssl/                  # SSL certificates directory
│   ├── cert.pem         # SSL certificate
│   └── key.pem          # SSL private key
├── docs/                 # MkDocs documentation source
│   └── index.md         # Documentation homepage
└── .kiro/               # Kiro AI assistant configuration
    └── steering/        # AI guidance documents
```

## Key Conventions

### Application Code

- **app.py**: Single-file Streamlit application at project root
- Keep the main application logic simple and focused
- Use Streamlit's built-in components and conventions

### SSL Certificates

- Store certificates in the `ssl/` directory
- Use self-signed certificates for development
- Certificate files: `cert.pem` (public) and `key.pem` (private)

### Documentation

- MkDocs for project documentation in `docs/` directory
- README.md contains setup and deployment instructions
- Keep documentation synchronized with code changes

### Docker

- Use python:3.9-slim as base image for minimal footprint
- Application runs on port 443 inside container
- SSL certificates must be present before container starts
- Health check configured for Streamlit's internal endpoint

### CI/CD

- GitLab CI/CD with three stages: build, test, deploy
- Pipeline configuration in `.gitlab-ci.yml`
- Deployment targets production environment
