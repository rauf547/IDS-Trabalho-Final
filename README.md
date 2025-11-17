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

### Seleção de Features utilizando Threshold = "median"

Número original de features: 191
Número de features selecionadas: 96

Top Features Selecionadas (baseado no threshold da Mediana):
['dur', 'spkts', 'dpkts', 'sbytes', 'dbytes', 'rate', 'sttl', 'dttl', 'sload', 'dload', 'sloss', 'dloss', 'sinpkt', 'dinpkt', 'sjit', 'djit', 'swin', 'stcpb', 'dtcpb', 'dwin', 'tcprtt', 'synack', 'ackdat', 'smean', 'dmean', 'trans_depth', 'response_body_len', 'ct_srv_src', 'ct_state_ttl', 'ct_dst_ltm', 'ct_src_dport_ltm', 'ct_dst_sport_ltm', 'ct_dst_src_ltm', 'is_ftp_login', 'ct_ftp_cmd', 'ct_flw_http_mthd', 'ct_src_ltm', 'ct_srv_dst', 'is_sm_ips_ports', 'proto_a/n', 'proto_any', 'proto_argus', 'proto_arp', 'proto_cbt', 'proto_chaos', 'proto_dcn', 'proto_ddp', 'proto_egp', 'proto_gre', 'proto_i-nlsp', 'proto_icmp', 'proto_igmp', 'proto_igp', 'proto_ip', 'proto_ipv6', 'proto_ipv6-frag', 'proto_kryptolan', 'proto_mobile', 'proto_mux', 'proto_netblt', 'proto_ospf', 'proto_pim', 'proto_pup', 'proto_rtp', 'proto_rvd', 'proto_sctp', 'proto_sep', 'proto_st2', 'proto_sun-nd', 'proto_swipe', 'proto_tcp', 'proto_tp++', 'proto_trunk-2', 'proto_udp', 'proto_unas', 'proto_vrrp', 'service_dhcp', 'service_dns', 'service_ftp', 'service_ftp-data', 'service_http', 'service_irc', 'service_pop3', 'service_radius', 'service_smtp', 'service_snmp', 'service_ssh', 'service_ssl', 'state_ECO', 'state_FIN', 'state_INT', 'state_PAR', 'state_REQ', 'state_RST', 'state_URN', 'state_no']


### Seleção de Features utilizando Threshold = "mean"

Número original de features: 191\
Número de features selecionadas: 34

Top Features Selecionadas (baseado no threshold da Mediana):
['dur', 'spkts', 'dpkts', 'sbytes', 'dbytes', 'rate', 'sttl', 'dttl', 'sload', 'dload', 'sloss', 'dloss', 'sinpkt', 'dinpkt', 'sjit', 'djit', 'swin', 'stcpb', 'dtcpb', 'tcprtt', 'synack', 'ackdat', 'smean', 'dmean', 'ct_srv_src', 'ct_state_ttl', 'ct_dst_ltm', 'ct_src_dport_ltm', 'ct_dst_sport_ltm', 'ct_dst_src_ltm', 'ct_src_ltm', 'ct_srv_dst', 'proto_arp', 'state_INT']



### Resultados KNN 96 FEATURES

--- Relatório de Classificação k-NN com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.95 |   0.70 |     0.81 |   37000 |
| Ataque (1)   |      0.80 |   0.97 |     0.88 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.85 |   82332 |
| macro avg    |      0.88 |   0.84 |     0.84 |   82332 |
| weighted avg |      0.87 |   0.85 |     0.85 |   82332 |

--- Matriz de Confusão ---\
[[25848 11152]\
 [ 1244 44088]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 97.26%\
Falso Negativo (FN - Ataque perdido): 2.74%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 69.86%\
Falso Positivo (FP - Alarme falso): 30.14%



--- Relatório de Classificação k-NN com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.93 |   0.76 |     0.84 |   37000 |
| Ataque (1)   |      0.83 |   0.96 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.87 |   82332 |
| macro avg    |      0.88 |   0.86 |     0.86 |   82332 |
| weighted avg |      0.87 |   0.87 |     0.86 |   82332 |

--- Matriz de Confusão ---\
[[28013  8987]\
 [ 2036 43296]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 95.51%\
Falso Negativo (FN - Ataque perdido): 4.49%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 75.71%\
Falso Positivo (FP - Alarme falso): 24.29%



--- Relatório de Classificação k-NN com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.91 |   0.82 |     0.86 |   37000 |
| Ataque (1)   |      0.87 |   0.93 |     0.90 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.88 |   82332 |
| macro avg    |      0.89 |   0.88 |     0.88 |   82332 |
| weighted avg |      0.89 |   0.88 |     0.88 |   82332 |

--- Matriz de Confusão ---\
[[30417  6583]\
 [ 3040 42292]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 93.29%\
Falso Negativo (FN - Ataque perdido): 6.71%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 82.21%\
Falso Positivo (FP - Alarme falso): 17.79%



--- Relatório de Classificação k-NN com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.88 |   0.88 |     0.88 |   37000 |
| Ataque (1)   |      0.90 |   0.91 |     0.90 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.89 |   82332 |
| macro avg    |      0.89 |   0.89 |     0.89 |   82332 |
| weighted avg |      0.89 |   0.89 |     0.89 |   82332 |

--- Matriz de Confusão ---\
[[32588  4412]\
 [ 4275 41057]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 90.57%\
Falso Negativo (FN - Ataque perdido): 9.43%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 88.08%\
Falso Positivo (FP - Alarme falso): 11.92%


--- Relatório de Classificação k-NN com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.86 |   0.94 |     0.90 |   37000 |
| Ataque (1)   |      0.94 |   0.87 |     0.91 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.90 |   82332 |
| macro avg    |      0.90 |   0.90 |     0.90 |   82332 |
| weighted avg |      0.81 |   0.90 |     0.90 |   82332 |

--- Matriz de Confusão ---\
[[34614  2386]\
 [ 5701 39631]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 87.42%\
Falso Negativo (FN - Ataque perdido): 12.58%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 93.55%\
Falso Positivo (FP - Alarme falso): 6.45%

------------------------------------------------------------------

### Resultados KNN 34 FEATURES

--- Relatório de Classificação k-NN com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.92 |   0.65 |     0.76 |   37000 |
| Ataque (1)   |      0.77 |   0.95 |     0.85 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.82 |   82332 |
| macro avg    |      0.85 |   0.80 |     0.81 |   82332 |
| weighted avg |      0.84 |   0.82 |     0.81 |   82332 |

--- Matriz de Confusão ---\
[[24068 12932]\
 [ 2071 43261]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 95.43%\
Falso Negativo (FN - Ataque perdido): 4.57%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 65.05%\
Falso Positivo (FP - Alarme falso): 34.95%


--- Relatório de Classificação k-NN com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.87 |   0.72 |     0.79 |   37000 |
| Ataque (1)   |      0.80 |   0.91 |     0.85 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.84 |   0.82 |     0.82 |   82332 |
| weighted avg |      0.83 |   0.83 |     0.82 |   82332 |

--- Matriz de Confusão ---\
[[26680 10320]\
 [ 3888 41444]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 91.42%\
Falso Negativo (FN - Ataque perdido): 8.58%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 72.11%\
Falso Positivo (FP - Alarme falso): 27.89%


--- Relatório de Classificação k-NN com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.85 |   0.77 |     0.81 |   37000 |
| Ataque (1)   |      0.82 |   0.89 |     0.86 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.84 |   0.83 |     0.83 |   82332 |
| weighted avg |      0.84 |   0.83 |     0.83 |   82332 |

--- Matriz de Confusão ---\
[[28432  8568]\
 [ 5068 40264]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 88.82%\
Falso Negativo (FN - Ataque perdido): 11.18%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 76.84%\
Falso Positivo (FP - Alarme falso): 23.16%


--- Relatório de Classificação k-NN com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.79 |   0.87 |     0.83 |   37000 |
| Ataque (1)   |      0.88 |   0.82 |     0.85 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.84 |   82332 |
| macro avg    |      0.84 |   0.84 |     0.84 |   82332 |
| weighted avg |      0.84 |   0.84 |     0.84 |   82332 |


--- Matriz de Confusão ---\
[[32106  4894]\
 [ 8302 37030]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 81.69%\
Falso Negativo (FN - Ataque perdido): 18.31%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 86.77%\
Falso Positivo (FP - Alarme falso): 13.23%


--- Relatório de Classificação k-NN com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.74 |   0.95 |     0.83 |   37000 |
| Ataque (1)   |      0.95 |   0.73 |     0.82 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.84 |   0.84 |     0.83 |   82332 |
| weighted avg |      0.85 |   0.83 |     0.83 |   82332 |

--- Matriz de Confusão ---\
[[35194  1806]\
 [12342 32990]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 72.77%\
Falso Negativo (FN - Ataque perdido): 27.23%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 95.12%\
Falso Positivo (FP - Alarme falso): 4.88%



------------------------------------------------------------------

### Resultados MLP 96 FEATURES

--- Relatório de Classificação MLP com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.98 |   0.71 |     0.82 |   37000 |
| Ataque (1)   |      0.80 |   0.99 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.86 |   82332 |
| macro avg    |      0.89 |   0.85 |     0.85 |   82332 |
| weighted avg |      0.88 |   0.86 |     0.86 |   82332 |

--- Matriz de Confusão ---\
[[26143 10857]\
 [  662 44670]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 98.54%\
Falso Negativo (FN - Ataque perdido): 1.46%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 70.66%\
Falso Positivo (FP - Alarme falso): 29.34%


--- Relatório de Classificação MLP com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.96 |   0.77 |     0.85 |   37000 |
| Ataque (1)   |      0.84 |   0.97 |     0.90 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.88 |   82332 |
| macro avg    |      0.90 |   0.87 |     0.88 |   82332 |
| weighted avg |      0.89 |   0.88 |     0.88 |   82332 |

--- Matriz de Confusão ---\
[[28353  8647]\
 [ 1183 44149]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 97.39%\
Falso Negativo (FN - Ataque perdido): 2.61%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 76.63%\
Falso Positivo (FP - Alarme falso): 23.37%


--- Relatório de Classificação MLP com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.94 |   0.83 |     0.88 |   37000 |
| Ataque (1)   |      0.87 |   0.96 |     0.91 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.90 |   82332 |
| macro avg    |      0.91 |   0.89 |     0.90 |   82332 |
| weighted avg |      0.90 |   0.90 |     0.90 |   82332 |

--- Matriz de Confusão ---\
[[30632  6368]\
 [ 1903 43429]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 95.80%\
Falso Negativo (FN - Ataque perdido): 4.20%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 82.79%\
Falso Positivo (FP - Alarme falso): 17.21%


--- Relatório de Classificação MLP com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.91 |   0.89 |     0.90 |   37000 |
| Ataque (1)   |      0.91 |   0.93 |     0.92 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.91 |   82332 |
| macro avg    |      0.91 |   0.91 |     0.91 |   82332 |
| weighted avg |      0.91 |   0.91 |     0.91 |   82332 |

--- Matriz de Confusão ---\
[[32871  4129]\
 [ 3084 42248]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 93.20%\
Falso Negativo (FN - Ataque perdido): 6.80%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 88.84%\
Falso Positivo (FP - Alarme falso): 11.16%


--- Relatório de Classificação MLP com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.87 |   0.95 |     0.91 |   37000 |
| Ataque (1)   |      0.95 |   0.89 |     0.92 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.91 |   82332 |
| macro avg    |      0.91 |   0.92 |     0.91 |   82332 |
| weighted avg |      0.92 |   0.91 |     0.91 |   82332 |

--- Matriz de Confusão ---\
[[35060  1940]\
 [ 5120 40212]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 88.71%\
Falso Negativo (FN - Ataque perdido): 11.29%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 94.76%\
Falso Positivo (FP - Alarme falso): 5.24%

------------------------------------------------------------------

### Resultados MLP 34 FEATURES

--- Relatório de Classificação MLP com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.96 |   0.69 |     0.80 |   37000 |
| Ataque (1)   |      0.79 |   0.98 |     0.88 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.85 |   82332 |
| macro avg    |      0.88 |   0.83 |     0.84 |   82332 |
| weighted avg |      0.87 |   0.85 |     0.84 |   82332 |

--- Matriz de Confusão ---\
[[25533 11467]\
 [ 1011 44321]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 97.77%\
Falso Negativo (FN - Ataque perdido): 2.23%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 69.01%\
Falso Positivo (FP - Alarme falso): 30.99%


--- Relatório de Classificação MLP com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.94 |   0.76 |     0.84 |   37000 |
| Ataque (1)   |      0.83 |   0.96 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.87 |   82332 |
| macro avg    |      0.88 |   0.86 |     0.86 |   82332 |
| weighted avg |      0.88 |   0.87 |     0.87 |   82332 |

--- Matriz de Confusão ---\
[[27942  9058]\
 [ 1851 43481]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 95.92%\
Falso Negativo (FN - Ataque perdido): 4.08%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 75.52%\
Falso Positivo (FP - Alarme falso): 24.48%



--- Relatório de Classificação MLP com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.91 |   0.82 |     0.86 |   37000 |
| Ataque (1)   |      0.87 |   0.94 |     0.90 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.88 |   82332 |
| macro avg    |      0.89 |   0.88 |     0.88 |   82332 |
| weighted avg |      0.89 |   0.88 |     0.88 |   82332 |

--- Matriz de Confusão ---\
[[30395  6605]\
 [ 2907 42425]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 93.59%\
Falso Negativo (FN - Ataque perdido): 6.41%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 82.15%\
Falso Positivo (FP - Alarme falso): 17.85%


--- Relatório de Classificação MLP com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.88 |   0.88 |     0.80 |   37000 |
| Ataque (1)   |      0.90 |   0.90 |     0.90 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.89 |   82332 |
| macro avg    |      0.89 |   0.89 |     0.89 |   82332 |
| weighted avg |      0.89 |   0.89 |     0.89 |   82332 |

--- Matriz de Confusão ---\
[[32444  4556]\
 [ 4346 40986]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 90.41%\
Falso Negativo (FN - Ataque perdido): 9.59%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 87.69%\
Falso Positivo (FP - Alarme falso): 12.31%


--- Relatório de Classificação MLP com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.83 |   0.94 |     0.88 |   37000 |
| Ataque (1)   |      0.95 |   0.84 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.89 |   82332 |
| macro avg    |      0.89 |   0.89 |     0.89 |   82332 |
| weighted avg |      0.89 |   0.89 |     0.89 |   82332 |

--- Matriz de Confusão ---\
[[34853  2147]\
 [ 7131 38201]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 84.27%\
Falso Negativo (FN - Ataque perdido): 15.73%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 94.20%\
Falso Positivo (FP - Alarme falso): 5.80%


-----------------------------------------------------------------

### Resultados SVM 96 FEATURES

--- Relatório de Classificação SVM com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.95 |   0.68 |     0.80 |   37000 |
| Ataque (1)   |      0.79 |   0.97 |     0.87 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.84 |   82332 |
| macro avg    |      0.87 |   0.83 |     0.83 |   82332 |
| weighted avg |      0.86 |   0.84 |     0.84 |   82332 |

--- Matriz de Confusão ---\
[[25284 11716]\
 [ 1301 44031]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 97.13%\
Falso Negativo (FN - Ataque perdido): 2.87%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 68.34%\
Falso Positivo (FP - Alarme falso): 31.66%


--- Relatório de Classificação SVM com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.95 |   0.71 |     0.81 |   37000 |
| Ataque (1)   |      0.80 |   0.97 |     0.88 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.85 |   82332 |
| macro avg    |      0.87 |   0.84 |     0.84 |   82332 |
| weighted avg |      0.87 |   0.85 |     0.85 |   82332 |

--- Matriz de Confusão ---\
[[26198 10802]\
 [ 1504 43828]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 96.68%\
Falso Negativo (FN - Ataque perdido): 3.32%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 70.81%\
Falso Positivo (FP - Alarme falso): 29.19%


--- Relatório de Classificação SVM com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.94 |   0.74 |     0.83 |   37000 |
| Ataque (1)   |      0.82 |   0.96 |     0.88 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.86 |   82332 |
| macro avg    |      0.88 |   0.85 |     0.85 |   82332 |
| weighted avg |      0.87 |   0.86 |     0.86 |   82332 |

--- Matriz de Confusão ---\
[[27279  9721]\
 [ 1797 43535]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 96.04%\
Falso Negativo (FN - Ataque perdido): 3.96%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 73.73%\
Falso Positivo (FP - Alarme falso): 26.27%


--- Relatório de Classificação SVM com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.93 |   0.77 |     0.84 |   37000 |
| Ataque (1)   |      0.84 |   0.95 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.87 |   82332 |
| macro avg    |      0.88 |   0.86 |     0.87 |   82332 |
| weighted avg |      0.88 |   0.87 |     0.87 |   82332 |

--- Matriz de Confusão ---\
[[28497  8503]\
 [ 2219 43113]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 95.11%\
Falso Negativo (FN - Ataque perdido): 4.89%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 77.02%\
Falso Positivo (FP - Alarme falso): 22.98%


--- Relatório de Classificação SVM com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.88 |   0.82 |     0.85 |   37000 |
| Ataque (1)   |      0.86 |   0.91 |     0.89 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.87 |   82332 |
| macro avg    |      0.87 |   0.87 |     0.87 |   82332 |
| weighted avg |      0.87 |   0.87 |     0.87 |   82332 |

--- Matriz de Confusão ---\
[[30463  6537]\
 [ 3965 41367]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 91.25%\
Falso Negativo (FN - Ataque perdido): 8.75%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 82.33%\
Falso Positivo (FP - Alarme falso): 17.67%

---------------------------------------------------------------

### Resultados SVM 34 FEATURES

--- Relatório de Classificação SVM com Limiar = 0.5 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.91 |   0.68 |     0.78 |   37000 |
| Ataque (1)   |      0.78 |   0.95 |     0.86 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.85 |   0.81 |     0.82 |   82332 |
| weighted avg |      0.84 |   0.83 |     0.82 |   82332 |

--- Matriz de Confusão ---\
[[25231 11769]\
 [ 2377 42955]]\
 
--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 94.76%\
Falso Negativo (FN - Ataque perdido): 5.24%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 68.19%\
Falso Positivo (FP - Alarme falso): 31.81%


--- Relatório de Classificação SVM com Limiar = 0.6 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.90 |   0.71 |     0.79 |   37000 |
| Ataque (1)   |      0.80 |   0.93 |     0.86 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.85 |   0.82 |     0.83 |   82332 |
| weighted avg |      0.84 |   0.83 |     0.83 |   82332 |

--- Matriz de Confusão ---\
[[26258 10742]\
 [ 3026 42306]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 93.32%\
Falso Negativo (FN - Ataque perdido): 6.68%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 70.97%\
Falso Positivo (FP - Alarme falso): 29.03%

--- Relatório de Classificação SVM com Limiar = 0.7 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.87 |   0.74 |     0.80 |   37000 |
| Ataque (1)   |      0.81 |   0.91 |     0.86 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.84 |   82332 |
| macro avg    |      0.84 |   0.83 |     0.83 |   82332 |
| weighted avg |      0.84 |   0.84 |     0.83 |   82332 |

--- Matriz de Confusão ---\
[[27477  9523]\
 [ 3998 41334]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 91.18%\
Falso Negativo (FN - Ataque perdido): 8.82%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 74.26%\
Falso Positivo (FP - Alarme falso): 25.74%


--- Relatório de Classificação SVM com Limiar = 0.8 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.85 |   0.79 |     0.82 |   37000 |
| Ataque (1)   |      0.84 |   0.88 |     0.86 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.84 |   82332 |
| macro avg    |      0.84 |   0.84 |     0.84 |   82332 |
| weighted avg |      0.84 |   0.84 |     0.84 |   82332 |

--- Matriz de Confusão ---\
[[29138  7862]\
 [ 5322 40010]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 88.26%\
Falso Negativo (FN - Ataque perdido): 11.74%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 78.75%\
Falso Positivo (FP - Alarme falso): 21.25%


--- Relatório de Classificação SVM com Limiar = 0.9 ---
|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| Normal (0)   |      0.78 |   0.87 |     0.82 |   37000 |
| Ataque (1)   |      0.89 |   0.80 |     0.84 |   45332 |
| ------------ | --------- | ------ | -------- | ------- |
| accuracy     |           |        |     0.83 |   82332 |
| macro avg    |      0.83 |   0.84 |     0.83 |   82332 |
| weighted avg |      0.84 |   0.83 |     0.83 |   82332 |

--- Matriz de Confusão ---\
[[32287  4713]\
 [ 8991 36341]]

--- Métricas da Matriz de Confusão (em Porcentagem) ---\
Verdadeiro Positivo (VP - Ataque detectado corretamente): 80.17%\
Falso Negativo (FN - Ataque perdido): 19.83%\
Verdadeiro Negativo (VN - Normal detectado corretamente): 87.26%\
Falso Positivo (FP - Alarme falso): 12.74%



