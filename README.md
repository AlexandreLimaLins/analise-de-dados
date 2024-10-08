
# Analise de dados em python/python data analysis

Um projeto de analise de dados para descobrir o motivo dos cancelamentos de uma empresa ficticia/a data analysis project to discover the reason for the cancellations of a fictitious company.


## Bibliotecas usadas/Libraries used

 - [Pandas](https://pandas.pydata.org/docs/)
 - [Plotly](https://plotly.com/python/)


## Uso/Usage

```python
# passo a passo
# pegar as bibliotecas
#!pip install pandas plotly
import pandas as pd
import plotly.express as px
# passo 1: importar a base de dados
tabela = pd.read_csv("cancelamentos.csv")
tabela = tabela.replace(1.0, 'cancelou')
tabela = tabela.replace(0.0, 'não cancelou')
display(tabela)

# Passo 2: Visualizar a base de dados
tabela = tabela.drop(columns="CustomerID")
display(tabela.info())
# se uma grande parcela da tabela for vazia use fillna para substituir os valores vazios pelo que mais se encaixa na situação

# passo 3: tratamento de dados - corrigir os valores vazios
tabela =  tabela.dropna()

# passo 4: analise inicial dos cancelamentos
display(tabela["cancelou"].value_counts())
# value_counts connta os valores da base de dados dado a ele

# em porcentagem
# display(tabela["cancelou"].value_counts(normalize=True))
# normalize normaliza o resultado em porcentagem
# display(tabela["cancelou"].value_counts(normalize=True)).map("{:.1%}".format)
# map formata utilizando ":" pra falar que é numero, "." pra falar que é decimal e "1" pra falar o numero de casas decimais

# passo 5: analise das causas de cancelamento dos clientes

# crie o grafico
for coluna in tabela.columns:
    grafico = px.histogram (tabela, x=coluna, color="cancelou", text_auto=True)
# mostrar o grafico
    grafico.show()
```
## Screenshots

![image](https://github.com/user-attachments/assets/63b984e7-300d-45a4-854d-13641a2d933d)


![image](https://github.com/user-attachments/assets/7f6a3c8f-2170-43ea-897c-e347b7ced829)


![image](https://github.com/user-attachments/assets/7bf35368-8e30-40e3-98bd-3307d5277226)


![image](https://github.com/user-attachments/assets/3bbd9323-c99a-4d63-b49c-ae49a79a6101)

