# Prompts para analise e documentação dos projetos

## Documentação de projetos java e node

Tem por objetivo documentar classes e metodos das aplicações, bem como aquivos de configuração gerando assim um *README.md* para o projeto trabalhado

```text
1. Analise o código.
2. Documente todos os arquivos de codigo fonte.
    1. Incluir comentarios nas classes, metodos e adapters do projeto.
    2. Identifique os controllers e DTOs e documente para o swagger.
3. Gere um README.md para o projeto, se README.md já existir então sobrescreva ele.
4. O README.md deve conter informações por relevancia ao desenvolvedor.
5. No README.md deve conter informações do projeto, onde:
    1. como objetivo e principais classes e colocar informações sobre enums.
    2. No README.md deve conter detalhes de todas as classes.
    3. No README.md deve conter detalhes dos debitos tecnicos da aplicação com a recomendações para implementação.
6. No README.md deve conter informações dos arquivos de configurações do projeto caso existam, onde:
    1. No README.md deve ser mais detalhado no application.yml onde tratar do spring.cloud.gateway
    2. No README.md deve ser mais detalhado no application.yml onde tratar do spring.cloud.vault
    3. No README.md deve ser mais detalhado no application.yml onde tratar do spring.doc
    4. No README.md deve ser mais detalhado no application.yml onde tratar do app.config
    5. No README.md deve conter detalhes do nginx.config se este existir.
    6. No README.md deve conter detalhes do vite.config se este existir.
    7. No README.md deve conter detalhes do DDL se no root uma pasta */db e ou */ddl
    8. No README.md deve conter detalhes das scripts shell se no root uma pasta */script e ou */scripts
    9. No README.md deve conter detalhes do Docker se houver Dockerfile e ou docker-compose.yml
7. No README.md deve conter informações da qualidade de codigo e cobertura de testes, onde:
    1. Cobertura de testes de 100% para services.
    2. Cobertura de testes de 100% para utils.
    3. Nenhuma regra de negocio ou funçoes em DTOs e Models
    4. Aplicação do SOLID.
    5. Nos repositorios as consultas devem ser sempre que possivel na forma declarativa evitando o uso de queries explicitas.
    6. Forneça exemplos para os items no deste topico
```
