# 📊 Análise de Churn - TelecomX
---
Este projeto foi desenvolvido como parte do programa **Oracle Next Education (ONE)**, uma iniciativa educacional promovida pela **Oracle** em parceria com a **Alura**, tendo como objetivo analisar os dados de clientes da empresa TelecomX a fim de identificar os principais fatores que levam ao cancelamento de contrato (Churn) e propor recomendações para melhorar a retenção de clientes.


## 🧠 Objetivo

Investigar as causas do churn e gerar insights acionáveis com base em dados históricos dos clientes.

---

## 🔧 Metodologia

1. **Extração dos Dados**  
   - Dados importados de arquivo `.json`.

2. **Transformação**  
   - Normalização da estrutura em um DataFrame.
   - Conversão de colunas numéricas (ex: `TotalCharges`) para tipo adequado.
   - Tratamento de valores nulos e criação da coluna `Daily_Charge`.
   - Mapeamento binário de variáveis textuais (Yes/No → 1/0).

3. **Análise Exploratória**  
   - Visualizações com gráficos de barras, histograma, boxplot e heatmap.
   - Análise de churn por tempo de contrato, tipo de serviço, método de pagamento, etc.

---

## 📈 Resultados e Gráficos

### Distribuição geral do Churn
![Distribuição geral do Churn](imagens_telecom/churn.png)  
Mostra a proporção entre clientes que cancelaram (`Churn = Yes`) e os que permaneceram na base. Cerca de 26% dos clientes realizaram o cancelamento, o que levanta a necessidade de investigar os fatores associados.

---

### Churn por Tipo de Contrato
![Churn por Tipo de Contrato](imagens_telecom/churn_por_tipo_contrato.png)  
Clientes com contratos mensais apresentaram a maior taxa de cancelamento, enquanto contratos de 1 e 2 anos mostraram churn significativamente menor. Indicando que clientes tendem a cancelar com contratos mais curtos.

---

### Churn por Tenure e Gastos
![Churn por Tenure e Gastos](imagens_telecom/churn_por_tenures_e_gastos.png)  
Clientes com menos de 6 meses de contrato e altos gastos mensais estão entre os que mais cancelam. O custo percebido no início da jornada do cliente influencia fortemente o churn.

---

### Churn por Método de Pagamento
![Churn por Método de Pagamento](imagens_telecom/churn_por_metodo_pgto.png)  
O método "Electronic check" é disparado o que mais apresenta churn, sugerindo desconforto ou desconfiança com esse tipo de pagamento. Outras formas como cartão de crédito apresentam taxas mais baixas.

---

### Churn por Faixa Etária (SeniorCitizen)
![Churn por Faixa Etária](imagens_telecom/churn_por_faixa_etaria.png)  
Clientes que não são classificados como “SeniorCitizen” (ou seja, adultos mais jovens) apresentaram maiores taxas de churn, o que pode indicar perfis mais voláteis ou menos comprometidos com fidelidade.

---

### Churn por Dependentes
![Churn por Dependentes](imagens_telecom/churn_por_dependentes.png)  
Clientes sem dependentes demonstram maior propensão a cancelar. Isso pode estar relacionado a um uso mais individualizado dos serviços e menor engajamento.

---

### Churn por Serviços de Streaming
![Churn por Serviços de Streaming](imagens_telecom/churn_por_servicos_streaming.png)  
Clientes que não possuem serviços de streaming, como `StreamingTV` ou `StreamingMovies`, tendem a cancelar mais. A presença desses serviços pode aumentar a percepção de valor do pacote.


---

## 📌 Principais Fatores Identificados

| Fator                   | Descrição                                                      |
|-------------------------|----------------------------------------------------------------|
| Tenure < 6 meses        | risco de churn muito alto                                      |
| Contrato mensal         | 42,7% de churn vs. 11,1% (1 ano) e 2,9% (2 anos)               |
| Daily_Charge elevado    | custos diários altos → maior evasão                            |
| Electronic check        | método de pagamento com maior churn                            |
| **Falta de uso de serviços**    | Clientes que não usam os serviços (InternetService, TechSupport, OnlineBackup e PaperlessBilling) tendem a cancelar seus contratos.|
| **Serviços de má qualidade**    | Insatisfação com os serviços OnlineSecurity e DeviceProtection levando a uma alta tendência de churn.|
| **SeniorCitizen = 0**          | Jovens/adultos têm maior probabilidade de cancelar.                       |
| **Sem parceiros e sem dependentes** | Clientes jovens/adultos que moram sozinhos apresentam taxas de churn mais elevadas.|
| **InternetService = 'No'**     | Ausência do serviço principal (internet) aumenta o risco de churn.        |
| **DeviceProtection e TechSupport (ativos)** | Clientes que possuem esses serviços também mostram alta evasão, possivelmente por insatisfação com o valor percebido. |
| **Charges_Monthly muito alto** | Pode indicar percepção negativa de custo-benefício.                      |

---

## ✅ Recomendações

- **Onboarding Intensivo:** check-ins nos primeiros meses, tutoriais e canais de suporte acessíveis.
- **Promoções para contratos longos:** descontos ou meses gratuitos para fidelizar clientes.
- **Pacotes de serviços essenciais com desconto:** bundles com TechSupport, Segurança e Backup.
- **Revisão da experiência com Electronic check:** melhorar usabilidade e incentivar troca por métodos automáticos.
- **Campanhas direcionadas:** foco em jovens sem dependentes/parceiros, usuários de fatura digital e clientes com contrato mensal.
- **Pesquisa de satisfação ativa:** monitorar qualidade dos serviços com alta evasão.
- **Análise de valor percebido:** para clientes com custos elevados, garantir comunicação clara dos benefícios.
---

## 🛠️ Próximos Passos

- Implementar **modelo preditivo de churn** com base nas variáveis mais relevantes.
- Criar **sistema de alertas** para retenção proativa.
- **Acompanhar a evolução** da taxa de churn após ações aplicadas.
- **Aprimorar qualidade dos serviços** com maior índice de cancelamento.

---

## 📁 Estrutura do Projeto

├── TelecomX_Churn_Analysis.ipynb # Notebook principal com análise e visualizações

├── dados/

│ └── telecom_users.json # Base de dados original

├── imagens_telecom/

│ ├── churn.png

│ ├── churn_por_genero.png

│ ├── churn_por_faixa_etaria.png

│ ├── churn_por_parceiros.png

│ ├── churn_por_dependentes.png

│ ├── churn_por_tipo_contrato.png

│ ├── churn_por_metodo_pgto.png

│ ├── churn_por_servicos.png

│ ├── churn_por_servicos_streaming.png

│ ├── churn_por_tenures_e_gastos.png

│ ├── correlacao_campos.png

│ └── distribuicao_churn_gastos_diarios.png

└── README.md
---

## ▶️ Instruções para Execução

1. Clone este repositório:

```
git clone https://github.com/seu-usuario/nome-do-repositorio.git
```
2. Instale os pacotes necessários (utilizando virtualenv recomendado):

```
pip install pandas matplotlib seaborn
```

3. Execute o notebook:

```
jupyter notebook TelecomX_Churn_Analysis.ipynb
```
