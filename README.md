# Engenharia de Sistemas de Detecção de Intrusões 

## Classificação do Tráfego de Rede Utilizando Algoritmos de Aprendizado de Máquina

- informações como o dataset que foi utilizado/construído pelo grupo (ou instruções para obtê-lo);

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




- metodologia,

  
- arquitetura proposta,

  
- tecnologias utilizadas

  
- resultados obtidos.

  
- Resultados experimentais (gráficos, métricas, logs, etc.);

