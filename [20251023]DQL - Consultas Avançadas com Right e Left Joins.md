## [20251023]DQL - Consultas Avançadas com Right e Left Joins


### 🧠 Exercício A:

```sql
SELECT
    c.nome AS cliente,
    v.produto
FROM CLIENTES c
LEFT JOIN VENDAS v
    ON c.id_cliente = v.id_cliente;
```

### 🧠 Exercício B:

```sql
SELECT
    v.produto,
    NVL(c.nome, 'Sem Cliente') AS cliente
FROM CLIENTES c
RIGHT JOIN VENDAS v
    ON c.id_cliente = v.id_cliente;
```

### 🧠 Exercício C:

```sql
SELECT
    c.nome,
    c.cidade
FROM CLIENTES c
LEFT JOIN VENDAS v
    ON c.id_cliente = v.id_cliente
WHERE v.id IS NULL;
```

### 🧠 Exercício D (Desafio):

```sql
SELECT
    c.cidade,
    NVL(SUM(v.valor), 0) AS total_vendas
FROM CLIENTES c
LEFT JOIN VENDAS v
    ON c.id_cliente = v.id_cliente
GROUP BY c.cidade
ORDER BY total_vendas DESC;
```