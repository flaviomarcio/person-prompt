# Prompts para analise e criação dos scripts de bancos de dados dos projetos

## Documentação de projetos java e node

Tem por objetivo analisar e gerar DDL dos models de um projetos.

```text
1. Faça a analise o código com foco nos models.
2. Crie separadamente os arquivos:
    - clear
        - literamente aqui ficaram trucantes de cada objeto criado.
        - Usar [if exists] desde que o banco de dados tenha suporte
    - drops.sql
        - literamente aqui ficaram drops de cada objeto criado.
        - Usar [if exists teste e equivalente] desde que o banco de dados para exivitar erros onde o objeto ou field ja fora criado.
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if exists].
    - schemas.sql, Apenas esquemas usados para conter os objetos
    - sequences.sql, Incluir os sequences indicados no model desde havendo suporte a generator ou generatores no banco de dados configurado no projeto,
    - tables.sql, tabelas dos models
        - Não deve incluir nenhum tipo de drop aqui
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if exists] ou [if not exists].
        - Tabelas sem definição de PK, FK, tablespace, triggers
        - Gerar separadamente create table apenas com o field que será a PK
        - Gerar separadamente com alter table para fields que não são PK
        - Particiladirades do oracle
        - Se no projeto o field indicar tipo UUID e houver algum converter registrado publicamente no projeto ou na configuração do field ficar claro que está configurado como texto então considerar usar varchar(36)
        - Se no projeto o field indicar tipo boolean e houver algum converter registrado publicamente no projeto ou na configuração do field ficar claro que está configurado como texto então considerar usar o tipo ou conversão indicada para o campo.
        - Se no projeto o field indicar tipo boolean for necessário criar um campo numerico considerar criar sempre como integer ao em vez de bit, smallint ou tipos equivalentes.

        - Se o field for String e este não tiver a length definido considerar 255.
    - constraints-pk.sql, PK utilizadas nos models
        - FK isoladas do create table
        - Não deve incluir nenhum tipo de drop aqui
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if not exists].
        - Seguir a formatação para nomear as constraints: pk__${table-name}_${fields-names}. 
    - constraints-fk.sql, FK utilizadas nos models
        - Não deve incluir nenhum tipo de drop aqui
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if not exists].
        - Seguir a formatação para nomear as constraints: fk__${table-name}_${fields-names}. 
    - constraints-check.sql, constraits utilizadas nos fields dos models para validar dados como, [1,2,3] ou ['A','B','C']
        - Não deve incluir nenhum tipo de drop aqui
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if not exists].        
        - criar constraints para objeto cuja o model tem alguma tratativa como apenas incluir apenas ['A','B','C'] via configuração direta no field
        - Seguir a formatação para nomear as constraints: fk__${table-name}_${fields-names}_${seq-table-idx}. 
        - Seq-table-idx é incremental iniciando de 1 e alinhando com zeros a esquerda, ex: 01, 002.
    - indexes.sql, indices relacionados a FKs
        - Não deve incluir nenhum tipo de drop aqui, se possivel create or replace de forma concorrente no banco de dados.
        - Usar equivalente a [select object_id('object_name')] em banco de dados ou comandos que não tenham suporte a [if not exists].
        - Seguir a formatação para nomear indices
            - Indices FKs: ix_fk__${table-name}_${fields-names}_${seq-table-idx}.
            - Indices Uniques: ix_un__${table-name}_${fields-names}_${seq-table-idx}.
            - Indices Normals: ix_un__${table-name}_${fields-names}_${seq-table-idx}. 
            - Seq-table-idx é incremental iniciando de 1 e alinhando com zeros a esquerda, ex: 01, 002.
        - Deve criar indices para FK nos models
        - Deve criar indices para fields claramente utilizados em consultas
            - Analisar order consultada para sugestão de indice mais seletivo, ex: 2 funcoes uma em cadastro consulta por [nome] e outra por [data] e nome, considerar se é melhor criar 1 indice para ambos, como apenas [nome] ou [data], ou criar os dois indices.
            - Façá considerações diante de seletividade:
                - ex: se [data] for localdate é um otimo campo para indice, mas se ele for timestamp ou datetimes já tem a performance prejudica, contudo se ainda sim pode estar sendo gravado com hora 00:00:00 sendo assim torna-se novamente um bom campo para indice.
                - Se o campo [date] for timestamp o o filtro via controller iniciar com date ou localdate, considerar usar estrategia de ajuste do dado do campo como cast, converter  desde o banco de dados tenha suporte a isso. obs: postgres tem suporte a isso um campo timestamp [data] pode se tornar apenas date assim: create index un_table_name on table_name(data::date, name).

    - init.data 
    - fake-data.sql 
```