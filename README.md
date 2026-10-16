# Classificação Linear – Produção de Energia Renovável

Challenge acadêmico de Machine Learning: análise de correlação e classificação da classe de produção de energia (`Low`, `Medium`, `High`) com um modelo linear do scikit-learn.

## Integrantes

- Vitor Nascimento RM: 571873

- Nickollas Korner RM: 569655

- João Pedro Ferrari RM: 573037

- Lucca Bracco RM: 570175

- Pierre Biason RM: 569718

- Lucas Santana RM: 573197
## Dataset

[Renewable Energy Production Dataset (2010-2020)](https://www.kaggle.com/datasets/itsrohithere/renewable-energy-production-dataset-2010-2020), do Kaggle. São 1.000 registros com variáveis climáticas (temperatura, vento, radiação solar, chuva), região, fonte de energia, estação, eficiência e produção defasada. O target é `Energy_Class`.

## Arquivos

| Arquivo | Descrição |
|---|---|
| `challenge_energia_renovavel.py` | Código completo, organizado em células `# %%` |
| `challenge_energia_renovavel.ipynb` | Mesmo código em formato notebook, para o Google Colab |
| `Renewable_Energy_Data.csv` | Base de dados utilizada |

## O que foi feito

1. **Análise do dataset:** carregamento dos dados, encoding ordinal do target (Low=0, Medium=1, High=2), matriz de correlação de todas as colunas (com one-hot nas categóricas) e seleção de features a partir dela.
2. **Modelo:** `LogisticRegression` com `StandardScaler`, um classificador linear cuja fronteira de decisão é um hiperplano. O modelo foi treinado em dois cenários, com 40% e com 15% dos dados separados para teste.
3. **Avaliação:** matriz de confusão, acurácia, precisão e recall de cada cenário, além de uma comparação entre os tamanhos de test set.

## Principais resultados

- `Efficiency_Ratio` é a única feature fortemente relacionada ao target (Spearman 0,74). As variáveis categóricas têm correlação próxima de zero e foram descartadas. O modelo final usa **7 das 18 colunas**.
- **Acurácia de 92,2% (teste 40%) e 90,7% (teste 15%)**, contra 48,6% do baseline (sempre prever a classe mais frequente). Todos os erros ocorrem entre classes vizinhas.
- Em 50 divisões aleatórias, a acurácia média é igual nos dois cenários (~91%), mas o teste de 15% varia o dobro (desvio de 1,9 p.p. contra 1,0 p.p.).

## Como executar

Abra o projeto no Google Colab: (https://colab.research.google.com/drive/14pGSiPKge_zRz_-optP4D-MOn3EzqyE2?usp=sharing)
