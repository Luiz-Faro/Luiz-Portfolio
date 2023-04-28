# Luiz-Portfolio
Meu portfolio de Data Science

Acesse meu [repositório de projetos em data science](https://github.com/Luiz-Faro/Projetos-Data-Science)

# [Projeto 1: Clusterizando Clientes de Crédito com K-means](https://github.com/Luiz-Faro/Projetos-Data-Science/blob/main/Clustering_Kmeans-checkpoint.ipynb)

Neste projeto de clusterização de clientes de cartão de crédito, utilizei o método não supervisionado K-Means para agrupá-los com o objetivo de facilitar o desenho de estratégias focadas nesses clientes. Para entender melhor o perfil de cada cliente, fiz a clusterização e identifiquei qual é o perfil médio de dos clientes de cada cluster.

O trabalho passou pelas seguintes etapas:

Tratamento dos dados e observação das estatísticas descritivas e distribuições dos dados;
Tratamento de outliers caso necessário;
Transformação para padronização dos dados;
Clusterização com o método do cotovelo para definir o número de clusters;
Utilização de boxplots para entender os perfis dos clusters e caracterizá-los.
Foram utilizadas bibliotecas como numpy, pandas, matplotlib.pyplot, seaborn, scikit-learn. O dataset utilizado foi obtido no Kaggle e apresentou menos de 4% de valores vazios, que foram eliminados. Para o tratamento de outliers, o critério utilizado foi selecionar somente até o percentil 95 de algumas colunas.

O projeto resultou em uma matriz de correlação, que apresentou correlações positivas e negativas entre as variáveis analisadas, e boxplots que permitiram a identificação dos perfis dos clientes em cada cluster.

## Aprofundado análise do projeto (EDA)

Na etapa de EDA, foi possivel identificar a correlação das features do data set: 

![Matriz de Correlação](https://github.com/Luiz-Faro/Luiz-Portfolio/blob/main/Imagens/Matriz%20Cor.png)

Com isso destacam-se 3 features mais relevantes dado seu nível de correlação: 
> Balanço /
> Credito /
> Compras

Dessa forma o foco da análise será volto para a composição dessas features, que podem ser avalidas de maneira independente de acordo com sua frequência: 

### Balanço
![Histograma de Balanço](Imagens/Hist%20Balance.png)

### Credito
![Histograma de Crédito](Imagens/Hist%20Credit%20Limit.png)

### Compras
![Histograma de Compras](Imagens/Hist%20Purchase.png)

De uma maneira geral, os dados estão distribuidos com a maior frequencia próximas ao ponto 0 do eixo x o que pode nos auxiliar a entender qual a característica da maioria dos clientes. 

## Agrupamento dos Similares e Método do Cotovelo 

nesse contexto, o método do cotovelo é uma técnica utilizada para identificar o número ideal de clusters em uma análise de clusterização. A ideia por trás desse método é observar a relação entre a variância explicada e o número de clusters utilizados na análise.

No código em questão, após realizar a transformação dos dados para padronização, é realizada a clusterização utilizando o método K-Means com um loop que varia o número de clusters de 1 a 10. Em cada iteração, é calculada a distorção média ao quadrado (MSE) de cada cluster, que representa a distância média entre os pontos do cluster e o seu centroide.

Em seguida, é criado um gráfico de linha mostrando a relação entre o número de clusters e a distorção média ao quadrado. O ponto de inflexão na curva é conhecido como "cotovelo" e indica o número ideal de clusters para a análise.

No case em questão, podemos observar que o número ideal de clusters é 4, pois após esse ponto o ganho de informação é relativamente pequeno em comparação com o número de clusters adicionais utilizados. Esse resultado pode ser observado visualmente na figura gerada pelo código.

![Método de cotovelos](Imagens/Cotovelo%20K%20means.png)

Assim, o método do cotovelo é uma técnica importante para auxiliar na escolha do número ideal de clusters, permitindo uma análise mais precisa e significativa dos dados.

## Identificação dos Clusters

Com base na análise realizada usando o método do cotovelo para identificar o número ideal de clusters, podemos concluir que existem 4 grupos distintos de clientes com base em suas compras em nossa loja virtual.

### Balanço
![Cluster Balanço](Imagens/Clusters%20Balance.png)

### Crédito
![Cluster Crédito](Imagens/Clusters%20Credit%20Limit.png)

### Compras
![Cluster Compras](Imagens/Clusters%20Purchase.png)

Ao analisar os clusters e as descrições de cada variável, identificamos diferenças entre as populações em algumas variáveis, o que nos permite criar 4 perfis distintos. É importante observar que há presença de outliers quando comparamos entre os clusters.

Os 4 perfis identificados são:

Cliente Contido (Cluster 0): Não realiza compras em grandes valores, quantidades ou pagamento antecipado.

Cliente Comprador (Cluster 1): Realiza compras em grandes valores e quantidades, porém não realiza pagamento antecipado.

Cliente em Ascensão (Cluster 2): Está começando a aumentar suas compras, porém ainda realiza compras em quantidades normais e não realiza pagamento antecipado.

Cliente Não Devedor (Cluster 3): Similar ao Cliente Contido, porém realiza pagamento antecipado em todas as suas compras.

Essa descrição é útil em áreas não técnicas, como atendimento ao cliente, marketing, vendas e financeiro, pois fornece detalhes relevantes sobre a população que podem ser úteis para o negócio, sem a necessidade de analisar todas as contas individualmente

