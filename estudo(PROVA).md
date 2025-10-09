# **[20280821]Introdução a Bancos de Dados Relacionais**


## 🧩 Entidade

- É algo que existe no mundo real e que você quer guardar informações no banco de dados.
👉 Pode ser uma pessoa, lugar, objeto ou evento.
Exemplos:

- Cliente, Produto, Pedido, Funcionário

- Cada entidade vira uma tabela no banco.


## 🔢 Atributo

- São as características ou informações da entidade.
👉 Cada atributo vira uma coluna da tabela.
Exemplos:

- Entidade Cliente → atributos: nome, idade, endereço

- Entidade Produto → atributos: nome, preço, quantidade


## 💡 Dica pra prova

- Entidade = o que quero representar.

- Atributo = o que sei sobre isso.

- Um registro (linha) é um exemplo real da entidade (ex: o cliente Maria).


---


# **[20250827]Modelagem Conceitual de Dados**

### 🧠 O que esse conteúdo ensina (resumo pra prova):


## 1. Modelagem Conceitual de Dados

É o passo inicial antes de criar o banco.
Mostra o que o sistema precisa armazenar e como tudo se relaciona, sem usar código.
👉 É o desenho da ideia do banco (conceito, entidades, atributos, relações).

## 2. Linguagens SQL (em teoria — só pra saber o papel de cada uma)

(sem precisar decorar sintaxe, só o que cada uma faz)

| Tipo    | Função principal                                                |
| ------- | --------------------------------------------------------------- |
| **DDL** | Cria e altera a estrutura do banco (tabelas, colunas etc.)      |
| **DML** | Manipula os dados (inserir, alterar, apagar)                    |
| **DQL** | Consulta os dados (buscar informações)                          |
| **DCL** | Controla acessos e permissões                                   |
| **TCL** | Garante que as operações sejam seguras e completas (transações) |


👉 Em resumo: DDL = estrutura, DML = dados, DQL = busca, DCL = permissões, TCL = segurança de transação.


## 3. IDEF0 (parte importante da modelagem de processos)

- É um modelo visual que mostra como o negócio funciona e como as atividades se conectam.
- Usa caixas e setas com 4 elementos chamados ICOM:

| Elemento                  | O que significa         | Exemplo                                |
| ------------------------- | ----------------------- | -------------------------------------- |
| **Input (Entrada)**       | O que entra no processo | Dados do cliente, catálogo de produtos |
| **Control (Controle)**    | Regras e normas         | Políticas de desconto, leis fiscais    |
| **Output (Saída)**        | O que sai do processo   | Relatórios, cupons gerados             |
| **Mechanism (Mecanismo)** | Quem ou o que executa   | Funcionários, sistemas, banco de dados |


 👉 **Em resumo: ** o IDEF0 serve pra entender e desenhar o funcionamento de um sistema ou empresa, antes de modelar os dados.


## 4. Decomposição Funcional (A-0, A0, A1...)

- A-0: visão geral do processo (ex: “Gerenciar Promoções e Cupons”).

- A0, A1, A2...: mostram as partes internas, cada uma com suas entradas, controles, saídas e mecanismos.

👉 É “abrir” o processo principal e ver o que acontece dentro.


## 5. O que você realmente precisa saber pra prova

- Saber o que é uma entidade e atributos.

- Entender como identificar entradas, saídas, controles e mecanismos em um texto ou caso real.

- Conseguir montar ou interpretar um diagrama IDEF0 simples.

- Saber pra que serve cada tipo de comando SQL (DDL, DML, DQL, DCL, TCL) — só o conceito.

- Saber explicar o processo (ex: “como a loja gera e aplica cupons”) de forma organizada.


---


# **[20250904]Modelagem Lógica de Dados**


## 🧩 1. O que é Modelagem Lógica

- É o passo entre o desenho conceitual e o banco real.
- Mostra entidades, atributos, chaves e relações, mas sem código SQL.

👉 Serve pra garantir que a estrutura dos dados faz sentido antes de criar o banco.


## 🧠 2. As 5 Visões RM-ODP (ISO/IEC 10746)

| Visão                               | Mostra                           | Exemplo                              |
| ----------------------------------- | -------------------------------- | ------------------------------------ |
| **1️⃣ Enterprise (Negócio)**        | Objetivos, atores, regras        | Loja quer aumentar vendas com cupons |
| **2️⃣ Informação (Dados)**          | Entidades, atributos, restrições | Cupom, Cliente, Pedido, Regras       |
| **3️⃣ Computacional (Serviços)**    | Como as partes se comunicam      | CouponService, OrderService          |
| **4️⃣ Engenharia (Infraestrutura)** | Como o sistema é distribuído     | API, Banco, Cache, Mensageria        |
| **5️⃣ Tecnológica (Ferramentas)**   | Tecnologias usadas               | PostgreSQL, Redis, Node.js, Docker   |


**📍 Essas 5 visões mostram o sistema do negócio até a tecnologia.**


## 📦 3. Entidades e Atributos

- Entidade → coisa que existe e precisa ser armazenada
###### Ex: Aluno, Livro, Autor, Empréstimo 

- Atributos → informações sobre a entidade
###### Ex: nome, RA, ISBN, título, data_retirada

#### 🧠 Dica: entidade = “o que”, atributo = “o que sei sobre isso”


## 🧱 4. MER e DER

| Tipo                                       | O que é                                                                       | O que mostra                                                                                 |
| ------------------------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **MER (Modelo Entidade-Relacionamento)**   | Modelo **conceitual** e **lógico**, usado para **pensar e definir o sistema** | **Entidades, atributos e relacionamentos** (sem se preocupar ainda com chaves técnicas)      |
| **DER (Diagrama Entidade-Relacionamento)** | **Representação visual e técnica** do MER (ou seja, o **desenho do modelo**)  | **PK (chaves primárias)**, **FK (chaves estrangeiras)** e **cardinalidades (1:1, 1:N, N:M)** |



**MER = ideia**
**DER = estrutura pronta pra virar banco**


## 🔑 5. Chaves

| Tipo                 | Função                               | Exemplo                           |
| -------------------- | ------------------------------------ | --------------------------------- |
| **PK (Primary Key)** | Identifica o registro de forma única | RA do aluno, ISBN do livro        |
| **FK (Foreign Key)** | Liga tabelas (referência)            | ISBN em EXEMPLAR aponta pra LIVRO |

###### 🧩 PK = identidade
###### 🔗 FK = ligação entre tabelas


## 🔢 6. Cardinalidades (Relações entre Entidades)
| Tipo    | Nome               | Exemplo                | Significado                    |
| ------- | ------------------ | ---------------------- | ------------------------------ |
| **1:1** | Um para um         | Funcionário ↔ Endereço | Cada um tem só um              |
| **1:N** | Um para muitos     | Livro ↔ Exemplares     | Um livro tem vários exemplares |
| **N:N** | Muitos para muitos | Livro ↔ Autor          | Vários livros ↔ vários autores |


**📍 Relação N:N precisa de tabela associativa, ex: LIVRO_AUTOR (ISBN, id_autor)**

###### 🚫 7. Por que não pode ter N:N direto

###### Quebra a 1ª Forma Normal (1FN).

###### Um campo não pode ter vários valores ao mesmo tempo.

###### A tabela associativa resolve isso e mantém a integridade.


## 📘 8. Exemplo: Biblioteca Universitária
| Entidade       | Atributos principais                 | Relacionamentos                 |
| -------------- | ------------------------------------ | ------------------------------- |
| **Aluno**      | RA, nome, curso, e-mail              | 1:N com Empréstimo              |
| **Livro**      | ISBN, título, ano                    | 1:N com Exemplar; N:N com Autor |
| **Autor**      | id_autor, nome, nacionalidade        | N:N com Livro                   |
| **Exemplar**   | id_exemplar, estado, disponibilidade | 1:N com Empréstimo              |
| **Empréstimo** | id_empréstimo, datas                 | liga Aluno e Exemplar           |


##### 📚 Regras:
- Um aluno pode fazer vários empréstimos.
- Um livro pode ter vários exemplares.
- Um exemplar só pode estar em um empréstimo por vez.
- Um livro pode ter vários autores.


## 🔍 9. Cardinalidades no Diagrama

![Cardinalidade ](https://ehgomes.com.br/wp-content/uploads/2023/08/cardinalidade-pe-de-galinha-no-modelo-de-dados-Crows-Foot.webp)

## 🧠 10. Dicas finais pra prova


✅ Identifique entidades e atributos lendo o texto do problema.
✅ Veja quais são as relações e se há N:N (crie associativa).
✅ Marque PK e FK certinho.
✅ Entenda o que cada visão (1 a 5) mostra.
✅ Lembre: MER → DER → Banco.
✅ Não precisa decorar código, só entender o modelo.


---


#  **[20250911]Normalização e Desnormalização usando DDL**


### 🧾 COLA DE PROVA — Normalização e Desnormalização (DDL)


## 🧱 1️⃣ O que é Normalização

#### Processo de organizar os dados em tabelas para:

- Evitar redundância (repetição);
- Garantir integridade;
- Facilitar manutenção e atualização.

##### 👉 Objetivo: cada dado aparece uma única vez e com significado claro.


## ⚙️ 2️⃣ Primeira Forma Normal (1FN)

#### Regra:

- Cada campo deve ter valores atômicos (não pode lista, vírgula, tabela dentro de tabela);
- Sem grupos repetitivos;
- Cada linha única (PK obrigatória).

###### 🧩 Exemplo: ``❌ Hobbies: "Futebol, Música, Leitura"``
###### ✅ Crie tabela ALUNOS, tabela HOBBIES e tabela ALUNO_HOBBY (N:N).
###### 📘 **Foco:** Quebra listas em linhas separadas.
###### 🔑 **Chave:** evita campos multivalorados.


## ⚙️ 3️⃣ Segunda Forma Normal (2FN)

#### Regras:

- Estar na 1FN;
- Nenhum atributo não-chave depende de parte da chave primária.

###### 📘 Foco: elimina dependência parcial (em chaves compostas).

##### 🧩 Exemplo:
Tabela ``PEDIDO_ITEM(pedido_id, produto_id, nome_cliente, nome_produto)``
→ nome_cliente depende de pedido
→ nome_produto depende de produto
###### ✅ Crie tabelas PEDIDOS, PRODUTOS e PEDIDO_ITEM (com FK).


## ⚙️ 4️⃣ Terceira Forma Normal (3FN)

#### Regras:

- Estar na 2FN;
- Nenhum atributo não-chave depende de outro atributo não-chave (dependência transitiva).

###### 📘 **Foco**: elimina dependência indireta.

##### 🧩 Exemplo:
Tabela ``FUNCIONARIOS(func_id, nome, departamento, gerente_departamento)``
→ gerente depende do departamento, não do func_id
###### ✅ Crie DEPARTAMENTOS(gerente_id) e FUNCIONARIOS(departamento_id).


## ⚙️ 5️⃣ Forma Normal de Boyce-Codd (BCNF)

#### Regras:

- Estar na 3FN;
- Toda determinante (lado esquerdo da dependência funcional) deve ser uma superchave.

###### 📘 **Foco**: casos onde há várias chaves candidatas.

##### 🧩 Exemplo:
PROFESSOR_DISCIPLINA(professor, disciplina, sala)
→ professor → sala e disciplina → sala
###### ✅ Crie PROFESSORES(sala), DISCIPLINAS(sala) e PROFESSOR_DISCIPLINA (relacionamento puro).


## 💡 6️⃣ Impactos da Normalização

#### ✅ Vantagens:

- Menos redundância;
- Atualizações seguras;
- Dados consistentes;
- Facilidade em manutenção.

#### ⚠️ Desvantagens:

- Muitos JOINs → consultas lentas;
- Complexidade em relatórios.


## 🔄 7️⃣ Desnormalização (Quando usar)

##### Usada de propósito para:

- Melhorar performance em leitura;
- Evitar JOINs complexos;
- Facilitar relatórios (ex: BI, Data Warehouse).

##### 🧩 Exemplo:
Criar ``VENDAS_RELATORIO(cliente_nome, produto_nome, valor_total)``
→ dados repetidos, mas leitura rápida.
###### ✅ Útil para relatórios, ⚠️ não para operação.

###### 📘 **Foco:** rapidez, não integridade.
###### 🔑 **Regra:** só em consultas, nunca na base principal.


## 🏭 8️⃣ Estudo de Caso: Fábrica de Concreto (“Concreto +”)
#### 🎯 Objetivo:

- Modelar um banco para uma fábrica de concreto que:
- Usa fornecedores e receitas técnicas;
- Registra lotes, funcionários, clientes e transportes;
- Precisa de normalização completa (1FN a BCNF);
- Mas também de tabela desnormalizada para relatórios.

### Etapas do Projeto:

| Etapa | O que fazer                             | Foco                                                            |
| ----- | --------------------------------------- | --------------------------------------------------------------- |
| 1️⃣   | Identificar entidades e relacionamentos | Fornecedores, Clientes, Receitas, Lotes, Funcionários, Veículos |
| 2️⃣   | Criar **DER conceitual**                | Desenho com cardinalidades                                      |
| 3️⃣   | Criar **modelo lógico**                 | Tabelas, atributos, tipos e restrições                          |
| 4️⃣   | **Implementar DDL**                     | Oracle SQL, PK, FK, CHECK, UNIQUE                               |
| 5️⃣   | **Desnormalizar** (bônus)               | Tabela para relatórios rápidos                                  |
| 6️⃣   | **Reflexão final**                      | Explicar decisões e impacto                                     |

#### 💡 O que o professor pode perguntar

- O que quebra a 1FN?
→ Valores multivalorados (vírgula, listas).

- Como resolver N:N?
→ Criando tabela associativa.

- Quando usar desnormalização?
→ Quando quer performance (relatórios, BI).

- O que é dependência parcial e transitiva?
→ Parcial = depende de parte da PK.
→ Transitiva = depende de outro atributo não-chave.

- Qual a diferença entre 3FN e BCNF?
→ BCNF é mais rigorosa, toda dependência precisa vir de uma chave.

- Por que normalizar?
→ Evita repetição, garante integridade e clareza.

- Por que desnormalizar?
→ Pra otimizar leitura, não estrutura.

### 🧱 Resumo dos Pilares

| Forma               | Corrige                  | Exemplo típico                   |
| ------------------- | ------------------------ | -------------------------------- |
| **1FN**             | Campos múltiplos         | “Hobbies: Futebol, Leitura”      |
| **2FN**             | Dependência parcial      | `nome_cliente` em chave composta |
| **3FN**             | Dependência transitiva   | `gerente_departamento`           |
| **BCNF**            | Multichaves com conflito | `professor-disciplina-sala`      |
| **Desnormalização** | Performance de leitura   | `Vendas_Relatorio`               |

#### 💬 Resumindo em uma frase:

Normalize para integridade, desnormalize para velocidade — mas só quando souber o que está fazendo. ⚖️


---


#  **[20250918]Data Manipulation Language**

### 🧾 COLA DE PROVA — DML (Data Manipulation Language)

### 🔹 O que é DML?
Conjunto de comandos SQL usados para manipular dados dentro das tabelas. (Não altera a estrutura, só o conteúdo)

### 🔹 Principais Comandos: 

| Comando    | Função                    | Conceito                                                |
| ---------- | ------------------------- | ------------------------------------------------------- |
| **INSERT** | Insere novos registros    | Adiciona linhas na tabela                               |
| **UPDATE** | Atualiza dados existentes | Altera valores com base em uma condição                 |
| **DELETE** | Remove registros          | Apaga linhas com base em uma condição                   |
| **MERGE**  | Atualiza **ou** insere    | Sincroniza tabelas (atualiza se existir, insere se não) |

### 🔹 DML x DDL:

| Tipo    | Ação             | Exemplos                      |
| ------- | ---------------- | ----------------------------- |
| **DML** | Manipula dados   | INSERT, UPDATE, DELETE, MERGE |
| **DDL** | Define estrutura | CREATE, ALTER, DROP           |

### 🔹 Conceitos importantes:

- Sempre usar WHERE no UPDATE e DELETE para não alterar tudo.
- COMMIT confirma as alterações.
- ROLLBACK desfaz alterações não confirmadas.
- MERGE combina INSERT + UPDATE automaticamente.

### 🧠 Resumo em uma frase

- DML manipula os dados da tabela;
- DDL define a estrutura dela.

---


# **[20250925]DQL - Relatórios Inteligentes**

### 🧾 COLA DE PROVA — DQL (SELECT e Relatórios)

### 🔹 O que é DQL

- DQL = Data Query Language → usada para consultar e gerar relatórios.
- Principal comando: SELECT
👉 Ele lê dados das tabelas (não altera nada).

### 🔹 O que o SELECT faz

Usado para buscar e organizar informações de uma ou mais tabelas.
Permite filtrar, ordenar e calcular dados.

### 🔹 Principais Palavras-Chave

| Palavra      | Função              | Exemplo conceitual        |
| ------------ | ------------------- | ------------------------- |
| **SELECT**   | escolhe colunas     | quais dados ver           |
| **FROM**     | define tabela       | de onde vem os dados      |
| **WHERE**    | filtra resultados   | “só categoria Acessórios” |
| **ORDER BY** | ordena resultados   | do maior pro menor        |
| **GROUP BY** | agrupa registros    | soma por vendedor         |
| **HAVING**   | filtra grupos       | grupos com soma > 1000    |
| **DISTINCT** | remove repetidos    | categorias únicas         |
| **LIKE**     | busca texto parcial | “contém Notebook”         |

### 🔹 Funções de Agregação (resumem valores)

| Função      | Serve para       |
| ----------- | ---------------- |
| **SUM()**   | somar valores    |
| **AVG()**   | média            |
| **MIN()**   | menor valor      |
| **MAX()**   | maior valor      |
| **COUNT()** | contar registros |

### 🔹 Exemplos de relatórios (em teoria)

- Ver todas as vendas → SELECT *
- Filtrar por categoria ou vendedor → WHERE
- Ordenar por valor → ORDER BY valor DESC
- Mostrar total de vendas → SUM(valor)
- Agrupar por vendedor → GROUP BY vendedor

### 🧠 Resumo rápido

DQL (SELECT) serve para consultar e gerar relatórios.
Usa filtros (WHERE), ordenações (ORDER BY) e funções (SUM, AVG, COUNT)
para transformar dados em informação.


---


# **[20251002]DQL - Selects robustos**

### 🧾 COLA DE PROVA — DQL Avançado (Subqueries)

### 🔹 O que é uma Subquery

- É uma consulta dentro de outra consulta (``SELECT`` dentro de outro ``SELECT``).
- Serve para buscar, comparar ou calcular informações que serão usadas pela consulta principal.
- Pode aparecer em:
	- **WHERE** → para comparar valores.
	- **FROM** → como “tabela virtual”.
	- **SELECT** → para mostrar cálculos junto dos dados.

### 🔹 Tipos e usos comuns

| Tipo                        | Função                       | Exemplo conceitual                       |
| --------------------------- | ---------------------------- | ---------------------------------------- |
| **Subquery simples**        | Calcula algo geral           | comparar com média geral                 |
| **Subquery correlacionada** | Depende da linha externa     | comparar dentro de cada grupo            |
| **Subquery no FROM**        | Cria tabela temporária       | ranking, soma por grupo                  |
| **Subquery no SELECT**      | Mostra valor calculado junto | exibir média geral ao lado de cada linha |

### 🔹 Para que serve (em teoria)

- Comparar dados com médias, mín/máx globais.
- Descobrir “maiores”, “menores” ou “acima da média”.
- Fazer relatórios inteligentes sem precisar várias tabelas.
- Criar rankings e estatísticas dentro de um único SELECT.

### 🔹 Diferença principal

- SELECT normal → busca dados diretos da tabela.
- SELECT com subquery → busca dados calculados ou comparados com base em outra consulta.

### 🔹 Palavras-chave importantes

- ``WHERE`` → filtrar com base em outra consulta
- ``IN``, ``>``, ``<``, = → comparar com resultado da subquery
- ``GROUP BY`` + ``HAVING`` → agrupar e filtrar grupos
- ``ROW_NUMBER()`` → gerar ranking por grupo

### 🧩 Resumindo tudo em 1 frase


Subquery é uma consulta dentro de outra, usada para comparar, agrupar ou gerar relatórios mais inteligentes a partir dos próprios dados.

