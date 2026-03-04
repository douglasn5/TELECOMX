# 📡 TelecomX — Análise de Evasão de Clientes (Churn)

> Projeto de ETL + Análise Exploratória de Dados para identificar os fatores que causam a evasão de clientes na TelecomX.

---

## 📋 Sobre o Projeto

A **TelecomX** é uma empresa fictícia de telecomunicações que enfrenta um alto índice de cancelamento de clientes. Este projeto realiza um processo completo de **ETL (Extração, Transformação e Carga)** seguido de uma **EDA (Análise Exploratória de Dados)** para identificar padrões de evasão e fornecer insumos para modelos preditivos.

---

## 🗂️ Estrutura do Projeto

```
TelecomX/
│
├── TelecomX_BR.ipynb          # Notebook principal (ETL + EDA + Relatório)
├── TelecomX_Data.json         # Dados brutos (ou obtidos via API)
├── TelecomX_dicionario.md     # Dicionário de dados
└── README.md                  # Este arquivo
```

---

## 🚀 Como Executar

### ✅ Opção 1 — Google Colab (recomendado)

1. Acesse [Google Colab](https://colab.research.google.com)
2. Clique em **Arquivo → Fazer upload de notebook**
3. Selecione o arquivo `TelecomX_BR.ipynb`
4. Execute todas as células em ordem: **Runtime → Run all**

> Os dados são carregados automaticamente via URL da API do GitHub — não é necessário fazer upload do JSON.

### ✅ Opção 2 — VS Code / Local

```bash
# 1. Clone ou baixe o projeto
# 2. Instale as dependências
pip install pandas numpy matplotlib seaborn requests

# 3. Abra o notebook
jupyter notebook TelecomX_BR.ipynb
```

---

## 📦 Dependências

| Biblioteca | Versão mínima | Uso |
|---|---|---|
| `pandas` | 1.3+ | Manipulação de dados |
| `numpy` | 1.20+ | Operações numéricas |
| `matplotlib` | 3.4+ | Visualizações |
| `seaborn` | 0.11+ | Gráficos estatísticos |
| `requests` | 2.25+ | Chamada à API |

> Todas as bibliotecas já estão disponíveis no Google Colab sem instalação adicional.

---

## 📊 O que o Notebook Faz

### Seção 1 — Extração (E)
- Importação dos dados via API (GitHub raw URL)
- Normalização do JSON aninhado para DataFrame tabular

### Seção 2 — Transformação (T)
- Exploração do dataset e tipos de dados
- Identificação e correção de inconsistências
- Remoção de registros sem rótulo de Churn
- Conversão de tipos (`Charges_Total` string → float)
- Correção de valores nulos
- Criação de colunas auxiliares (`Contas_Diarias`, `Faixa_Mensal`, `Qtd_Servicos`)
- Padronização de variáveis binárias (Yes/No → 1/0)

### Seção 3 — Carga e Análise (L)
- Análise descritiva (média, mediana, desvio padrão)
- Distribuição da variável Churn
- Churn por variáveis categóricas (gênero, contrato, pagamento, internet, tenure, faixa mensal, serviços)

### Seção 4 — Análise de Correlação (Extra)
- Heatmap de correlação entre todas as variáveis
- Ranking de correlação com Churn
- Dispersão: Conta Diária × Tenure × Churn
- Impacto da quantidade de serviços na evasão

### Seção 5 — Relatório Final
- Introdução e contextualização do problema
- Resumo do processo de limpeza
- Sumário executivo com principais métricas
- Conclusões e insights estratégicos
- Recomendações para a equipe de Data Science

---

## 🔑 Principais Resultados

| Fator | Taxa de Churn |
|---|---|
| **Taxa geral de evasão** | ~26,5% |
| Contrato mês a mês | ~42,7% |
| Pagamento por cheque eletrônico | ~45,3% |
| Internet por fibra óptica | ~41,9% |
| Sem segurança online | ~41,8% |
| Clientes idosos (≥65 anos) | ~41,7% |
| **Contrato bianual** | ~2,8% ✅ |
| **5+ serviços adicionais** | ~8,5% ✅ |

---

## 💡 Variáveis Mais Relevantes para Modelo Preditivo

```
Contract · PaymentMethod · InternetService · tenure
OnlineSecurity · TechSupport · Charges_Monthly · Qtd_Servicos
```

---

## 🗃️ Dicionário de Dados Resumido

| Coluna | Descrição |
|---|---|
| `customerID` | ID único do cliente |
| `Churn` | Evasão (Yes/No) |
| `gender` | Gênero do cliente |
| `SeniorCitizen` | Idoso (≥65 anos): 0/1 |
| `tenure` | Meses de contrato |
| `Contract` | Tipo de contrato (mensal/anual/bianual) |
| `PaymentMethod` | Forma de pagamento |
| `InternetService` | Tipo de serviço de internet |
| `Charges_Monthly` | Cobrança mensal |
| `Charges_Total` | Cobrança total acumulada |

> Consulte `TelecomX_dicionario.md` para a descrição completa de todas as colunas.

---

## 👤 Autor

Projeto desenvolvido como parte do desafio **Churn de Clientes — TelecomX**  
Equipe de Data Science · TelecomX

---

*🐍 Python · Pandas · NumPy · Matplotlib · Seaborn*
