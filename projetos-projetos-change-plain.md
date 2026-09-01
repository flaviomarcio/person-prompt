# Prompts para criação de planos de ação

## Plano de ação baseado em XML de uma task

Tem por objetivo documentar classes e metodos das aplicações, bem como aquivos de configuração gerando assim um *README.md* para o projeto trabalhado

```text
1. Atuar para criar um plano de ação neste repositório e considere a palavra TASK-NAME a representação TTT-1234 sendo esta a tarefa a ser feita.
2. O diretório do projeto e aser modificado é diretório corrente.
3. Existe um workspace para os trabalhos
    3.1 O diretório do workspace é: ${HOME}/work/spaces
    3.2 O workspace contem arquivo xml principal TASK-NAME.xml, você deve identificar de qual ferramenta é, ex: Jira
    3.3 Além do arquivo TASK-NAME.xml todos os arquivos TASK-NAME*.* devem ser considerados anexos, uma resalva apenas para arquivo markdown(*.md) estes podem ter sido gerados por uma A.I.
    3.4 Arquivos com conteudo JSON são especialmente importantes, pois podem ser logs e documentação openapi
    3.5 Arquivos de imagens devem ser interpretados logo eles podem ser logs e prints de tela feito pelo usuário.
4. Crie se necessário o diretório ${HOME}/work/spaces
5. Solicite permissão para para ações de leitura e gravação nos diretório de arquivo e do projeto
6. Analise do XML, este xml encontrask em TASK-NAME.xml, esta analise do XML deve compreender a necessidade da modificação
7. Crie um arquivo TASK-NAME-aprendizado-ai.md onde você deve armazenar o que aprendeu nas analises feitas no diretorio
8. Crie para a modificação um plano de ação no padrão markdown no arquivo TASK-NAME-plain.md
9. Solicite permissão para ler e gravar arquivos bem como comandos no diretorio do workspace.
```