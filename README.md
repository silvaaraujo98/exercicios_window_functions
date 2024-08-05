Claro! Aqui está o README em português:

---

# Consultas SQL e Análise com SQLite e Pandas

Este repositório contém um Jupyter Notebook onde eu faço as questões de window functions que criei com o gpt, caso queira ver essa resolução em formato de artigo no medium segue o link [Artigo do Medium](https://medium.com/@jvsilvaaraujo98/exerc%C3%ADcios-de-window-functions-para-iniciantes-no-sqlite-5fe5e700e489)

## Índice

- [Introdução](#introdução)
- [Configuração](#configuração)
- [Uso](#uso)
- [Consultas Incluídas](#consultas-incluídas)
- [Contribuindo](#contribuindo)

## Introdução

Este notebook tem como objetivo fornecer uma abordagem prática para entender e utilizar funções de janela SQL além de conectar um banco de dados através de um notebook jupyter.

## Configuração

Para executar este notebook, você precisará ter os seguintes itens instalados:

- Python 3.x
- Jupyter Notebook
- SQLite
- Pandas

Você pode instalar os pacotes Python necessários usando pip:

```bash
pip install pandas sqlite3
```

## Uso

1. Clone o repositório:

```bash
git clone <url_do_repositório>
cd <diretório_do_repositório>
```

2. Abra o Jupyter Notebook:

```bash
jupyter notebook codigo_com_consultas.ipynb
```

3. Execute as células no notebook para ver as consultas e seus resultados.

## Consultas Incluídas

O notebook inclui os seguintes tipos de consultas:

1. **Criando uma Conexão**: Estabeleça uma conexão com o banco de dados SQLite.
   ```python
   conn = create_connection('extra_practice_database.db')
   ```

2. **Executando Consultas**: Execute consultas SQL e exiba os resultados usando Pandas.
   ```python
   execute_query(conn, query)
   ```

3. **Consultas de Exemplo**:
   - **Gasto Total por Cliente**: Liste todos os clientes junto com seu gasto acumulado total.
     ```sql
     WITH venda_acumulada_por_customerid AS (
         SELECT customerid, Sum(total) OVER (PARTITION BY customerid) AS total_acumulado
         FROM invoice
     )
     SELECT b.firstname || ' ' || b.lastname AS nome, a.total_acumulado
     FROM venda_acumulada_por_customerid a
     JOIN customers b ON a.customerid = b.customerid
     ```
   - **Outras Consultas Analíticas**: Consultas adicionais demonstrando o uso de funções de janela e outras técnicas SQL.

## Contribuindo

Contribuições são bem-vindas! Por favor, faça um fork do repositório e envie um pull request com suas melhorias.
