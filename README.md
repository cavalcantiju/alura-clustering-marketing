# Segmentação de Clientes com K-Means

Este projeto utiliza técnicas de aprendizado de máquina não supervisionado para agrupar consumidores com base em seus interesses e comportamentos em redes sociais. O objetivo é fornecer insights para a equipe de marketing, permitindo a criação de campanhas mais direcionadas e eficazes.

---

## Objetivo do Projeto

- Identificar padrões de comportamento em dados de consumidores  
- Segmentar usuários em grupos (clusters) com interesses semelhantes  
- Analisar as características de cada grupo  
- Disponibilizar o modelo treinado para uso em produção  

---

## Estrutura dos Dados

O conjunto de dados contém:

- 12.992 registros  
- 27 colunas  

### Tipos de atributos

**Categóricos:**
- sexo (F, M, NE)

**Numéricos:**
- idade  
- número de amigos  
- categorias de interesse (ex: basquete, música, compras, etc.)

Os valores representam a frequência com que determinadas palavras foram mencionadas nas redes sociais dos usuários.

---

## Processamento de Dados

### Codificação de Variáveis Categóricas

Como algoritmos de clustering utilizam cálculos de distância, a variável categórica `sexo` foi transformada em variáveis numéricas utilizando o OneHotEncoder.

Resultado:
- sexo_F  
- sexo_M  
- sexo_NE  

---

### Normalização

Os dados apresentavam escalas muito diferentes entre si, o que poderia impactar negativamente o modelo.

Foi aplicado o MinMaxScaler para normalizar os dados no intervalo entre 0 e 1, garantindo que todas as variáveis tenham o mesmo peso no cálculo das distâncias.

---

## Desenvolvimento do Modelo

Foi utilizado o algoritmo K-Means para segmentação dos dados.

### Escolha do número de clusters

Foram utilizadas duas métricas:

**Método do Cotovelo (Elbow Method):**
- Avalia a inércia (soma das distâncias intra-cluster)

**Coeficiente de Silhueta (Silhouette Score):**
- Mede a qualidade dos agrupamentos  
- Varia de -1 a 1  

Após a análise, o melhor valor foi:

- k = 3  
- Silhouette Score médio = 0.745  

---

## Análise dos Clusters

### Cluster 0
- Predominantemente feminino  
- Interesses principais:
  - música  
  - cabelo  
  - dança  
  - compras  

### Cluster 1
- Predominantemente masculino  
- Interesses principais:
  - esportes (futebol americano, basquete)  
  - bandas  
  - rock  

### Cluster 2
- Sexo não especificado (NE)  
- Perfil mais equilibrado  
- Interesses:
  - música  
  - dança  
  - estética  

---

## Exportação de Objetos

Para garantir a reprodutibilidade e utilização em produção, foram salvos:

- encoder.pkl: transformação de variáveis categóricas  
- scaler.pkl: normalização dos dados  
- kmeans.pkl: modelo treinado  

---

## Tecnologias Utilizadas

- Python 3  
- Pandas e NumPy  
- Scikit-learn  
- Matplotlib e Seaborn  
- Joblib  

---

## Conclusão

O modelo permitiu segmentar os consumidores em três grupos distintos com base em seus interesses. Esses agrupamentos podem ser utilizados pela equipe de marketing para desenvolver campanhas mais direcionadas e eficazes.
