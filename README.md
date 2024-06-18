## Generate new SSL certs

If you would like to create new SSL certificates, run the following from the root directory:

```bash
openssl req -x509 -newkey rsa:4096 -nodes -out ssl/cert.pem -keyout ssl/key.pem -days 365
```

## Launching the app

To launch the application, execute the following from the root directory:

```bash
streamlit run app.py --server.port=443 --server.address=0.0.0.0 --server.sslKeyFile=ssl/key.pem --server.sslCertFile=ssl/cert.pem
```

## Docker Container Development

Build docker image:

```bash
docker build -t streamlit-container-app .
```

Run the docker image:

```bash
docker run -d --name streamlit-app -p 443:443 streamlit-container-app
```

## Sources & References
