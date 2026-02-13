# Car Insurance Risk Analysis

Análise exploratória, dashboard e modelo interpretável aplicados ao dataset **Car Insurance Data (Kaggle)**.

Projeto desenvolvido como parte de teste técnico para posição de Analista de Dados.

---

## Objetivo

Analisar a taxa de sinistro (`outcome`) e identificar fatores associados a maior risco, com foco em:

- Segmentação de clientes
- Apoio à precificação
- Insights estratégicos para underwriting
- Construção de modelo interpretável

---

## 📂 Estrutura do Projeto
📄 Teste_Técnico_Analista_de_Dados.ipynb
📄 Car_Insurance_Claim.csv
📄 Car Insurance Dashboard.pbix
📄 README.md
📄 car_insurance_tratado.csv


- `notebooks/` → EDA + Modelagem bônus
- `car_insurance_tratado.csv` → dataset final tratado
- `dashboard/` → arquivos Power BI
- `README.md` → documentação do projeto

---

## 🔎 Parte A — EDA

### ✔ Auditoria de Dados
- Verificação de tipos
- Missing values (~10% em credit_score e annual_mileage)
- Duplicados (não encontrados)
- Outliers (valores plausíveis mantidos)
- Balanceamento de classes (31% sinistros)

### ✔ Tratamento
- Padronização de colunas
- Conversão de variáveis binárias
- Imputação por mediana
- Criação de flags de missing
- Criação de buckets para score e quilometragem

### 📊 Principais Insights

1. **Experiência é o principal driver de risco**
   - 0–9 anos → ~63% taxa
   - 30+ anos → <5%

2. **Credit Score possui relação monotônica**
   - Quartil inferior → ~55%
   - Quartil superior → ~15%

3. **Quilometragem aumenta exposição ao risco**
   - >14k milhas → ~47%
   - <10k milhas → ~23%

4. **Histórico isolado (multas/acidentes) não é linear**
   - Experiência domina efeito do histórico

---

## 📊 Parte B — Dashboard (Power BI)

### Página 1 — Overview
- Overall Claims Rate
- All Sinister
- Customers
- Average Claims Rate by Age
- Accident Rate (Average) by Driving Experience
- All customers and All Sinister

### Página 2 — Risk Drivers
- Heatmap Driving Experience
- Average Claim Rate by Speeding Violations
- Driving Experience and Customers by Sinister

### Página 3 — Recomendações
- Ação 1 — Ajuste de prêmio por experiência
- Ação 2 — Integração do score na precificação
- Ação 3 — Incentivo a baixa quilometragem
- Ação 4 — Ajustar modelo de avaliação de histórico

---

## 🤖 Bônus — Modelo Interpretável

Foi utilizada **Regressão Logística** para explicar fatores associados ao risco.

### Métricas:
- AUC
- F1 Score

Principais variáveis confirmadas:
- Baixa experiência
- Baixo credit score
- Alta quilometragem

Modelo adicional:
- Árvore de decisão (max_depth=4) para visualização interpretável

---

## ⚠️ Limitações

- Dataset sem dimensão temporal
- Ausência de informações financeiras (prêmio, valor segurado)
- Possível correlação entre idade e experiência
- Dados (Kaggle)

---

## 🛠 Tecnologias Utilizadas

- Python (Pandas, NumPy)
- Scikit-Learn
- Matplotlib / Seaborn
- Power BI

---

## 🚀 Como Executar

1. Clone o repositório
2. Use google colab
3. instale as dependencias

pip install pandas numpy scikit-learn matplotlib seaborn

3. Execute o notebook em `notebooks/`
4. Abra o arquivo Power BI em `dashboard/`

---

## 👤 Autor

Allan dos Santos  
[LinkedIn] (https://www.linkedin.com/in/allansantos881/) 
[GitHub] (https://github.com/allansantos881)

---

## 📈 Conclusão

A análise demonstra que experiência, credit score e quilometragem são os principais drivers de risco da carteira.

Recomenda-se estratégia de precificação segmentada baseada nesses fatores para melhoria da sinistralidade e rentabilidade.
