## Classificação do Tráfego de Rede Utilizando Algoritmos de Aprendizado de Máquina

Este trabalho é parte integrante da disciplina de Engenharia de Sistemas de Detecção de Intrusões do Programa de Pós-Graduação em Engenharia de Software da Unipampa.

## Implementação 
### Dataset 
UNSW-NB15, conjunto de dados de tráfego de rede para problemas de detecção de intrusões
* O dataset pode ser obtido em: https://research.unsw.edu.au/projects/unsw-nb15-dataset

O conjunto de dados (dataset) UNSW-NB15 foi concebido e gerado no Cyber Range Lab do Australian Centre for Cyber Security (ACCS). Seu objetivo principal foi simular um ambiente híbrido de atividades normais modernas e diversos comportamentos de ataque no escopo do tráfego de rede de computadores, buscando maior realismo em relação a datasets anteriores.
Para a geração do tráfego de rede “raw”, a ferramenta IXIA PerfectStorm foi utilizada para simular de forma sintética o tráfego normal e nove famílias de ciberataque: Fuzzers, Analysis, Backdoors, DoS, Exploits, Generic, Reconnaissance, Shellcode e Worms. O tráfego capturado foi processado pelas ferramentas Argus e Bro-IDS. A partir deste processamento e da aplicação de doze algoritmos, foram extraídas 49 características (features) com o rótulo de classe. Esse rótulo é fornecido para classificação binária (ataque ou não ataque) e para classificação multiclasse (os nove tipos de ataque mais o tráfego normal).
O dataset completo totaliza 2.540.044 instâncias/conexões e é distribuído em vários arquivos CSV, sendo os mais relevantes:
UNSW-NB15_features.csv: Descreve detalhadamente cada uma das 49 features do dataset.
UNSW_NB15_training-set.csv: Partição predefinida com 175.341 instâncias. É o conjunto de treinamento sugerido pelos autores, pois já inclui as features e os rótulos de classe binários e de categoria.
UNSW_NB15_testing-set.csv: Partição predefinida com 82.332 instâncias. É o conjunto sugerido para teste, fundamental para garantir a comparabilidade do estudo com outros trabalhos na literatura.


### Objetivo do Trabalho

Esse trabalho apresenta uma análise comparativa  para otimização de um Sistema de Detecção de Intrusão (IDS) baseado em Inteligência Artificial aplicado ao dataset UNSW-NB15. O objetivo deste estudo é perceber através da investigação do dataset e exploração dos hiperparâmetros dos classificadores identificar o mais adequado para a classificação em termos de eficácia na detecção de falsos positivos, falsos negativos e custo computacional.O estudo parte da limpeza de dados, codificação de variáveis categóricas, seleção de features baseado em Random Forest. Para o treino do modelo foram utilizados os classificadores K-Nearest Neighbors (k-NN), Multi-Layer Perceptron (MLPClassifier) e Support Vector Machine (SVM). Para exploração e identificação dos valores ótimos dos hiperparâmetros dos classificadores foi utilizado o RandomizedSearchCV. Os resultados obtidos foram satisfatórios de modo geral.

### Tecnologias Utilizadas

Para o desenvolvimento do trabalho foram utilizadas as seguintes ferramentas: Google Colaboratory (ambiente de programação), Google Drive (armazenamento da instância), Google Gemini, linguagem Python v3.7, além das bibliotecas pandas, scikit-learn, numpy e matplotlib.

### Metodologia,

A implementação prática deste estudo consiste nos seguintes passos:

* Escolha do Dataset
* Pré-Processamento
* Seleção de Features
* Treinamento dos modelos
* Análise de Resultados (Avaliação do Conjunto de Testes)

  
### Resultados Obtidos.

### Seleção de Features utilizando Threshold = "mean"

  Treinando Random Forest para Feature Importance...
Treinamento concluído.

Número original de features: 191\
Número de features selecionadas: 34

Top Features Selecionadas (baseado no threshold da Mediana):
['dur', 'spkts', 'dpkts', 'sbytes', 'dbytes', 'rate', 'sttl', 'dttl', 'sload', 'dload', 'sloss', 'dloss', 'sinpkt', 'dinpkt', 'sjit', 'djit', 'swin', 'stcpb', 'dtcpb', 'tcprtt', 'synack', 'ackdat', 'smean', 'dmean', 'ct_srv_src', 'ct_state_ttl', 'ct_dst_ltm', 'ct_src_dport_ltm', 'ct_dst_sport_ltm', 'ct_dst_src_ltm', 'ct_src_ltm', 'ct_srv_dst', 'proto_arp', 'state_INT']

Ranking das 20 Features mais importantes (em porcentagem):\
sttl              11.4511%\
ct_state_ttl       6.3667%\
dload              5.5257%\
rate               5.1310%\
dttl               4.5252%\
ackdat             4.1214%\
sload              4.0810%\
dmean              3.7315%\
synack             3.7091%\
ct_srv_dst         3.6343%\
dinpkt             3.3235%\
sbytes             3.2391%\
dbytes             3.2094%\
tcprtt             2.7676%\
state_INT          2.7657%\
dpkts              2.6333%\
sinpkt             2.4137%\
dur                2.3814%\
ct_dst_src_ltm     2.3089%\
ct_srv_src         2.3015%\
dtype: object


