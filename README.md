# Nginx Reverse Proxy Stack (Docker + Ubuntu Server)

Ambiente multi-container configurado no Ubuntu Server utilizando **Docker Compose** com **Nginx** como proxy reverso na frente de uma API leve e pronta para testes de infraestrutura.

## O que este projeto implementa
- **Proxy Reverso & SSL/TLS:** Nginx exposto nas portas `80` e `443` com redirecionamento para HTTPS, headers de proxy (`X-Forwarded-*`) e cabeçalhos básicos de segurança.
- **Isolamento de Rede:** Comunicação entre Nginx e API feita exclusivamente por uma rede Docker interna (`bridge`), sem expor portas internas no host.
- **Persistência:** Volumes para certificados SSL, configurações do Nginx e logs.
- **Healthchecks:** Monitoramento de saúde dos contêineres e controle de inicialização (`depends_on` com `service_healthy`).
- **API Pronta:** Serviço leve atrás do proxy (ex.: `traefik/whoami` ou `http-https-echo`) para validar roteamento, headers e TLS sem foco em desenvolvimento de CRUD.
