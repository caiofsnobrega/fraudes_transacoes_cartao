# Detecção de Fraudes em Cartão de Crédito com Aprendizado de Máquina

*[Click here for the English version](README-en.md)*

Este projeto foi desenvolvido como **Trabalho de Conclusão de Curso** da **EBAC** (Escola Britânica de Artes Criativas e Tecnologia). 

Durante o desenvolvimento — especialmente em etapas como ajustes finos e resolução de gargalos no computador (como o travamento do algoritmo de inteligência artificial SVM) —, utilizei ferramentas de IA para encontrar caminhos mais rápidos e aplicar as melhores práticas de programação.

---

### O Problema que este Projeto Resolve

O objetivo é criar um sistema inteligente capaz de **identificar compras fraudulentas em um cartão de crédito em tempo real**, permitindo que o banco bloqueie a transação suspeita antes que o prejuízo aconteça. 

Tudo isso mantendo um equilíbrio delicado: **bloquear a fraude sem atrapalhar a vida do cliente** (evitando o estresse de ter uma compra legítima recusada por engano).

---

### Como o Projeto foi Realizado

Para resolver esse problema, o projeto seguiu quatro etapas principais:

* **Organização dos dados:** Os dados foram divididos de forma equilibrada entre "treino" (para o sistema aprender) e "teste" (para provar que ele funciona na prática), garantindo que a proporção real de fraudes fosse respeitada.
* **Padronização:** Informações como o *horário* e o *valor* da compra passaram por um ajuste matemático para que números muito altos ou fora do padrão não confundissem o sistema.
* **Correção do desequilíbrio:** Como a imensa maioria das compras do dia a dia são verdadeiras e as fraudes são raras, o sistema usou uma técnica especial (chamada SMOTE) para criar novas amostras de fraudes de forma controlada. Isso ajudou o algoritmo a enxergar melhor o que é um golpe, sem inchar o tamanho do banco de dados.
* **Ajuste fino (Otimização):** O sistema testou centenas de combinações de configurações matemáticas automaticamente para descobrir qual delas era a mais rápida e precisa.

---

### Os Modelos Testados e Quem Venceu

Os modelos foram colocados à prova simulando a vida real (com dados desbalanceados):

* **XGBoost (O Grande Vencedor):** Foi o que apresentou o melhor resultado geral. Conseguiu acertar **83% das vezes quando dizia que era fraude** (Precisão) e conseguiu **pegar 87% de todas as fraudes que realmente aconteceram** (Recall).
* **Regressão Logística:** Conseguiu identificar a maioria das fraudes (89% de Recall), mas disparava muitos alarmes falsos — bloqueando o cartão em transações legítimas (apenas 20% de precisão).
* **SVM Linear:** Teve um desempenho prejudicado porque o processamento ficou muito pesado e precisou ser interrompido antes de terminar todos os testes.

#### Ajuste final de segurança
Para proteger ainda mais o cliente, o **XGBoost** passou por um "filtro de sensibilidade": o nível de exigência para o sistema identificar uma fraude foi aumentado. Com isso, a precisão saltou para **90%**, garantindo que poucos clientes inocentes tivessem o cartão bloqueado por engano, mantendo uma taxa de detecção de fraudes de **84%**.


* * *

### Arquivos Gerados para Produção

Após o término do script, para simular um cenário real em que o modelo seria colocado em produção, gerei três arquivos para serem carregados:

*   `modelo_xgb.pkl`: modelo ajustado;
*   `robust_scaler.pkl`: arquivo da normalização;
*   `threshold_calibrado.pkl`: o ponto de corte ideal definido.

* * *

### Visualizações Geradas em Destaque

![Curva Precision-Recall](images_fraud/curva_pr.png)

![Distribuições dos Valores de Transações por Classes](images_fraud/boxplot_amount_class.png)

![Importância de Variáveis](images_fraud/importancia_variaveis.png)

*Nota: Este projeto foi desenvolvido para fins acadêmicos e de portfólio profissional.*
