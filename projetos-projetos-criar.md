# Prompts para criação de projetos python

## Api simples usando MVC

Tem por objetivo documentar classes e metodos das aplicações, bem como aquivos de configuração gerando assim um *README.md* para o projeto trabalhado

```text
1. Crie um projeto Api em python 
2. Deve criar uma Api
    1. Deve utilizar bibliotecas com os release mais relevantes.
    2. O projeto será um crud e deve ser usado um MVC.
    3. Deve arquiteturalmente deve isolar controllers, configs, dtos, models, services e testes
    4. Deve ter 100% de cobertura de testes
    5. A entidade será Person e seu Dto será PersonDto
    6. Tanto o model quando o Dto deve ter id, createdAt, updatesAt, name, active
    7. Deve usar o mesmo Dto PersonDto para input e output
    8. Deve conter o metodo GET list com retorno sendo uma lista de PersonDto com parametro da requisição sendo o name com tipo String
    9. Deve conter o metodo GET find com retorno sendo PersonDto e com parametro da requisição sendo o id com tipo UUID
    10. Deve conter o metodo POST e PUT save com retorno sendo PersonDto e com parametro da requisição sendo o person com tipo PersonDto
    11. Deve conter o metodo DELETE remove sem retorno e com parametro da requisição sendo id com tipo UUID
3. Deve utilizar banco de dados postgres
    1. Utilizando os models como modelo crie um pasta db/ e nela distribuita o ddl nos arquivos arquivo tables.sql, constrains-pk.sql, constrains-fk.sql, indexes.sql, views.sql, init-data.sql
    2. Deve gerar um arquivo db/init-db.sql contento dos os comandos para iniciar o postgres
4. Deve criar um ambiente docker
    1. Deve incluir um Dockerfile para gerar imagem no ambiente de produção
    2. Deve incluir um docker-compose.yml para uso local com o postgres inicializando com o arquivo db/init-db.sql
5. Deve criar README.md
    1. Deve conter informações do projeto
    2. Deve conter informações desde a instalação de dependencias a execução do projeto python
    3. Deve conter informações de como inicializar o docker compose para o desenvolvedor
    4. Deve ter informações dos scripts de bancos de dados
```