### Exercício A

```sql
SELECT PRODUTO, CATEGORIA, VALOR
FROM VENDAS
WHERE VALOR > (
    SELECT MIN(VALOR)
    FROM VENDAS
    WHERE CATEGORIA = 'Eletrônicos'
)
ORDER BY VALOR DESC;
```

## Exercício B

```sql
SELECT VENDEDOR, PRODUTO, VALOR
FROM VENDAS
WHERE VALOR = (
    SELECT MAX(VALOR)
    FROM VENDAS
);
```

## Exercício C

```sql
SELECT DISTINCT CATEGORIA
FROM VENDAS
WHERE VALOR > (SELECT AVG(VALOR) FROM VENDAS);
```

## Exercício D (Desafio)

```sql
SELECT vendedor, produto, valor
FROM (
    SELECT 
        vendedor,
        produto,
        valor,
        ROW_NUMBER() OVER (PARTITION BY vendedor ORDER BY valor DESC) AS posicao
    FROM VENDAS
) ranked
WHERE posicao <= 3
ORDER BY vendedor, valor DESC;
```