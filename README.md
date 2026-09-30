# 🛒 Vamos Encher o Carrinho!

Análise exploratória de dados do **Instacart**, plataforma de entrega de supermercado, com foco em entender o comportamento de compra dos clientes, os produtos mais recorrentes e os padrões de recompra.

O projeto realiza **leitura, preparação, tratamento de dados e análise exploratória (AED/EDA)** sobre pedidos, produtos e itens adicionados aos carrinhos, transformando os dados brutos em insights sobre comportamento de consumo.

---

## 🎯 Objetivos do Projeto

O projeto busca responder perguntas de negócio relacionadas a:

- comportamento dos clientes ao longo do dia e da semana;
- intervalo entre pedidos;
- quantidade de pedidos por cliente;
- quantidade de itens por pedido;
- produtos mais populares;
- produtos mais incluídos em pedidos repetidos;
- proporção de recompra por produto e por cliente;
- produtos adicionados primeiro ao carrinho.

A análise foi construída sobre cinco tabelas relacionadas do conjunto de dados do Instacart.

---

## 🔎 Abordagem / Arquitetura Técnica

O notebook está organizado em três etapas principais:

### 1. Visão geral dos dados

Os cinco arquivos `.csv` são carregados com **Pandas**, utilizando `;` como separador:

- `instacart_orders.csv` — informações dos pedidos e clientes;
- `products.csv` — catálogo de produtos;
- `order_products.csv` — produtos associados a cada pedido;
- `aisles.csv` — categorias de corredores;
- `departments.csv` — categorias de departamentos.

Também são verificadas as estruturas, tipos de dados e a existência de valores ausentes.

### 2. Preparação dos dados

Foram realizadas verificações de:

- duplicidades de linhas;
- duplicidades de identificadores;
- nomes de produtos repetidos;
- valores ausentes;
- consistência dos dados.

Entre os tratamentos realizados:

- remoção das linhas duplicadas de `orders`;
- preenchimento dos nomes de produtos ausentes com `Unknown`;
- investigação dos valores ausentes em `days_since_prior_order`;
- tratamento dos valores ausentes de `add_to_cart_order`, substituindo-os por `999` e convertendo a coluna para inteiro;
- padronização dos nomes de produtos para letras minúsculas durante a análise de duplicidades.

Um ponto importante identificado foi que os **1.258 nomes de produtos ausentes** estão associados ao `aisle_id = 100` e ao `department_id = 21`.

Também foram encontrados **15 registros duplicados em `instacart_orders`**, concentrados em pedidos realizados na quarta-feira às 2h da manhã. Esses registros foram removidos.

### 3. Análise exploratória

A etapa analítica utiliza agrupamentos, filtros, junções, medidas de frequência e visualizações para investigar os padrões de compra.

Entre as principais análises estão:

- clientes por hora do dia;
- clientes por dia da semana;
- distribuição do tempo entre pedidos;
- comparação de pedidos por hora entre quartas-feiras e sábados;
- distribuição da quantidade de pedidos por cliente;
- ranking dos 20 produtos mais populares;
- distribuição de itens por pedido;
- ranking dos 20 produtos mais presentes em pedidos repetidos;
- proporção de pedidos repetidos por produto;
- proporção de pedidos repetidos por cliente;
- ranking dos 20 produtos adicionados primeiro ao carrinho.

---

## 🧰 Stack Tecnológica

| Tecnologia | Utilização |
|---|---|
| 🐍 **Python** | Linguagem utilizada no projeto |
| 🐼 **Pandas** | Leitura, tratamento, transformação, agrupamento e análise dos dados |
| 📊 **Matplotlib** | Construção das visualizações e gráficos |
| 📓 **Jupyter Notebook** | Desenvolvimento, documentação e execução da análise |
| 🗃️ **CSV** | Formato dos conjuntos de dados utilizados |

---

## 📁 Estrutura do Repositório

```text
instacart_entregas/
│
├── datasets/
│   ├── aisles.csv
│   ├── departments.csv
│   ├── instacart_orders.csv
│   ├── order_products.csv
│   └── products.csv
│
├── notebooks/
│   └── notebook.ipynb
│
├── README.md
└── requirements.txt
```

### Organização

- `datasets/` → contém os cinco conjuntos de dados utilizados na análise.
- `notebooks/` → contém o Jupyter Notebook com todo o processo de exploração, tratamento e análise.
- `README.md` → documentação e apresentação do projeto.
- `requirements.txt` → arquivo destinado às dependências necessárias para reprodução do projeto.

---

## ⚙️ Instalação e Execução

### 1. Clone o repositório

```bash
git clone https://github.com/alexpereira951/instacart_entregas
cd instacart_entregas
```

### 2. Crie e ative um ambiente virtual

#### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

#### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

As bibliotecas utilizadas diretamente no notebook são **Pandas** e **Matplotlib**.

Caso seja necessário preparar o ambiente manualmente:

```bash
pip install pandas matplotlib jupyter
```

### 4. Execute o notebook

```bash
jupyter notebook
```

Depois, abra:

```text
notebooks/notebook.ipynb
```

> O notebook utiliza caminhos relativos para acessar os arquivos da pasta `datasets/`. Por isso, mantenha a estrutura do repositório conforme apresentada acima.

---

## 📊 Principais Resultados

A análise identificou padrões relevantes no comportamento de compra.

### ⏰ Horários de compra

Os pedidos se concentram principalmente durante o período diurno, com destaque para a faixa entre aproximadamente **8h e 20h**. A análise por hora também identificou picos de atividade próximos das **11h e 15h**.

### 📅 Dias da semana

**Domingo e segunda-feira** aparecem como os dias com maior quantidade de clientes realizando pedidos na análise.

### 🔁 Intervalo entre pedidos

A distribuição de `days_since_prior_order` mostra uma concentração relevante de clientes realizando um novo pedido após aproximadamente **6 a 8 dias**.

### 🛍️ Quantidade de itens por pedido

A quantidade mais frequente identificada foi de **5 itens por pedido**, enquanto a maior parte dos pedidos analisados possui até aproximadamente **15 itens**.

### 👤 Pedidos por cliente

A maioria dos clientes realiza poucos pedidos no período analisado. A moda da distribuição ficou em aproximadamente **3 pedidos por cliente**, e grande parte dos clientes realizou até **5 pedidos**.

### 🥦 Produtos populares e recompra

Entre os produtos que aparecem com destaque nas análises de popularidade e recompra estão itens como:

- bananas;
- morangos;
- espinafre orgânico;
- abacates;
- limões;
- leite integral orgânico;
- framboesas;
- cebola e alho;
- abobrinha;
- mirtilos;
- maçãs;
- tomates-cereja orgânicos.

A análise também calculou a proporção de recompra por produto e por cliente. Para os clientes, a moda observada na distribuição ficou entre **50% e 60%**.

### 🛒 Ordem de adição ao carrinho

Também foram identificados os **20 produtos mais frequentemente adicionados como primeiro item do carrinho**, permitindo observar quais produtos tendem a iniciar uma jornada de compra.

---

## ⚠️ Limitações

O projeto apresenta algumas limitações que devem ser consideradas na interpretação dos resultados:

* **Dados históricos e amostrais:** os resultados refletem exclusivamente o conjunto de dados disponibilizado, não representando necessariamente o comportamento atual de todos os clientes da plataforma.
* **Valores ausentes:** alguns registros apresentam informações ausentes, especialmente em variáveis relacionadas aos pedidos e aos produtos, o que pode limitar determinadas análises.
* **Ausência de modelagem preditiva:** o projeto está concentrado em **análise exploratória e descritiva**, não sendo desenvolvido um modelo para previsão de compras, recompra ou comportamento futuro dos clientes.
* **Análise sem causalidade:** os padrões identificados mostram associações e distribuições nos dados, mas não permitem concluir que determinado fator seja a causa direta de um comportamento de compra.

Os resultados devem, portanto, ser interpretados dentro do contexto do conjunto de dados, dos tratamentos realizados e do escopo exploratório definido para o projeto.


## 💡 Insights de Negócio

Os resultados permitem explorar algumas hipóteses de negócio:

- **Fidelização:** a presença significativa de pedidos repetidos evidencia um comportamento de recompra relevante no conjunto analisado.
- **Produtos recorrentes:** itens de consumo cotidiano aparecem com frequência nos rankings de popularidade e recompra.
- **Comportamento temporal:** os padrões de horário e dia da semana podem apoiar análises futuras de campanhas e operações.
- **Produtos âncora:** os itens frequentemente presentes em pedidos repetidos ou adicionados primeiro ao carrinho podem ser analisados como potenciais produtos de entrada para estratégias comerciais.
- **Segmentação:** a proporção de recompra por cliente permite criar análises futuras de perfis de comportamento.

> Os insights acima são interpretações derivadas das análises realizadas no notebook; não representam um modelo preditivo nem uma estimativa causal.

---

## 📌 Conclusão

O projeto demonstra um fluxo completo de **análise exploratória de dados**, partindo de arquivos CSV brutos, passando por validação, tratamento de inconsistências e transformação dos dados, até chegar à geração de indicadores e visualizações.

O principal resultado é a construção de uma visão estruturada sobre **quando os clientes compram, quantos itens levam, quais produtos são mais recorrentes e como o comportamento de recompra se distribui entre produtos e clientes**.

Esse processo também estabelece uma base para etapas futuras, como **segmentação de clientes, análise de coocorrência de produtos, previsão de recompra e desenvolvimento de estratégias de recomendação**.

---

## 📚 Dados

O conjunto de dados utilizado é uma versão modificada do dataset de pedidos da **Instacart**, disponibilizada no contexto do projeto de análise. Os arquivos presentes neste repositório são:

```text
aisles.csv
departments.csv
instacart_orders.csv
order_products.csv
products.csv
```

---

## 👨‍💻 Projeto

Projeto desenvolvido como estudo prático de **Análise de Dados com Python**, com foco em preparação de dados, análise exploratória e geração de insights de negócio.
