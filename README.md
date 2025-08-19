# Challenge - TelecomX Parte 2 🚀

Solução do desafio da **Telecom X**, focada na previsão de **churn** (evasão de clientes) usando técnicas de **Machine Learning** para identificar fatores que levam ao cancelamento de serviços.

Este projeto faz parte do último desafio do programa **Oracle Next Education (ONE)**.

# 🔍 Cancelamento de Clientes

## 🎯 Missão

Desenvolver modelos preditivos capazes de identificar **clientes com maior probabilidade de cancelamento**, permitindo à empresa agir preventivamente e reduzir a evasão.

---

## 🧠 Objetivos

✔️ Preparar os dados para modelagem (limpeza, codificação, normalização)  
✔️ Analisar a correlação entre variáveis e realizar seleção de atributos  
✔️ Construir múltiplos modelos de classificação  
✔️ Avaliar o desempenho dos modelos com métricas relevantes  
✔️ Interpretar os resultados e entender os principais fatores de evasão  
✔️ Gerar insights estratégicos para retenção de clientes

---

## 📦 Etapas do Projeto

### 📥 1. Extração dos Dados
Os dados foram importados de uma API da empresa Telecom X, no formato `.csv`. Os dados já estavam pré-tratados para iniciar as análises.

---

### 🧹 2. Preparação dos Dados

#### 🔸 Remoção de Colunas Irrelevantes
Foram excluídas colunas com **IDs**, estimativas redundantes e informações duplicadas.

#### 🔸 Codificação de Variáveis (Encoding)
As variáveis categóricas foram transformadas em numéricas usando técnicas como **One-Hot Encoding**, tornando-as compatíveis com os modelos de machine learning.

#### 🔸 Verificação de Balanceamento
Foi avaliada a proporção entre clientes cancelados e não cancelados:
- Dataset levemente desbalanceado → aplicação de **oversampling**, **undersampling** e **SMOTE**.

---

### ⚖️ 3. Balanceamento das Classes

- **RandomOverSampler:** duplicação de exemplos da classe minoritária  
- **RandomUnderSampler:** redução da classe majoritária  
- **SMOTE:** criação de exemplos sintéticos

> ✅ **SMOTE** foi o escolhido, pois mantém os dados originais e reduz risco de overfitting.

---

### ⚙️ 4. Normalização dos Dados

- Aplicado **StandardScaler** nas variáveis numéricas contínuas
- Evitou-se vazamento de dados ao aplicar apenas em dados de treino
- Modelos baseados em distância (KNN, SVM, Regressão Logística) **requerem normalização**
- Modelos baseados em árvore (Decision Tree, Random Forest) **não precisam**

---

## 📊 5. Análise de Correlação

- Utilizada **matriz de correlação** entre variáveis numéricas
- Principais variáveis correlacionadas com `Cancelamento`:
  - `Meses_de_Contrato` → correlação fraca negativa
  - `Valor_Mensal` → correlação fraca positiva

> 🔍 Não há correlação linear forte, mas a análise direcionada (boxplot/stripplot) revelou tendências importantes.

---

## 📈 6. Visualizações

### 📦 Boxplot – Tempo de Contrato por Cancelamento
Clientes que **evadiram** geralmente têm **menos meses de contrato**.

### 💸 Stripplot – Valor Mensal por Cancelamento
Clientes que **pagam mais** mensalmente tendem a **evadir mais**.

---

## 🤖 7. Modelagem

Foram construídos e avaliados **quatro modelos de classificação**:

| Modelo                 | Normalização | Sensível à Escala |
|------------------------|--------------|-------------------|
| Resultado do Modelo Logístico | Sim          | Sim               |
| Desempenho do Random Forest   | Não          | Não               |
| Desempenho do KNN             | Sim          | Sim               |
| Desempenho da Árvore de Decisão | Não          | Não               |


---

## 📊 8. Avaliação dos Modelos

Métricas utilizadas:

- **Acurácia**
- **Precisão**
- **Recall**
- **F1-Score**
- **Matriz de Confusão**

### 📌 Resultados:

| Modelo                   | Acurácia | Precisão | Recall | F1-Score |
|--------------------------|----------|----------|--------|----------|
| Resultado do Modelo Logístico | 0.7996   | 0.6544   | 0.5214 | 0.5804   |
| Desempenho do Random Forest   | 0.7896   | 0.6434   | 0.4679 | 0.5418   |
| Desempenho do KNN             | 0.7569   | 0.5473   | 0.4947 | 0.5197   |
| Desempenho da Árvore de Decisão | 0.7264   | 0.4859   | 0.5053 | 0.4954   |


> 🏆 **Regressão Logística** foi o modelo com melhor desempenho geral.

---

## 🔍 9. Interpretação: Importância das Variáveis

As variáveis mais influentes segundo a **Regressão Logística**:

- `Meses_de_Contrato`: quanto menor, maior chance de evasão  
- `Valor_Mensal`: valores mais altos indicam maior risco de cancelamento  
- Serviços como segurança, backup e suporte também tiveram influência

---

## 🧠 10. Conclusões Estratégicas

- **Ações de retenção** devem focar em clientes com **contratos curtos** e **valores altos**
- Oferecer **descontos progressivos** e **benefícios personalizados**
- Utilizar o modelo de Regressão Logística para **monitorar cancelamentos em tempo real**
- Investir em **serviços adicionais** que demonstraram reduzir a evasão

---

## 🚀 Tecnologias Utilizadas

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)  
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)  
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)  
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)  
![Seaborn](https://img.shields.io/badge/Seaborn-2D7188?style=for-the-badge&logo=seaborn&logoColor=white)  
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)  
