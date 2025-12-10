Projeto Final – Previsão de Desempenho Acadêmico
Disciplina: Introdução à Machine Learning
Professor: Durval Lins de Siqueira Neto
Aluno: João Pedro de França Silva – Matrícula 01679045
Dataset: student_performace

1. Introdução

O presente trabalho tem como objetivo aplicar técnicas de Machine Learning supervisionado para o
problema de previsão de desempenho acadêmico a partir de um conjunto de dados real contendo
informações de alunos e suas respectivas notas. O projeto foi desenvolvido ao longo de quatro etapas
práticas, envolvendo desde o entendimento do problema e exploração dos dados até a construção e
otimização de um modelo de regressão capaz de prever a performance estudantil de forma automáticaNa Etapa 5, apresentada neste relatório, são consolidados todos os resultados obtidos nas etapas
anteriores, documentando as decisões tomadas, os métodos utilizados e as principais conclusões do
projeto.

2. Objetivo do Projeto

O objetivo geral do projeto é prever uma variável numérica de desempenho acadêmico (por exemplo,
nota final ou média em provas) utilizando como entrada características dos estudantes presentes no
dataset student_performace.

Os objetivos específicos foram:

- Entender o problema e as variáveis disponíveis no conjunto de dados.
- Realizar a limpeza, transformação e preparação dos dados para uso em modelos de regressão.
- Testar modelos clássicos de regressão supervisionada e comparar seu desempenho.
- Otimizar o modelo escolhido por meio de ajuste de hiperparâmetros.
- Avaliar o modelo final e discutir limitações e possibilidades de melhoria.

3. Descrição do Conjunto de Dados

O dataset student_performace contém registros de estudantes, com variáveis que representam
informações de contexto (características demográficas, educacionais e/ou socioeconômicas) e uma
variável-alvo contínua associada ao desempenho acadêmico.

De forma geral, o conjunto de dados pode ser descrito como:

- Linhas: cada linha representa um aluno.
- Colunas: incluem variáveis explicativas (features) e uma variável-alvo numérica relacionada ao
desempenho (por exemplo, nota, média ou score).
- Tipos de variáveis:
 - Variáveis numéricas (ex.: pontuações em avaliações, horas de estudo, etc.).
 - Variáveis categóricas (ex.: informações de contexto do aluno, tipo de curso, condições de
estudo, etc.).

Ao longo das quatro primeiras etapas, foram identificados possíveis valores ausentes ou
inconsistentes, distribuições assimétricas em algumas variáveis numéricas, presença de outliers e
correlações mais fortes entre certas variáveis explicativas e a variável-alvo, justificando sua
importância no modelo.

4. Metodologia

4.1 Etapa 1 – Entendimento do Problema e Análise Exploratória Inicial

Na primeira etapa, foram definidos:

- Problema de negócio: antecipar o desempenho acadêmico de estudantes a partir de seus dados, de
modo a apoiar ações de intervenção, monitoramento e suporte pedagógico.
- Tipo de tarefa: regressão supervisionada (variável-alvo numérica).
- Métricas de avaliação: foram utilizadas métricas clássicas de regressão, como erro médio absoluto
(MAE), erro quadrático médio (MSE/RMSE) e coeficiente de determinação (R²).
Também foi realizada uma análise exploratória inicial (EDA), contemplando:
- Verificação de tipos de dados e contagem de valores ausentes.
- Estatísticas descritivas (média, desvio padrão, mínimo, máximo e quartis).
- Análise gráfica básica (histogramas, boxplots) para entender a distribuição da variável-alvo e das
principais variáveis explicativas.
- Cálculo de correlações entre variáveis numéricas para identificar possíveis relações lineares
relevantes.

4.2 Etapa 2 – Pré-processamento de Dados

Na segunda etapa, foi construída a base de features preparada para treino de modelos de regressão.
As principais etapas de pré-processamento foram:

- Tratamento de valores ausentes.
- Codificação de variáveis categóricas (One-Hot Encoding ou codificação ordinal).
- Escalonamento/normalização de variáveis numéricas com StandardScaler.
- Divisão em treino e teste, mantendo uma proporção típica (como 70/30 ou 80/20).

Esse pré-processamento foi encapsulado em pipelines do scikit-learn, garantindo reprodutibilidade e
evitando data leakage.

4.3 Etapa 3 – Modelagem e Avaliação Inicial

Na terceira etapa, foram testados alguns modelos de regressão supervisionada, como Regressão Linemodelos de regularização (Ridge/Lasso), Árvores de Regressão e Random Forest. O modelo principal
escolhido foi o Support Vector Regressor (SVR) com kernel RBF.

Foi construída uma pipeline base utilizando:

- Um estágio de escalonamento (StandardScaler).
- Um estágio de modelagem com SVR(kernel="rbf").

Essa pipeline foi avaliada por meio de validação cruzada em k-folds, permitindo estimar o desempenhomédio e a variabilidade do modelo. Na comparação com baselines mais simples (por exemplo, um modque sempre prevê a média), o SVR apresentou melhor capacidade de capturar relações possivelmentelineares, justificando sua escolha para otimização.

4.4 Etapa 4 – Otimização de Hiperparâmetros

Na quarta etapa, o foco foi otimizar o modelo SVR por meio de ajuste de hiperparâmetros. Foram
considerados, principalmente:
- C – parâmetro de regularização.
- gamma – parâmetro associado ao kernel RBF.
- epsilon – margem de tolerância na função de perda do SVR.

A busca pelos melhores valores foi feita com técnicas como Grid Search ou Randomized Search
combinadas com validação cruzada. Em cada combinação de hiperparâmetros, foram calculadas métrcomo MAE, RMSE e R², e o conjunto com melhor desempenho médio foi selecionado como modelo fin5. Resultados Finais
Após a definição do modelo final (SVR com hiperparâmetros otimizados), o pipeline completo foi
treinado nos dados de treino e avaliado no conjunto de teste.

Os principais resultados qualitativos foram:

- Redução do erro de previsão em relação ao baseline.
- Desempenho estável em validação cruzada, indicando boa capacidade de generalização.
- Relações coerentes com o domínio educacional, onde variáveis associadas ao contexto e esforço doaluno mostraram maior influência sobre o desempenho previsto.

6. Discussão e Limitações

As principais limitações observadas foram:

- Tamanho e representatividade do dataset, que pode limitar a generalização para outros contextos.
- Qualidade e granularidade das variáveis disponíveis, que não capturam todos os fatores que
influenciam o desempenho acadêmico.
- Menor interpretabilidade do modelo SVR em comparação com modelos lineares ou baseados em árv- Possível risco de overfitting, mitigado mas não completamente eliminado, mesmo com validação
cruzada e regularização.

7. Conclusões

O projeto atingiu o objetivo de construir, otimizar e avaliar um modelo de regressão para previsão
de desempenho acadêmico utilizando o dataset student_performace. As quatro primeiras etapas
permitiram entender o problema, preparar os dados, testar abordagens clássicas e selecionar o SVR
com kernel RBF como modelo principal. A Etapa 5 consolidou esse processo em um relatório final,
conectando as decisões técnicas às implicações práticas no contexto educacional.

8. Trabalhos Futuros

Como trabalhos futuros, destacam-se:

- Inclusão de novas variáveis relacionadas ao perfil do aluno e ao contexto escolar.
- Teste de outros algoritmos de regressão, como Gradient Boosting, XGBoost ou Random Forest com
otimização completa.
- Uso de técnicas de interpretabilidade (como SHAP ou Permutation Importance).
- Implementação de uma aplicação prática, por exemplo, uma API ou sistema simples de apoio à toma
de decisão para instituições de ensino