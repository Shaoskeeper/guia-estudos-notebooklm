# 📘 Miniguia de Estudos com IA: Bancos de Dados e SQL

> Projeto desenvolvido para o desafio **“Explorando a IA como Ferramenta de Aprendizagem Ativa com NotebookLM”** da DIO.
Ferramenta utilizada: Google NotebookLM
> 

---

## 🎯 Contexto e Objetivos

Escolhi como tema **Bancos de Dados relacionais e a linguagem SQL** (Structured Query Language), abordando desde os conceitos fundamentais até boas práticas de modelagem, escrita de queries e performance.

**Por que esse tema?** Atualmente curso Tecnólogo em Gestão da Tecnologia da Informação (GTI) e tenho como objetivo de carreira migrar minha experiência em gestão para uma posição de gestão de TI. Bancos de dados são a espinha dorsal de praticamente todo sistema corporativo (ERP, BI, e-commerce, controle de estoque), então entender como eles funcionam “por dentro” — não só escrever um `SELECT`, mas entender modelagem, integridade e performance — é essencial tanto para dialogar tecnicamente com equipes de desenvolvimento/dados quanto para tomar decisões melhores como gestor.

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
| --- | --- | --- | --- |
| 1 | **PostgreSQL Tutorial (Parte I — Documentação Oficial)** | Web/HTML | https://www.postgresql.org/docs/current/tutorial.html |
| 2 | **PostgreSQL 18 Documentation (PDF completo)** | PDF | https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf |
| 3 | **W3Schools SQL Tutorial** (referência rápida de sintaxe) | Web/HTML | https://www.w3schools.com/sql/ |
| 4 | **Mode SQL Tutorial** (didático, com exemplos práticos de análise de dados) | Web/HTML | https://mode.com/sql-tutorial/ |
| 5 | **Use The Index, Luke — A Guide to SQL Performance for Developers** (Markus Winand) | Web/HTML (licença CC BY-NC-ND) | https://use-the-index-luke.com/ |

> 💡 **Dica de uso no NotebookLM:** para os itens 1, 3 e 4, usei a opção “Website” ao adicionar a fonte, colando a URL diretamente. Para o item 2 (PDF), fiz o download antes e subi o arquivo. O item 5 tem várias páginas internas — subi as páginas “Anatomy of an Index” e “The Where Clause” separadamente, que são o núcleo do conteúdo sobre performance.
> 

---

## 🧪 Engenharia de Prompts e “Cicatrizes”

Aqui documento as perguntas que fiz ao NotebookLM, o raciocínio por trás delas e as dificuldades encontradas no caminho.

### Rodada 1 — Exploração inicial

**Prompt:** `"Com base nas fontes carregadas, explique o que é um SGBD relacional e como ele se diferencia de um banco de dados NoSQL, em linguagem simples."`

- **Resposta obtida (resumo):**

**O que é um SGBD Relacional?**

Um **SGBD (Sistema de Gerenciamento de Banco de Dados)** é um conjunto de programas de computador que serve para definir, administrar, processar e proteger bancos de dados, atuando como uma ponte (interface) entre os usuários ou aplicativos e as informações guardadas.

Quando ele é **Relacional** (também chamado de **SGBDR**), significa que organiza as informações em estruturas chamadas **tabelas** (conhecidas matematicamente como relações). Pense nelas como planilhas compostas por:

- **Colunas:** Que representam os atributos ou características do dado (como "Nome", "E-mail" ou "Telefone").
- **Linhas:** Que contêm os registros individuais de cada informação (por exemplo, os dados específicos de um cliente).

Nesse modelo, as tabelas se conectam entre si por meio de chaves (como chaves primárias e estrangeiras), garantindo que as informações fiquem organizadas e sem repetições desnecessárias. Para acessar e manipular esses dados, os SGBDs relacionais utilizam a linguagem padrão universal **SQL (Linguagem de Consulta Estruturada)**. Exemplos populares incluem o **PostgreSQL**, **MySQL**, **Oracle** e o **SQL Server**.

---

**Como ele se diferencia de um banco de dados NoSQL?**

Os bancos de dados **NoSQL** (termo associado a "não apenas SQL") surgiram para lidar com o armazenamento de dados flexíveis, não estruturados e em escalas massivas que os sistemas tradicionais têm dificuldade de processar.

As principais diferenças entre os dois modelos estão em quatro pontos práticos:

1. **Estrutura dos dados (Esquema ou Schema):**
    - **Relacional (SQL):** Possui um **esquema rígido e predefinido**. É preciso planejar a modelagem física (como as tabelas e colunas se organizarão) antes de salvar qualquer informação.
    - **NoSQL:** Possui um **esquema dinâmico e flexível**. Os dados podem ser guardados sem estrutura predefinida em formatos como **documentos** (JSON/BSON), **chave-valor**, **famílias de colunas** ou **grafos**.
2. **Como eles crescem (Escalabilidade):**
    - **Relacional:** É projetado principalmente para crescer de forma **vertical**, ou seja, aumentando os recursos físicos (CPU, memória RAM ou SSD) do mesmo servidor. A distribuição horizontal (em várias máquinas) é complexa e possui suporte limitado.
    - **NoSQL:** É projetado nativamente para crescer de forma **horizontal**. Ele distribui a carga de trabalho de maneira muito mais fácil adicionando novos servidores de baixo custo (nós) ao sistema.
3. **Regras de transação (Consistência):**
    - **Relacional:** Garante alta confiabilidade seguindo as propriedades **ACID** (Atomicidade, Consistência, Isolamento e Durabilidade). Isso assegura que transações críticas (como transferências bancárias) ocorram com segurança total ou falhem por completo para evitar inconsistência de dados.
    - **NoSQL:** Baseia-se no **Teorema CAP** e foca em velocidade e alta disponibilidade, oferecendo frequentemente a chamada **consistência eventual** (onde os dados atualizados podem demorar alguns segundos para se propagar em todas as máquinas de um grupo).
4. **Busca e cruzamento de informações:**
    - **Relacional:** É extremamente forte para realizar consultas cruzadas complexas entre diferentes tabelas utilizando o comando **JOIN**.
    - **NoSQL:** Não costuma ter suporte para JOINs complexos, o que faz com que cruzamentos de informações precisem ser resolvidos pela própria lógica de programação do aplicativo.

Em suma: para dados organizados e que exigem garantia de consistência forte (como finanças ou cadastros), usa-se o **Relacional**. Para grandes volumes de dados desestruturados e rápida escalabilidade, opta-se pelo **NoSQL**.

- **Fontes citadas pela IA:**
- https://www.casasbahia-imagens.com.br/Control/ArquivoExibir.aspx?Id
- https://www.compararsoftware.com.br/gerenciamento-de-banco-de-dados
- https://www.mpgcamb.com/wp-content/uploads/2024/12/Abraham-Silberschatz-Henry-F.-Korth-S.-Sudarshan-Database-System-Concepts-McGraw-Hill-Education-2019.pdf
- https://www.opservices.com.br/principais-bancos-de-dados/
- **Observação:** as fontes que selecionei são focadas em PostgreSQL (relacional), então a IA tende a responder bem sobre o lado relacional, mas com pouca profundidade sobre NoSQL — o que fazia sentido, já que não subi nenhuma fonte sobre bancos não-relacionais. Ajustei o prompt na rodada seguinte para focar só no que as fontes realmente cobrem.

### Rodada 2 — Refinando o prompt (cicatriz #1)

**Prompt (tentativa 1):** `"Liste as boas práticas de SQL."`
- **Problema encontrado:** resposta muito genérica e superficial, misturando práticas de sintaxe com práticas de performance sem hierarquia.

**Prompt (tentativa 2 — refinado):** `"Com base apenas nas fontes carregadas, separe as boas práticas de SQL em duas categorias: (1) boas práticas de escrita/legibilidade de queries e (2) boas práticas de performance e uso de índices. Para cada item, cite de qual fonte a recomendação vem."`
- **Resposta obtida (resumo):** 

**(1) Boas Práticas de Escrita e Legibilidade de Queries**

- **Evitar o uso de SELECT * e especificar as colunas explicitamente**: O uso de **`SELECT *`** é amplamente considerado uma má prática em códigos de produção, pois qualquer adição futura de colunas altera os resultados da consulta e pode quebrar a aplicação. Listar as colunas de forma explícita garante maior segurança estrutural, além de facilitar a compreensão do código. *(Fontes: "https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf"; "SQL JOIN: Aprenda INNER, LEFT, RIGHT, FULL e CROSS | Alura Cursos Online"; "PRÁTICAS E FERRAMENTAS PARA OTIMIZAÇÃO DO DESEMPENHO...")*
- **Utilizar indentação e comentários apropriados**: Escrever instruções SQL levando em consideração boas práticas de desenvolvimento, como recuos (indentação) e comentários (**`/* */`** ou **`-`**), facilita a manutenção do código e a colaboração entre equipes. *(Fonte: "PRÁTICAS E FERRAMENTAS PARA OTIMIZAÇÃO DO DESEMPENHO...")*
- **Preferir a sintaxe ANSI JOIN moderna sobre a sintaxe antiga**: A sintaxe de junção que lista tabelas separadas por vírgula no **`FROM`** e aplica a relação no **`WHERE`** (ex: **`FROM tabela1, tabela2 WHERE tabela1.id = tabela2.id`**) é obsoleta. Deve-se sempre adotar a cláusula explícita **`INNER JOIN`** associada à instrução **`ON`**. *(Fonte: "SQL JOIN: Aprenda INNER, LEFT, RIGHT, FULL e CROSS | Alura Cursos Online")*
- **Usar a cláusula ON explícita em vez de filtros no WHERE**: Para melhor legibilidade, especifique as condições de junção de tabelas claramente na cláusula **`ON`** ao invés de misturá-las com filtros de registros utilizando o **`WHERE`**. *(Fonte: "SQL JOIN: Aprenda INNER, LEFT, RIGHT, FULL e CROSS | Alura Cursos Online")*
- **Qualificar os nomes das colunas em consultas com múltiplos JOINs**: É considerado um bom padrão de estilo qualificar todas as colunas (ex: **`tabela.coluna`**) em queries de junção. Isso evita falhas de execução caso uma coluna com nome idêntico seja adicionada futuramente em qualquer uma das tabelas envolvidas. *(Fonte: "https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf")*
- **Utilizar apelidos (aliases) de tabelas**: O uso de aliases facilita a leitura e a manutenção do código, especialmente em consultas complexas que contêm múltiplos JOINs. *(Fonte: "SQL JOIN: Aprenda INNER, LEFT, RIGHT, FULL e CROSS | Alura Cursos Online")*
- **Usar CTEs (Common Table Expressions) para simplificar subconsultas complexas**: Em vez de aninhar várias subconsultas dentro do **`FROM`** ou do **`WHERE`** (o que torna a lógica confusa), utilize a cláusula **`WITH`** (CTE) para dividir a instrução em blocos menores e mais inteligíveis. *(Fontes: "Database System Concepts, Seventh Edition"; "Advanced SQL Techniques to Transform Data Analysis - DASCA")*
- **Estilo na escrita de restrições CHECK**: Restrições de verificação que se aplicam a um único atributo devem ser declaradas junto à própria coluna, enquanto validações complexas que cruzam múltiplos atributos devem ser colocadas separadamente ao final da instrução **`CREATE TABLE`**. *(Fonte: "Database System Concepts, Seventh Edition")*
- **Usar parênteses ao combinar operadores lógicos**: Para evitar ambiguidades na ordem de precedência das condições de filtro, use sempre parênteses para agrupar expressões combinadas com **`AND`**, **`OR`** e **`NOT`**. *(Fonte: "SQL Para Leigos")*

---

**(2) Boas Práticas de Performance e Uso de Índices**

- **Limitar a seleção de dados ao estritamente necessário**: Evitar a seleção de colunas desnecessárias reduz a transferência de dados na rede e aumenta sensivelmente a performance da query. *(Fontes: "Advanced SQL Techniques..."; "Entendendo a Indexação..."; "OTIMIZAÇÃO DE CONSULTAS SQL..."; "PRÁTICAS E FERRAMENTAS...")*
- **Aplicar filtros precocemente (Early Filtering)**: Filtre os dados o mais cedo possível para reduzir o volume de registros processados nas etapas seguintes. Aplique filtros do **`WHERE`** antes de realizar operações de **`JOIN`**. *(Fontes: "Advanced SQL Techniques..."; "OTIMIZAÇÃO DE CONSULTAS SQL...")*
- **Realizar agregações o quanto antes**: Ao trabalhar com a cláusula **`GROUP BY`**, execute as agregações de dados o mais cedo possível na consulta, minimizando o volume de dados que precisará ser manipulado mais adiante. *(Fonte: "Advanced SQL Techniques...")*
- **Criar índices estrategicamente nas colunas mais buscadas**: Certifique-se de manter índices criados nas colunas que aparecem frequentemente em cláusulas **`WHERE`**, critérios de ordenação (**`ORDER BY`**) ou condições de junção (**`JOIN`**). *(Fontes: "Advanced SQL Techniques..."; "Entendendo a Indexação..."; "SQL JOIN...")*
- **Prestar atenção à ordem das colunas em índices compostos**: A estruturação de um índice composto funciona da esquerda para a direita. Portanto, posicione primeiro as colunas que serão testadas por igualdade e, depois, as colunas usadas para buscas de intervalos. *(Fonte: "Entendendo a Indexação...")*
- **Aproveitar índices de cobertura (Covering Indexes)**: Crie índices projetados para incluir colunas de retorno frequente como "carga útil" (utilizando a cláusula **`INCLUDE`**). Isso permite que o banco de dados realize um "Index-Only Scan" e retorne a informação diretamente do índice, sem precisar acessar fisicamente a tabela no disco. *(Fontes: "Entendendo a Indexação..."; "https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf")*
- **Evitar a sobre-indexação de tabelas**: Criar índices em excesso prejudica a performance, pois cada índice precisa ser atualizado a cada operação de escrita (**`INSERT`**, **`UPDATE`** e **`DELETE`**), além de aumentar o espaço de armazenamento em disco. *(Fontes: "Entendendo a Indexação..."; "Melhores práticas para se trabalhar com índices - DevMedia")*
- **Substituir subconsultas por JOINs**: Otimize o desempenho de processamento substituindo subconsultas internas por operações de junção (**`JOIN`**) equivalentes sempre que aplicável. *(Fonte: "OTIMIZAÇÃO DE CONSULTAS SQL...")*
- **Usar EXISTS em vez de COUNT para testes de existência**: Quando você precisa apenas verificar se um registro existe, usar **`EXISTS`** é muito mais eficiente. O banco de dados interrompe a varredura assim que localiza a primeira correspondência, ao contrário do **`COUNT`**, que varre todas as linhas qualificadas. *(Fonte: "PRÁTICAS E FERRAMENTAS...")*
- **Evitar operadores de comparação negativos**: Condições de pesquisa negativas (como **`NOT IN`**, **`NOT BETWEEN`** ou **`IS NOT NULL`**) reduzem a velocidade de recuperação de dados, pois costumam desabilitar o uso eficiente de índices e forçar o SGBD a avaliar registro por registro. *(Fonte: "PRÁTICAS E FERRAMENTAS...")*
- **Utilizar a ferramenta EXPLAIN para analisar o plano de execução**: Sempre valide suas consultas utilizando a ferramenta **`EXPLAIN`** (ou **`EXPLAIN ANALYZE`**). Ela revela como o planejador do SGBD processará a query, permitindo identificar gargalos de performance e scans sequenciais desnecessários em tabelas grandes. *(Fontes: "Advanced SQL Techniques..."; "Entendendo a Indexação..."; "OTIMIZAÇÃO DE CONSULTAS SQL...")*
- **Remover índices temporariamente antes de cargas massivas de dados**: Ao realizar inserções massivas de dados (bulk loads), é mais rápido remover os índices não primários da tabela, executar a importação (com comandos otimizados como **`COPY`**) e recriar os índices do zero posteriormente, em vez de deixar o SGBD atualizar os índices de forma incremental linha por linha. *(Fontes: "Database System Concepts"; "https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf")*
- **Preferir o comando COPY para importações em lote**: O comando **`COPY`** é altamente otimizado para inserção de dados em massa, superando largamente a performance de múltiplos comandos **`INSERT`** sequenciais. *(Fonte: "https://www.postgresql.org/files/documentation/pdf/18/postgresql-18-A4.pdf"*

- **Lição aprendida:** prompts que pedem estrutura explícita (categorias, tabelas, citação da fonte) geram respostas muito mais úteis e verificáveis do que perguntas abertas. Pedir a citação da fonte também ajuda a identificar quando a IA está “inferindo” além do que as fontes dizem.

### Rodada 3 — Testando profundidade técnica

**Prompt:** `"Explique como um índice do tipo B-Tree acelera uma cláusula WHERE, usando a explicação do 'Use The Index, Luke' como base. Dê um exemplo prático."`
- **Resposta obtida (resumo):**

A estrutura de um índice do tipo **B-Tree** (ou sua variação comum B+-Tree) é explicada conceitualmente no e-book *Use The Index, Luke* como uma das ferramentas de otimização de performance mais importantes para desenvolvedores1. Essa estrutura é composta por dois pilares fundamentais: a **árvore balanceada** e os **nós-folha organizados em uma lista duplamente encadeada**1.

A Estrutura da B-Tree

Fisicamente, o índice é estruturado em três níveis de páginas de dados: o **nó-raiz** (no topo), os **nós intermediários** e os **nós-folha** (na base)2. Toda a árvore é **balanceada**, o que significa que o caminho percorrido da raiz até qualquer um dos nós-folha tem exatamente o mesmo comprimento3.

Os nós-folha contêm as chaves ordenadas do índice acompanhadas de ponteiros que indicam a localização física das linhas correspondentes na tabela13. Por estarem ordenados na base, esses nós-folha são **interconectados de forma bidirecional como uma lista duplamente encadeada**1. Os nós intermediários e a raiz servem como um guia de navegação rápido para direcionar as pesquisas de cima para baixo3.

---

Como ela acelera a cláusula WHERE

A cláusula `WHERE` serve para filtrar os registros que satisfazem uma determinada condição booleana34. Em tabelas grandes sem índice, o banco de dados é obrigado a fazer uma **varredura sequencial completa** (Seq Scan), comparando linha por linha para encontrar os registros compatíveis, o que consome muito tempo e processamento35.

Com o índice B-Tree, esse comportamento muda drasticamente dependendo do operador no `WHERE`5:

1. **Buscas por Igualdade (ex: WHERE coluna = valor)**:
    - O SGBD inicia a pesquisa no nó-raiz e navega recursivamente para os níveis intermediários, comparando o valor buscado com as chaves de cada nó para decidir qual ramificação seguir. Ele desce até encontrar o nó-folha exato correspondente.
    - Essa busca reduz a complexidade de  para . Como os nós do índice são dimensionados para caber em blocos de disco (normalmente de 4 KB) e possuem um fator de ramificação ("fan-out") muito alto (podendo conter centenas de ponteiros por nó), a árvore é muito curta e larga. Mesmo em tabelas com milhões de registros, o SGBD precisa acessar apenas **3 ou 4 blocos de memória/disco** para encontrar a chave desejada.
2. **Buscas por Intervalo (ex: WHERE coluna > valor ou BETWEEN)**:
    - A B-Tree se destaca em consultas de intervalo precisamente devido à sua lista duplamente encadeada no nível folha.
    - Para processar o intervalo, o SGBD realiza uma única travessia vertical na árvore para localizar o nó-folha onde o limite inferior do intervalo se inicia.
    - Uma vez posicionado no nó-folha inicial, o banco de dados não precisa mais navegar pelos nós superiores da árvore; ele simplesmente utiliza a **lista duplamente encadeada para caminhar sequencialmente pelos nós-folha vizinhos**. Ele lê as chaves em ordem física até atingir o limite superior do intervalo.

---

Exemplo Prático

Considere uma tabela chamada `users` contendo **10 milhões de registros**5.

Caso 1: Filtro de Igualdade

```
SELECT * FROM users WHERE email = 'user@example.com';
```

- **Sem índice em email**: O banco de dados precisará varrer fisicamente as 10 milhões de linhas da tabela para garantir que encontrou todas as correspondências de `'user@example.com'`.
- **Com índice B-Tree em email**: O SGBD faz a busca vertical na B-Tree. Com um fator de ramificação típico, ele precisará ler apenas **3 ou 4 blocos de índice** para encontrar a folha e obter o ponteiro direto da linha correspondente. O tempo de resposta cai de segundos para poucos milissegundos.

Caso 2: Filtro de Intervalo

```
SELECT * FROM users WHERE created_at BETWEEN '2024-01-01' AND '2024-01-07';
```

- **Com índice B-Tree em created_at**: O SGBD faz uma busca vertical rápida para localizar o registro `'2024-01-01'` no nó-folha correspondente. A partir de lá, ele simplesmente **segue a lista duplamente encadeada de folhas**, lendo e retornando os registros em ordem cronológica de forma sequencial e contígua até alcançar o limite de `'2024-01-07'`. Ele ignora completamente as demais milhões de linhas que estão fora dessa janela temporal.

- **Dificuldade encontrada:** na primeira tentativa, a resposta trouxe um exemplo genérico que não batia exatamente com a fonte. Precisei pedir explicitamente: `"Baseie o exemplo apenas no capítulo 'The Anatomy of an Index' da fonte, sem adicionar informação externa."` Isso reduziu bastante a “alucinação”/generalização.

### Rodada 4 — Geração de material de revisão

**Prompt:** `"Crie um glossário com os 15 termos mais importantes sobre SQL e bancos de dados relacionais mencionados nas fontes, com definição de uma frase cada."`
- **Resposta obtida (resumo):** 

1. **SGBD (Sistema de Gerenciamento de Banco de Dados)**: É um **conjunto de programas de software** utilizados para definir, administrar, processar e proteger bancos de dados, atuando como uma interface direta entre o usuário (ou a aplicação) e as informações fisicamente armazenadas.
2. **SQL (Structured Query Language)**: É uma **linguagem de domínio específico** padronizada internacionalmente que é utilizada para realizar consultas, modificações, controle de acesso e definições de estruturas de dados em sistemas de bancos de dados relacionais.
3. **Banco de Dados**: Consiste em uma **coleção autodescritiva e organizada de registros integrados** e informações estruturadas que são projetados para serem consultados, atualizados e persistidos de maneira conveniente e eficiente.
4. **Relação (ou Tabela)**: É uma **matriz bidimensional** composta por linhas e colunas que armazena dados onde as células possuem valores exclusivos e nenhuma linha pode ser idêntica a outra.
5. **Tupla (ou Linha)**: Representa um **registro individual na tabela** que corresponde matematicamente a uma sequência ou lista de valores que descrevem um objeto conceitual ou físico específico.
6. **Atributo (ou Coluna)**: Representa uma **característica ou propriedade específica** do registro contido em uma tabela, possuindo sempre o mesmo significado e tipo de dado em todas as linhas daquela coluna.
7. **Esquema de Banco de Dados (Schema)**: Refere-se ao **projeto ou desenho lógico geral** que define as estruturas de armazenamento e os relacionamentos do banco de dados, funcionando de maneira análoga às declarações de variáveis em um programa.
8. **Instância de Banco de Dados**: É a **coleção de informações reais** armazenadas no banco de dados em um instante de tempo específico, funcionando como um "instantâneo" mutável do sistema que se altera à medida que as informações são inseridas ou removidas.
9. **Superchave (Superkey)**: É um **conjunto de um ou mais atributos** cujos valores, tomados coletivamente, garantem identificar cada tupla de uma relação de forma totalmente única.
10. **Chave Primária (Primary Key)**: É o **identificador único e obrigatório** de um registro na tabela, composto por uma superchave mínima cujos atributos devem ser sempre exclusivos e não nulos.
11. **Chave Estrangeira (Foreign Key)**: É uma **restrição de integridade referencial** que estabelece uma dependência entre duas tabelas, exigindo que o valor de um atributo em uma tabela referenciadora corresponda ao valor da chave primária de uma tabela referenciada.
12. **Metadados (Metadata)**: São os **dados que descrevem a estrutura e a organização** dos dados reais armazenados, sendo mantidos em uma área especial do sistema chamada dicionário de dados.
13. **Normalização (Normalization)**: É um **processo sistemático de modelagem de dados** que organiza tabelas e esquemas de relações por meio de "formas normais", com o objetivo de eliminar a redundância desnecessária de dados e evitar anomalias de modificação.
14. **Visão (View)**: É uma **relação virtual definida por uma consulta SQL** sobre tabelas reais, sendo útil para simplificar o acesso a dados de múltiplas tabelas e ocultar informações confidenciais de determinados usuários.
15. **Transação (Transaction)**: Refere-se a um **conjunto de operações que formam uma única unidade lógica de trabalho**, devendo ser executadas inteiramente com sucesso ou ser totalmente desfeitas para manter a integridade do banco de dados.

- **Observação:** o NotebookLM é bom em consolidar terminologia espalhada entre várias fontes diferentes — isso economizou bastante tempo comparado a eu mesmo garimpar os termos manualmente.

> 🔧 **Principais “cicatrizes” (lições de troubleshooting):**
1. Perguntas abertas demais → respostas rasas. Pedir estrutura (tabela, categorias, número de itens) melhora muito a qualidade.
2. Pedir explicitamente para citar a fonte ajuda a auditar se a resposta é fiel ao material ou está “preenchendo lacunas” com conhecimento geral do modelo.
3. Quando a resposta mistura conceitos de fontes diferentes de forma confusa, é melhor restringir o prompt a uma fonte específica por vez.
4. Reformular o prompt pedindo “sem adicionar informação externa às fontes” é útil para checar se um conceito está de fato bem coberto pelo material selecionado.
> 

---

## 🗂️ Miniguia de Estudo (Entrega Final)

### 1. Resumos Estruturados

#### O que é um Banco de Dados Relacional

Um banco de dados relacional organiza os dados em **tabelas** (linhas e colunas), onde cada tabela representa uma entidade (ex: `clientes`, `pedidos`, `produtos`). As relações entre tabelas são feitas por meio de **chaves primárias** (identificador único de cada registro) e **chaves estrangeiras** (referência à chave primária de outra tabela), garantindo integridade entre os dados.

#### As categorias da linguagem SQL

| Categoria | Sigla | Comandos principais | Função |
| --- | --- | --- | --- |
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
| --- | --- |
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

1. Acesse o NotebookLM e crie um novo notebook.
2. Adicione as fontes listadas na seção **Curadoria de Fontes** (upload de PDF ou link direto).
3. Use os **Prompts Reutilizáveis** acima, substituindo `[TEMA]`/`[CONCEITO]` pelo assunto desejado.
4. Documente as respostas e ajustes de prompt na seção de **Engenharia de Prompts**, seguindo o mesmo formato usado aqui.

---

## 📌 Sobre este projeto

Projeto desenvolvido como parte do desafio de prático da DIO sobre uso do NotebookLM como ferramenta de aprendizagem ativa.
