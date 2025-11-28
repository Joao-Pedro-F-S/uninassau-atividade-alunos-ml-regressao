# RELATÓRIO FINAL – PERFORMANCE ESTUDANTIL
*Projeto de Machine Learning – Etapa 5*  
*Grupo: [Insira os nomes]*  
*Ano: 2025*

---

## 1. Resumo Executivo
Este projeto teve como objetivo desenvolver um modelo de Machine Learning capaz de prever o desempenho final de estudantes com base em dados acadêmicos, comportamentais e socioeducacionais presentes no dataset **Students Performance**.  
Ao longo das etapas, realizamos exploração dos dados, pré-processamento, modelagem inicial, comparação de algoritmos e otimização de hiperparâmetros.

O melhor modelo encontrado na Etapa 3 foi um **SVR (kernel RBF)** encapsulado em um **Pipeline com StandardScaler**, garantindo normalização adequada das features. Na Etapa 4, realizamos tuning utilizando **RandomizedSearchCV com validação cruzada**, buscando ajustar hiperparâmetros como `C`, `gamma` e `epsilon`.

Embora o processo de otimização tenha explorado novas combinações, o desempenho **piorou levemente**, comportamento comum em SVR quando o espaço de busca é amplo e o dataset possui ruído. Mesmo assim, a análise detalhada permitiu compreender os efeitos dos hiperparâmetros, interpretar os erros e reforçar a importância de aplicar tuning de forma controlada.

O produto final do projeto inclui:  
- Modelo final salvo (`modelo_final.joblib`)  
- Notebooks organizados por etapa  
- Relatório técnico completo  
- Slides de apresentação final  

---

## 2. Introdução

### 2.1 Contexto do Problema
Compreender os fatores que influenciam o desempenho acadêmico é essencial para escolas, professores e gestores educacionais. A previsão do desempenho de estudantes permite:

- Identificar alunos em risco
- Direcionar intervenções pedagógicas
- Planejar políticas educacionais
- Otimizar recursos

### 2.2 Objetivo do Projeto
O objetivo deste projeto é **prever a nota final dos estudantes**, utilizando variáveis relacionadas a:

- Hábitos de estudo  
- Frequência escolar  
- Desempenho anterior  
- Informações socioeconômicas  

### 2.3 Metodologia Geral
As etapas principais foram:

1. Exploração dos Dados  
2. Pré-processamento  
3. Modelagem  
4. Otimização  
5. Relatório final  

---

## 3. Exploração dos Dados

### 3.1 Sobre o Dataset
O dataset **Students Performance** contém variáveis relacionadas a aspectos acadêmicos e comportamentais dos estudantes.

### 3.2 Estatísticas Descritivas
Estatísticas como média, mediana, desvio padrão e distribuição das variáveis foram avaliadas durante a EDA.

### 3.3 Principais Achados
- Horas de estudo correlacionam positivamente com a nota final.  
- Reprovações e faltas correlacionam negativamente com desempenho.  
- Variáveis socioeconômicas têm impacto moderado.  

---

## 4. Pré-Processamento

### 4.1 Missing Values
- Remoção de linhas com valores ausentes.

### 4.2 Normalização
✔ StandardScaler integrado ao Pipeline.

### 4.3 Outliers
- Mantidos no dataset.

### 4.4 Feature Engineering
- Dataset original mantido; conversões e normalização foram realizadas.

### 4.5 Split dos Dados
- 70% treino  
- 15% validação  
- 15% teste  

---

## 5. Modelagem

### 5.1 Modelos Testados
- Linear Regression  
- Lasso  
- Ridge  
- Decision Tree  
- Random Forest  
- **SVR (melhor)**  
- KNN  

### 5.2 Métricas Utilizadas
- MAE, MSE, RMSE, R², MAPE

### 5.3 Resultados da Etapa 3
| Métrica | Valor |
|--------|-------|
| MAE | 0.3580 |
| MSE | 0.2374 |
| RMSE | 0.4873 |
| R² | 0.7385 |
| MAPE | 126.08% |

---

## 6. Otimização

### 6.1 Modelo Selecionado
Pipeline com StandardScaler + SVR RBF.

### 6.2 Técnica Utilizada
RandomizedSearchCV, cv=5, scoring=MAE.

### 6.3 Métricas Após Otimização
| Métrica | Antes | Depois |
|--------|--------|---------|
| MAE | 0.3580 | 0.4588 |
| MSE | 0.2374 | 0.4099 |
| RMSE | 0.4873 | 0.6402 |
| R² | 0.7385 | 0.5487 |
| MAPE | 126.08% | 129.40% |

### 6.4 Interpretação
- O desempenho piorou após o tuning.  
- Normal em SVR quando o espaço de busca é amplo.  
- Processo ainda foi valioso para entendimento do modelo.  

---

## 7. Conclusões

### 7.1 Resultados
- Modelo final escolhido: SVR RBF.  
- Modelagem e tuning documentados.  
- Pipeline escalável e reprodutível.

### 7.2 Limitações
- Dataset pequeno  
- Modelo sensível a hiperparâmetros  
- MAPE elevado  

### 7.3 Trabalhos Futuros
- Testar XGBoost, CatBoost  
- Aumentar o dataset  
- Engenharia de features  
- Bayesian Optimization  

### 7.4 Lições Aprendidas
- Importância da normalização  
- Tuning não garante melhoria  
- Necessidade de interpretar resíduos  

---

## 8. Referências
- Scikit-Learn Documentation  
- Student Performance Dataset  
- Hands-On Machine Learning – Géron  
- ISLR  
- XGBoost Docs  
