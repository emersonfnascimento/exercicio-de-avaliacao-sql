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

| codautor | nome                |
| -------- | ------------------- |
| 1        | Machado de Assis    |
| 2        | Gabriel G. Marquez  |
| 3        | Leon Tostoi         |
| 4        | Elizabeth Rudnick   |
| 5        | Foster Provost      |
| 6        | Tom Fawcett         |
| 7        | Ramesh Sharda       |
| 8        | Efraim Turban       |
| 9        | Ramez Elmasri       |
| 10       | Shamkant B. Navathe |
| 11       | John E. Hall        |

<hr>
<br>

- Tabela livro:

| codlivro | titulo              | ano  | editora     | area       | preco  |
| -------- | ------------------- | ---- | ----------- | ---------- | ------ |
| 10       | Dom Casmurro        | 2019 | Principis   | Romance    | 180.00 |
| 20       | Cem Anos de Solidao | 2018 | Record      | Romance    | 120.00 |
| 30       | Anna Karienina      | 1877 | Livro e Cia | Romance    | 250.00 |
| 40       | O Rei Leao          | 1995 | Livro e Cia | Infantil   | 35.00  |
| 50       | Data science        | 2016 | Atlas       | Tecnologia | 135.00 |
| 60       | BI                  | 2019 | Atlas       | Tecnologia | 138.00 |
| 70       | Banco de Dados      | 2010 | Pearson     | Tecnologia | 220.00 |
| 80       | Fisiologia          | 2016 | Koogan      | Medicina   | 540.00 |
| 90       | Anatomia            | 2014 | Koogan      | Medicina   | 500.00 |
| 100      | Histologia Basica   | 2015 | Koogan      | Medicina   | 387.00 |
| 110      | Enxaqueca           | 2019 | Koogan      | Medicina   | 57.00  |

<hr>
<br>

- Tabela autorlivro:

| codautor | codlivro |
| -------- | -------- |
| 1        | 10       |
| 2        | 20       |
| 3        | 30       |
| 4        | 40       |
| 5        | 50       |
| 6        | 50       |
| 7        | 60       |
| 8        | 60       |
| 9        | 70       |
| 10       | 70       |
| 11       | 80       |
| 11       | 90       |
| 11       | 100      |
| 11       | 110      |

<hr>
<br>

- Tabela cliente:

| idcliente | nome             | endereco                             |
| --------- | ---------------- | ------------------------------------ |
| 1000      | Joao Oliveira    | Projetada, 22, Rio Branco-AC         |
| 2000      | Maria da Paz     | Rua do Maracatu, 23, Rio Branco-AC   |
| 3000      | Jose Bonifacio   | Av. Conselheiro Aguiar,10, Xapuri-AC |
| 5000      | Francisco Dantas | null                                 |

<hr>
<br>

- Tabela venda:

| codvenda | codcliente | codlivro | dataventa                | quantidade | valorpago |
| -------- | ---------- | -------- | ------------------------ | ---------- | --------- |
| 1001     | 1000       | 10       | 2021-01-10T00:00:00.000Z | 1          | 150.00    |
| 1002     | 1000       | 20       | 2020-04-08T00:00:00.000Z | 2          | 240.00    |
| 1003     | 2000       | 30       | 2019-04-18T00:00:00.000Z | 2          | 500.00    |
| 1004     | 3000       | 80       | 2020-02-12T00:00:00.000Z | 1          | 540.00    |
| 1005     | 3000       | 90       | 2019-10-10T00:00:00.000Z | 1          | 500.00    |
| 1006     | 3000       | 10       | 2019-10-23T00:00:00.000Z | 1          | 150.00    |

<hr>
<br>

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
