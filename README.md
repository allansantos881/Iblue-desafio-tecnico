# Car Insurance Risk Analysis

Análise exploratória (EDA), dashboard e modelo interpretável aplicados ao dataset **Car Insurance Data (Kaggle)**.

Projeto desenvolvido como parte de **teste técnico para Analista de Dados**.

---

## Objetivo

Analisar a taxa de sinistro (`outcome`) e identificar fatores associados a maior risco, apoiando:

- Segmentação de clientes
- Precificação
- Underwriting
- Recomendações acionáveis
- Modelo interpretável (bônus)

---

## Estrutura do Projeto

Arquivos principais do repositório:

- `Teste_Técnico_Analista_de_Dados.ipynb` → EDA
- `Validação (AUC + F1) - Analista de Dados.ipynb` → Modelagem bônus
- `Car_Insurance_Claim.csv` → dataset original
- `car_insurance_tratado.csv` → dataset tratado para Power BI
- `Car Insurance Dashboard.pbix` → dashboard Power BI
- `README.md` → documentação

---

## Parte A — EDA

### ✔ Auditoria de Dados
- Tipos de dados e consistência
- Missing values (~10% em `credit_score` e `annual_mileage`)
- Duplicados (não identificados)
- Outliers (valores extremos plausíveis, mantidos)
- Balanceamento de classes: **~31%** sinistros (classe 1)

### ✔ Tratamento
- Padronização de colunas (lowercase)
- Conversão de variáveis binárias para inteiro
- Imputação por **mediana** em `credit_score` e `annual_mileage`
- Criação de **flags de missing** (indicadores)
- Criação de buckets (quartis) para score e quilometragem (para análise/BI)

---

## Principais Insights (quantificados)

1. **Experiência é o principal driver de risco**
   - 0–9 anos: ~63% taxa de sinistro
   - 30+ anos: <5%

2. **Credit Score apresenta relação monotônica com risco**
   - Quartil inferior: ~55%
   - Quartil superior: ~15%

3. **Quilometragem anual aumenta exposição ao risco**
   - >14k milhas: ~47%
   - <10k milhas: ~23%

4. **Histórico isolado (multas/acidentes) não é linear**
   - Quando analisado em conjunto, **experiência domina o efeito do histórico**

---

## Parte B — Dashboard (Power BI)

### Página 1 — Overview
- Cards: Customers, All Sinister, Overall Claims Rate
- Comparação de taxa por **Age** e **Driving Experience**

### Página 2 — Risk Drivers
- Heatmap: **Driving Experience x Past Accidents** (taxa de sinistro)
- Análises por Speeding Violations e outros drivers (com filtros)

### Página 3 — Recomendações
- Ação 1: Ajuste de prêmio por experiência
- Ação 2: Integração do score na precificação
- Ação 3: Incentivo a baixa quilometragem (produto baseado em uso)
- Ação 4: Reavaliar uso de histórico isolado (multas/acidentes)

---

## Bônus — Modelo Interpretável

### Modelo
- **Regressão Logística** (interpretável) para estimar probabilidade de sinistro
- Modelo adicional: **Árvore de decisão (max_depth=4)** para visualização de regras

### Validação
- **AUC (Logit): 0.875**
- F1 Score calculado no notebook (ver célula de métricas)

### Principais fatores confirmados pelo modelo
- Baixa experiência
- Baixo credit score
- Alta quilometragem

---

## Limitações do Dataset

- Não há dimensão temporal (dados transversais)
- Ausência de variáveis financeiras do seguro (prêmio, valor segurado, franquia, custo do sinistro)
- Possível correlação entre idade e experiência (colinearidade)
- Missing values (~10%) exigem imputação
- Dataset público do Kaggle (pode não refletir integralmente cenários reais)

---

## Tecnologias Utilizadas

- Python: Pandas, NumPy
- Scikit-Learn
- Matplotlib / Seaborn
- Power BI

---

## Como Executar

### Notebook (Colab/Jupyter)
1. Abra o notebook `Teste_Técnico_Analista_de_Dados.ipynb`
2. Instale dependências (se necessário):
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
Execute as células do notebook

Dashboard (Power BI)
Abra Car Insurance Dashboard.pbix

Caso necessário, aponte a fonte para car_insurance_tratado.csv

👤 Autor
Allan dos Santos
LinkedIn: https://www.linkedin.com/in/allansantos881/
GitHub: https://github.com/allansantos881

Conclusão
A análise mostra que experiência, credit score e quilometragem são os principais drivers de risco.
Recomenda-se precificação segmentada e políticas de underwriting baseadas nesses fatores para melhorar sinistralidade e rentabilidade.
