# 📘 Miniguia de Estudos com IA: Bancos de Dados e SQL

> Projeto desenvolvido para o desafio **"Explorando a IA como Ferramenta de Aprendizagem Ativa com NotebookLM"** da DIO.
> Ferramenta utilizada: [Google NotebookLM](https://notebooklm.google.com/)

---

## 🎯 Contexto e Objetivos

Escolhi como tema **Bancos de Dados relacionais e a linguagem SQL** (Structured Query Language), abordando desde os conceitos fundamentais até boas práticas de modelagem, escrita de queries e performance.

**Por que esse tema?** Atualmente curso Tecnólogo em Gestão da Tecnologia da Informação (GTI) e tenho como objetivo de carreira migrar minha experiência em gestão para uma posição de gestão de TI. Bancos de dados são a espinha dorsal de praticamente todo sistema corporativo (ERP, BI, e-commerce, controle de estoque), então entender como eles funcionam "por dentro" — não só escrever um `SELECT`, mas entender modelagem, integridade e performance — é essencial tanto para dialogar tecnicamente com equipes de desenvolvimento/dados quanto para tomar decisões melhores como gestor.

**Objetivos de estudo:**
- [ ] Entender o que é um SGBD (Sistema de Gerenciamento de Banco de Dados) relacional e como ele se organiza.
- [ ] Compreender as categorias da linguagem SQL (DDL, DML, DQL, DCL, TCL) e quando usar cada uma.
- [ ] Aprender a escrever consultas com `JOIN`, agregações e filtros de forma correta e eficiente.
- [ ] Entender os princípios de normalização e integridade referencial (chaves primárias/estrangeiras).
- [ ] Conhecer boas práticas de nomenclatura, indexação e escrita de queries que evitem armadilhas comuns de performance.
- [ ] Consolidar tudo em um material de revisão rápida (resumo + glossário + prompts) para consultas futuras.

---

## 📚 Curadoria de Fontes

Fontes abertas selecionadas e carregadas no NotebookLM (formato texto/PDF/link):

| # | Fonte | Tipo | Link |
|---|-------|------|------|
| 1 | **PostgreSQL Tutorial (Parte I — Documentação Oficial)** | Web/HTML | https://www.postgresql.org/docs/current/tutorial.html |
| 2 | **PostgreSQL 18 Documentation (PDF completo)** | PDF | https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf |
| 3 | **W3Schools SQL Tutorial** (referência rápida de sintaxe) | Web/HTML | https://www.w3schools.com/sql/ |
| 4 | **Mode SQL Tutorial** (didático, com exemplos práticos de análise de dados) | Web/HTML | https://mode.com/sql-tutorial/ |
| 5 | **Use The Index, Luke — A Guide to SQL Performance for Developers** (Markus Winand) | Web/HTML (licença CC BY-NC-ND) | https://use-the-index-luke.com/ |

> 💡 **Dica de uso no NotebookLM:** para os itens 1, 3 e 4, usei a opção "Website" ao adicionar a fonte, colando a URL diretamente. Para o item 2 (PDF), fiz o download antes e subi o arquivo. O item 5 tem várias páginas internas — subi as páginas "Anatomy of an Index" e "The Where Clause" separadamente, que são o núcleo do conteúdo sobre performance.

---

## 🧪 Engenharia de Prompts e "Cicatrizes"

Aqui documento as perguntas que fiz ao NotebookLM, o raciocínio por trás delas e as dificuldades encontradas no caminho.

### Rodada 1 — Exploração inicial

**Prompt:** `"Com base nas fontes carregadas, explique o que é um SGBD relacional e como ele se diferencia de um banco de dados NoSQL, em linguagem simples."`

- **Resposta obtida (resumo):** *[cole aqui o resumo da resposta real do NotebookLM]*
- **Fontes citadas pela IA:** *[liste as fontes/trechos que o NotebookLM apontou como referência]*
- **Observação:** as fontes que selecionei são focadas em PostgreSQL (relacional), então a IA tende a responder bem sobre o lado relacional, mas com pouca profundidade sobre NoSQL — o que fazia sentido, já que não subi nenhuma fonte sobre bancos não-relacionais. Ajustei o prompt na rodada seguinte para focar só no que as fontes realmente cobrem.

### Rodada 2 — Refinando o prompt (cicatriz #1)

**Prompt (tentativa 1):** `"Liste as boas práticas de SQL."`
- **Problema encontrado:** resposta muito genérica e superficial, misturando práticas de sintaxe com práticas de performance sem hierarquia.

**Prompt (tentativa 2 — refinado):** `"Com base apenas nas fontes carregadas, separe as boas práticas de SQL em duas categorias: (1) boas práticas de escrita/legibilidade de queries e (2) boas práticas de performance e uso de índices. Para cada item, cite de qual fonte a recomendação vem."`
- **Resposta obtida (resumo):** *[cole aqui]*
- **Lição aprendida:** prompts que pedem estrutura explícita (categorias, tabelas, citação da fonte) geram respostas muito mais úteis e verificáveis do que perguntas abertas. Pedir a citação da fonte também ajuda a identificar quando a IA está "inferindo" além do que as fontes dizem.

### Rodada 3 — Testando profundidade técnica

**Prompt:** `"Explique como um índice do tipo B-Tree acelera uma cláusula WHERE, usando a explicação do 'Use The Index, Luke' como base. Dê um exemplo prático."`
- **Resposta obtida (resumo):** *[cole aqui]*
- **Dificuldade encontrada:** na primeira tentativa, a resposta trouxe um exemplo genérico que não batia exatamente com a fonte. Precisei pedir explicitamente: `"Baseie o exemplo apenas no capítulo 'The Anatomy of an Index' da fonte, sem adicionar informação externa."` Isso reduziu bastante a "alucinação"/generalização.

### Rodada 4 — Geração de material de revisão

**Prompt:** `"Crie um glossário com os 15 termos mais importantes sobre SQL e bancos de dados relacionais mencionados nas fontes, com definição de uma frase cada."`
- **Resposta obtida (resumo):** *[cole aqui]*
- **Observação:** o NotebookLM é bom em consolidar terminologia espalhada entre várias fontes diferentes — isso economizou bastante tempo comparado a eu mesmo garimpar os termos manualmente.

> 🔧 **Principais "cicatrizes" (lições de troubleshooting):**
> 1. Perguntas abertas demais → respostas rasas. Pedir estrutura (tabela, categorias, número de itens) melhora muito a qualidade.
> 2. Pedir explicitamente para citar a fonte ajuda a auditar se a resposta é fiel ao material ou está "preenchendo lacunas" com conhecimento geral do modelo.
> 3. Quando a resposta mistura conceitos de fontes diferentes de forma confusa, é melhor restringir o prompt a uma fonte específica por vez.
> 4. Reformular o prompt pedindo "sem adicionar informação externa às fontes" é útil para checar se um conceito está de fato bem coberto pelo material selecionado.

---

## 🗂️ Miniguia de Estudo (Entrega Final)

### 1. Resumos Estruturados

#### O que é um Banco de Dados Relacional
Um banco de dados relacional organiza os dados em **tabelas** (linhas e colunas), onde cada tabela representa uma entidade (ex: `clientes`, `pedidos`, `produtos`). As relações entre tabelas são feitas por meio de **chaves primárias** (identificador único de cada registro) e **chaves estrangeiras** (referência à chave primária de outra tabela), garantindo integridade entre os dados.

#### As categorias da linguagem SQL
| Categoria | Sigla | Comandos principais | Função |
|---|---|---|---|
| Data Definition Language | DDL | `CREATE`, `ALTER`, `DROP` | Define/altera a estrutura (schema) do banco |
| Data Manipulation Language | DML | `INSERT`, `UPDATE`, `DELETE` | Manipula os dados dentro das tabelas |
| Data Query Language | DQL | `SELECT` | Consulta/lê os dados |
| Data Control Language | DCL | `GRANT`, `REVOKE` | Controla permissões de acesso |
| Transaction Control Language | TCL | `COMMIT`, `ROLLBACK`, `SAVEPOINT` | Controla transações (unidades atômicas de trabalho) |

#### JOINs — combinando tabelas
- **INNER JOIN**: retorna apenas os registros que têm correspondência em ambas as tabelas.
- **LEFT JOIN**: retorna todos os registros da tabela da esquerda, mesmo sem correspondência na direita (preenchendo com `NULL`).
- **RIGHT JOIN**: o inverso do LEFT JOIN.
- **FULL JOIN**: retorna todos os registros de ambas as tabelas, com ou sem correspondência.

#### Normalização
Processo de organizar tabelas para reduzir redundância e evitar inconsistências. As formas normais mais citadas:
- **1FN (1ª Forma Normal):** cada célula deve conter um único valor atômico (sem listas dentro de uma coluna).
- **2FN:** elimina dependências parciais (todo atributo não-chave depende da chave inteira, não de parte dela).
- **3FN:** elimina dependências transitivas (atributos não-chave não podem depender de outros atributos não-chave).

#### Índices e Performance
Um índice é uma estrutura auxiliar (geralmente uma **B-Tree**) que permite ao banco localizar registros sem varrer a tabela inteira (*full table scan*). Colunas usadas com frequência em `WHERE`, `JOIN` e `ORDER BY` são boas candidatas a índice — mas índices em excesso pioram a performance de `INSERT`/`UPDATE`, pois cada índice também precisa ser atualizado.

#### Boas práticas gerais
- Nomear tabelas e colunas de forma consistente e descritiva (ex: `snake_case`, nomes no singular ou plural — mas sempre o mesmo padrão em todo o projeto).
- Sempre definir chave primária e usar chaves estrangeiras para garantir integridade referencial.
- Evitar `SELECT *` em produção — especificar as colunas necessárias.
- Usar transações (`BEGIN`/`COMMIT`/`ROLLBACK`) para operações que precisam ser atômicas.
- Escrever queries pensando em como o banco vai executá-las (plano de execução), não só na sintaxe.

### 2. Glossário

| Termo | Definição |
|---|---|
| **SGBD** | Sistema de Gerenciamento de Banco de Dados — software que administra a criação, consulta e manutenção de bancos de dados (ex: PostgreSQL, MySQL, SQL Server). |
| **Chave Primária (PK)** | Coluna (ou conjunto de colunas) que identifica unicamente cada registro de uma tabela. |
| **Chave Estrangeira (FK)** | Coluna que referencia a chave primária de outra tabela, criando um relacionamento entre elas. |
| **Query** | Uma consulta/instrução SQL enviada ao banco de dados. |
| **JOIN** | Operação que combina linhas de duas ou mais tabelas com base em uma condição relacionada. |
| **Índice (Index)** | Estrutura de dados que acelera a busca de registros, evitando varredura completa da tabela. |
| **Normalização** | Processo de organizar dados para reduzir redundância e evitar anomalias de atualização. |
| **Transação** | Conjunto de operações executadas como uma unidade atômica: ou todas são aplicadas, ou nenhuma é. |
| **ACID** | Conjunto de propriedades (Atomicidade, Consistência, Isolamento, Durabilidade) que garantem confiabilidade em transações. |
| **Full Table Scan** | Quando o banco precisa ler todas as linhas de uma tabela por falta de índice adequado. |
| **Schema** | A estrutura/organização lógica do banco de dados (tabelas, colunas, tipos, relacionamentos). |
| **DDL / DML / DQL / DCL / TCL** | As cinco subcategorias de comandos SQL (ver tabela na seção de resumos). |

### 3. Prompts Reutilizáveis (para revisões futuras)

```
1. "Com base nas fontes carregadas, crie um resumo em tópicos sobre [TEMA] em no máximo 10 linhas."

2. "Gere 5 perguntas de múltipla escolha sobre [TEMA] usando apenas o conteúdo das fontes, para eu testar meu conhecimento."

3. "Explique [CONCEITO] como se eu estivesse aprendendo pela primeira vez, com um exemplo prático de query SQL."

4. "Compare [CONCEITO A] e [CONCEITO B] em formato de tabela, indicando quando usar cada um."

5. "Baseando-se apenas nas fontes (sem adicionar conhecimento externo), quais boas práticas essas fontes recomendam sobre [TEMA]? Cite a fonte de cada recomendação."

6. "Crie um glossário com os principais termos sobre [TEMA] presentes nas fontes."

7. "Quais são os erros mais comuns que iniciantes cometem em relação a [TEMA], segundo as fontes?"
```

---

## 🛠️ Como reproduzir este estudo

1. Acesse o [NotebookLM](https://notebooklm.google.com/) e crie um novo notebook.
2. Adicione as fontes listadas na seção **Curadoria de Fontes** (upload de PDF ou link direto).
3. Use os **Prompts Reutilizáveis** acima, substituindo `[TEMA]`/`[CONCEITO]` pelo assunto desejado.
4. Documente as respostas e ajustes de prompt na seção de **Engenharia de Prompts**, seguindo o mesmo formato usado aqui.

---

## 📌 Sobre este projeto

Projeto desenvolvido como parte do desafio de prático da [DIO](https://www.dio.me/) sobre uso do NotebookLM como ferramenta de aprendizagem ativa.
