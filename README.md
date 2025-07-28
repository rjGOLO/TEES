# TEES
Trabalho final da disciplina Tópicos em Especiais em Engenharia de Software 2025.1

Especificação do Projeto Integrador

Curso: Engenharia de Software
Disciplina: Tópicos Especiais em Engenharia de Software
Instituição: Universidade do Estado da Bahia
Professor: Eduardo Manuel de Freitas Jorge
Projeto: ETL e Análise Semântica de Currículos Lattes com IA


1. Descrição Geral do Sistema

Este projeto visa desenvolver um sistema completo para processamento e análise de dados de currículos Lattes no formato XML. O sistema realizará ETL (Extração, Transformação e Carga) dos dados para um banco PostgreSQL, convertendo os textos em vetores com pgvector. Uma API REST, desenvolvida com FastAPI, permitirá buscas textuais e semânticas por produções científicas. Uma interface Next.js consumirá essa API. Por fim, os dados serão exportados para Power BI para análise OLAP.


2. Especificação de Requisitos

  2.1 Requisitos Funcionais (RF)

| Código | Descrição                                                   |
| ------ | ----------------------------------------------------------- |
| RF01   | Importar arquivos XML do currículo Lattes.                  |
| RF02   | Transformar e carregar os dados em PostgreSQL.              |
| RF03   | Gerar vetores a partir de títulos de produções científicas. |
| RF04   | Expor API REST para consultas por nome e termo textual.     |
| RF05   | Realizar buscas semânticas com embeddings.                  |
| RF06   | Exportar dados em CSV para uso no Power BI.                 |
| RF07   | Disponibilizar interface web responsiva para consultas.     |

  2.2 Requisitos Não Funcionais (RNF)

| Código | Descrição                                                |
| ------ | -------------------------------------------------------- |
| RNF01  | Executar todo o sistema em contêineres Docker.           |
| RNF02  | A API deve responder em até 2 segundos.                  |
| RNF03  | O banco deve suportar pgvector para operações vetoriais. |
| RNF04  | O front-end deve ser responsivo, em Next.js.             |


3. Casos de Uso

 Caso de Uso: Consultar Produções Científicas

Ator: Usuário (via Front-End)
Descrição: Permite buscar produções científicas por nome do pesquisador ou termo textual/semântico.

Fluxo Principal:
1. Usuário digita termo de busca.
2. Front-end envia requisição para a API.
3. A API processa a busca e retorna os resultados.
4. O front-end exibe os resultados em lista ou tabela.


4. Projeto Arquitetural

Arquitetura em Camadas:

Orquestração: Apache Hop para ETL (XML → PostgreSQL)
Banco de Dados: PostgreSQL + pgvector
Back-End: FastAPI com endpoints REST (busca textual e semântica)
Front-End: Next.js com consumo da API REST
Exportação: CSV para Power BI

> Diagrama da Arquitetura poderá ser elaborado em ferramentas como PlantUML ou Draw\.io.


5. Protótipo de Média Fidelidade

Protótipo visual da interface web com:

 Campo de busca por nome ou termo
 Lista de produções encontradas
 Botão de exportar CSV

> Sugestão: utilizar Figma ou Excalidraw para criar o layout.


 6. Modelo Entidade-Relacionamento (ER)

Entidades Principais:
pesquisadores (pesquisador\_id, nome, lattes\_id)
producao\_cientifica (id, pesquisador\_id, titulo, ano, tipo, vetor)
orientacoes (id, pesquisador\_id, tipo, titulo, ano)
premios, eventos, patentes etc. conforme necessidade dos dados XML

> O modelo pode ser implementado em PostgreSQL com chaves estrangeiras e extensão `pgvector` para a coluna `vetor` em `producao_cientifica`.



7. Entregas Previstas

| Etapa         | Entregável                                     |
| ------------- | ---------------------------------------------- |
| Nivelamento   | Scripts Hop, SQL, Python e tutoriais no GitHub |
| Especificação | Documento de análise e protótipos              |
| ETL           | Projeto no Apache Hop                          |
| Back-End      | API FastAPI com busca textual/semântica        |
| Front-End     | Interface Next.js consumindo API               |
| OLAP          | CSVs + dashboards Power BI                     |



Estudante: Reinaldo da Silva Júnior
Data: 28/07/2025
