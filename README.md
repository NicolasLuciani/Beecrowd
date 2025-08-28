# Atividade Beecrowd
---
## Niveis:
- Nível 1
  - Endereço dos Clientes
  - Cidades em Ordem Alfabética
  - Expandindo o Negocio
  - Maior e Menor Preço
 
- Nível 2
  - Menores que 10 ou Maiores que 100
  - Filmes em Promoção

- Nível 3
  - Categorias
  - Produtos Importados

- Nível 4
  - Filmes de Ação
 
- Nível 5
  - Locações de Setembro

 ---
# Nivel 1:
- Endereço de imagens:<br>
O seu trabalho é nos passar os nomes e os endereços dos clientes que moram em 'Porto Alegre', para entregar os convites pessoalmente.
```sql
SELECT
    name,
    street
FROM
    customers
WHERE
    city = 'Porto Alegre';
```

- Cidades em Ordem Alfabética:<br>
Todos os meses a empresa pede um relatório das cidades que os fornecedores estão cadastrados. Dessa vez não vai ser diferente, faça uma consulta no Banco de Dados que retorne todas as cidades dos fornecedores, mas em ordem alfabética.
```sql
SELECT
    city
FROM
    providers
ORDER BY
    city ASC;
```

- Expandindo o Negocio:<br>
O seu trabalho é nos passar os nomes e os endereços dos clientes que moram em 'Porto Alegre', para entregar os convites pessoalmente.
```sql
SELECT
    name,
    street
FROM
    customers
WHERE
    city = 'Porto Alegre';
```

- 	Maior e Menor Preço:<br>
O setor financeiro da nossa empresa, está querendo saber os menores e maiores valores dos produtos, que vendemos.
Para isso exiba somente o maior e o menor preço da tabela produtos.
```sql
SELECT
    max(price),
    min(price)
FROM
    Products
```

---
# Nível 2

- Menores que 10 ou Maiores que 100:<br>
O setor financeiro da empresa precisa de um relatório que mostre o código e o nome dos produtos cujo preço são menores que 10 ou maiores que 100.
```sql
SELECT
		id, 
		name
FROM
		products
WHERE
		price < 10
		OR price > 100;
```

- Filmes em Promoção:<br>
Antigamente a locadora fez um evento em que vários filmes estavam em promoção, queremos saber que filmes eram esses. Seu trabalho para nós ajudar é selecionar o ID e o nome dos filmes cujo preço for menor que 2.00.
```sql
SELECT
    m.id,
    m.name
    
FROM
    movies as m
    
JOIN
    prices as p 
        ON 
            m.id_prices = p.id
            
WHERE
    p.value < 2.00;
```

---
# Nível 3

- Categorias:<br>
Quando os dados foram migrados de Banco de Dados, houve um pequeno mal-entendido por parte do antigo DBA. Seu chefe precisa que você exiba o código e o nome dos produtos, cuja categoria inicie com 'super'.
```sql
SELECT 
    P.id AS ID, 
    P.name AS nome 
FROM 
    products AS P 
JOIN
    categories AS C ON P.id_categories = C.id
WHERE 
    C.name LIKE 'super%';
```

- Produtos Importados:<br>
O setor de importação da nossa empresa precisa de um relatório sobre a importação de produtos do nosso fornecedor Sansul. Sua tarefa é exibir o nome dos produtos, o nome do fornecedor e o nome da categoria, para os produtos fornecidos pelo fornecedor ‘Sansul SA’ e cujo nome da categoria seja 'Imported'.
```sql
SELECT
    prd.name AS product,
    prv.name AS provider,
    c.name AS category
FROM
    products AS prd
JOIN
    providers AS prv 
		    ON 
				    prd.id_providers = prv.id
JOIN
    categories AS c 
		    ON 
				    prd.id_categories = c.id
WHERE
    prv.name = 'Sansul SA'
    AND c.name = 'Imported';
```
---
# Nível 4

- Filmes de Ação:<br>
Uma Vídeo locadora contratou seus serviços para catalogar os filmes dela. Eles precisam que você selecione o código e o nome dos filmes cuja descrição do gênero seja 'Action'.
```sql
SELECT
    m.id,
    m.name
    
FROM
    movies AS m
    
JOIN
    genres AS g 
        ON 
            m.id_genres = g.id
WHERE
    g.description = 'Action';
```
---

# Nível 5 

- Locações de Setembro:<br>
A vídeo locadora está fazendo seu relatório semestral e precisa da sua ajuda. Basta você selecionar o nome dos clientes e a data de locação, das locações realizadas no mês de setembro de 2016.
```sql
SELECT
    C.name AS Nome
FROM
    customers AS C
JOIN
    rentals AS R ON R.id_customers = C.id

WHERE 
    EXTRACT (MONTH FROM R.rentals_date) = 9
    AND EXTRACT (YEAR FROM R.rentals_date) = 2016;
```
