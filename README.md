# Exercício de Avaliação - SQL

TRIBUNAL DE CONTAS DO ESTADO DO ACRE - TCE-AC

FUNDAÇÃO PARQUE TECNOLÓGICO DA PARAÍBA - PAQTCPB

Treinamento em BI e Ciência de Dados

Módulo: Gestão de Dados Relacionais em Ciência de Dados

Exercício de Avaliação - SQL

**Aluno:** Emerson Freitas do Nascimento

## Criação da tabela venda

```sql
CREATE TABLE venda (
  codvenda INT PRIMARY KEY, 
  codcliente INT,
  codlivro INT,
  dataventa DATE,
  quantidade INT,
  valorpago DECIMAL(10,2),
  
  FOREIGN KEY (codcliente) REFERENCES cliente (idcliente),
  FOREIGN KEY (codlivro)  REFERENCES livro(codlivro),
);
```

## Dados das tabelas

- tabela autor:

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled.png)

- Tabela livro:

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%201.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%201.png)

- Tabela autorlivro:

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%202.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%202.png)

- Tabela cliente:

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%203.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%203.png)

- Tabela venda:

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%204.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%204.png)

## **Usando SQL, responda ao menos 10 das questões abaixo de 1 a 15.**

1. Quais os títulos dos livros da área 'Romance' publicados antes de 2010?

```sql
SELECT * FROM livro 
WHERE area = 'Romance' AND ano <= 2010;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%205.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%205.png)

2. Quais os nomes dos clientes que compraram o livro Cem Anos de Solidão

```sql
SELECT cliente.nome FROM cliente
INNER JOIN venda ON cliente.idcliente = venda.codcliente
WHERE venda.codlivro = 20;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%206.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%206.png)

3.  Quais os livros de autoria de Machado de Assis?

```sql
SELECT livro.titulo FROM livro
INNER JOIN autorlivro ON autorlivro.codlivro = livro.codlivro
INNER JOIN autor ON autor.codautor = autorlivro.codautor
WHERE autor.codautor = 1; -- código do autor Machado de Assis
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%207.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%207.png)

4. Qual o menor e maior preço de livros da área de Tecnologia?

```sql
SELECT MIN(preco) AS menor_preco, MAX(preco) AS maior_preco 
FROM livro
WHERE area = 'Tecnologia';
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%208.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%208.png)

5. Modifique o preço do livro 'Dom Casmurro' para 180 reais.

```sql
UPDATE livro 
SET preco = 180.00 
where codlivro = 10;
```

6. Remova o cliente 4000.

```sql
DELETE FROM cliente
WHERE idcliente = 4000;
```

7. Quais os títulos dos livros da área de Tecnologia?

```sql
SELECT titulo, area FROM livro
WHERE area = 'Tecnologia';
```

8. Qual a média de preços dos livros da editora 'Koogan'?

```sql
SELECT editora,  AVG(preco) AS media_preco 
FROM livro
WHERE editora = 'Koogan'
GROUP BY editora;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%209.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%209.png)

9. Quantos livros de Tecnologia há?

```sql
SELECT area, COUNT(codlivro) as quantidade_de_livros
from livro
WHERE area = 'Tecnologia'
GROUP BY area;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2010.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2010.png)

10. Quais os nomes dos autores do livro Banco de Dados?

```sql
SELECT autor.nome as autores_do_livro
from autor
INNER JOIN autorlivro on autorlivro.codautor = autor.codautor
INNER JOIN livro on livro.codlivro = autorlivro.codlivro
where livro.codlivro = 70; -- código do livro Banco de Dados
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2011.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2011.png)

11. Quais os nomes e endereços dos clientes de Xapuri?

```sql
select nome from cliente
where endereco LIKE '%Xapuri%';
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2012.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2012.png)

12. Quais livros possuem mais de 2 vendas?

```sql
SELECT livro.titulo
from livro
INNER JOIN venda on venda.codlivro = livro.codlivro
GROUP BY livro.titulo
HAVING COUNT(venda.codlivro) >= 2;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2013.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2013.png)

13. Quais livros nunca venderam?

```sql
SELECT livro.codlivro, livro.titulo
from livro
WHERE NOT EXISTS (
  SELECT * from venda WHERE venda.codlivro = livro.codlivro
);
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2014.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2014.png)

14. Quanto o cliente 3000 gastou em compra de livros?

```sql
SELECT cliente.nome, SUM(venda.valorpago) as valor_gasto_em_compras
FROM venda 
INNER JOIN cliente on cliente.idcliente = venda.codcliente
WHERE venda.codcliente = 3000
GROUP BY cliente.nome;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2015.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2015.png)

15. Quais os nomes dos clientes que estão sem endereço?

```sql
SELECT nome from cliente
WHERE endereco ISNULL;
```

Retorno: 

![Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2016.png](Exerci%CC%81cio%20de%20Avaliac%CC%A7a%CC%83o%20-%20SQL%202cfd60612d784134b7105c8affcf3a1a/Untitled%2016.png)