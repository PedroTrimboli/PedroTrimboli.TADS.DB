## [20251016]DQL - Consultas Avançadas com Inner Join


### 🧠 Exercício A:

```sql
SELECT
    c.nome AS cliente,
    v.produto AS produto,
    c.cidade AS cidade
FROM VENDAS v
INNER JOIN CLIENTES c
    ON c.id_cliente = v.id_cliente
ORDER BY c.nome, v.produto;
```

### 🧠 Exercício B:

```sql
SELECT
    c.estado AS estado,
    SUM(v.valor) AS total_vendas
FROM VENDAS v
INNER JOIN CLIENTES c
    ON c.id_cliente = v.id_cliente
GROUP BY c.estado
ORDER BY total_vendas DESC;
```

### 🧠 Exercício C:

```sql
SELECT
    c.cidade AS cidade,
    SUM(v.valor) AS total_vendas
FROM VENDAS v
INNER JOIN CLIENTES c
    ON c.id_cliente = v.id_cliente
GROUP BY c.cidade
HAVING SUM(v.valor) > 2000
ORDER BY total_vendas DESC;
```

### 🧠 Exercício D (Desafio):

```sql
SELECT
    cliente,
    categoria,
    total_categoria
FROM (
    SELECT
        c.id_cliente,
        c.nome AS cliente,
        v.categoria,
        SUM(v.valor) AS total_categoria,
        RANK() OVER (
            PARTITION BY c.id_cliente
            ORDER BY SUM(v.valor) DESC
        ) AS rk
    FROM VENDAS v
    INNER JOIN CLIENTES c
        ON v.id_cliente = c.id_cliente
    GROUP BY c.id_cliente, c.nome, v.categoria
)
WHERE rk = 1
ORDER BY cliente, categoria;
```