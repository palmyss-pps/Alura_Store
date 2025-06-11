# Análise de Vendas das Lojas - Challenge Data Science Alura

## 📋 Sobre o Projeto

Este projeto tem como objetivo analisar dados de vendas de quatro lojas diferentes para auxiliar na decisão estratégica sobre qual loja deve ser vendida. A análise considera faturamento, vendas por categoria, avaliação dos clientes, produtos mais e menos vendidos, custo médio do frete e análise geográfica das vendas.

## 📂 Importação dos Dados

Os dados são importados diretamente de arquivos CSV hospedados no GitHub:

```python
import pandas as pd

url1 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_1.csv"
url2 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_2.csv"
url3 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_3.csv"
url4 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_4.csv"

loja1 = pd.read_csv(url1)
loja2 = pd.read_csv(url2)
loja3 = pd.read_csv(url3)
loja4 = pd.read_csv(url4)

\'''python

# 📊 Etapas da Análise
Análise do Faturamento
Cálculo do faturamento total por loja.
Soma dos preços das vendas para cada loja.

Vendas por Categoria
Agrupamento e soma das vendas por categoria de produto para cada loja.

Média de Avaliação das Lojas
Cálculo da média das avaliações dadas pelos clientes em cada loja.

Produtos Mais e Menos Vendidos
Identificação dos 5 produtos que geraram maior receita e dos 5 que geraram menor receita em cada loja.

Frete Médio por Loja
Cálculo do custo médio do frete por loja.

Visualizações

Gráficos de barras, linhas e pizza para mostrar receita total, média e participação de cada loja.

Gráfico de dispersão entre preço e frete para cada loja, com possibilidade de escolher a loja a analisar.

Análise Geográfica
Visualização da distribuição geográfica das vendas com latitude e longitude, destacando cada loja.

🛠 Tecnologias Utilizadas
Python 3.x

Pandas

Matplotlib

Seaborn

CSV / URL Reading

💡 Resultados e Insights
Faturamento Total: Loja 1 tem o maior faturamento; Loja 4, o menor.

Vendas por Categoria: Eletrônicos e eletrodomésticos são as categorias principais.

Avaliação Média: Loja 3 possui a melhor avaliação; Loja 1, a pior.

Produtos Mais Vendidos: TVs, geladeiras e celulares lideram as vendas.

Custo do Frete: Loja 4 tem o menor custo médio de frete.

Análise Geográfica: Distribuição dos clientes por localização mostra diferenças nas áreas atendidas pelas lojas.

📈 Recomendação Estratégica
Com base nos dados, a recomendação é vender a Loja 4, pois:

Apresenta o menor faturamento.

Tem avaliação média e desempenho abaixo das outras.

Embora tenha o menor custo de frete, isso não se traduz em melhores resultados financeiros.

📥 Como Rodar o Projeto
Clone o repositório.

Instale as dependências:

bash
Copiar
Editar
pip install pandas matplotlib seaborn
Execute os scripts para importar os dados e rodar as análises.

Utilize as funções interativas para explorar vendas por loja e visualizar gráficos.

📄 Exemplo de Uso
python
Copiar
Editar
from urllib.request import urlopen
import csv

urls = [url1, url2, url3, url4]

def ler_csv(url):
    dados = []
    with urlopen(url) as resposta:
        linhas = resposta.read().decode('utf-8').splitlines()
        leitor = csv.DictReader(linhas)
        for linha in leitor:
            dados.append(linha)
    return dados

faturamento_total = 0
for i, url in enumerate(urls):
    dados_loja = ler_csv(url)
    faturamento_loja = sum(float(venda['Preço']) for venda in dados_loja)
    print(f"Faturamento Loja {i+1}: R$ {faturamento_loja:.2f}")
    faturamento_total += faturamento_loja

print(f"\nFaturamento total de todas as lojas: R$ {faturamento_total:.2f}")
