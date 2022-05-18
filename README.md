# Estudo Introdutório à Recomendações e ao Algoritmo K-Nearest Neighbors

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)

## Objetivo

Estudo realizado como introdução às metodologias para a recomendação de dez filmes a um determinado usuário, sabendo ou não seus gostos e informações.
O dataset utilizado para estudo pode ser encontrado em  https://grouplens.org/datasets/movielens/latest/ **ml-latest.zip(size:265 MB)**.

Este estudo foi realizado orientado pelos seguintes passos:

## 1º - Compreender os dados presentes no dataset
Foi utilizado o Pandas para transformar os arquivos *movies.csv* e *ratings.csv* em dataframes, ajudando a realizar uma primeira análise para conhecer o conteúdo de ambos os arquivos (Id dos filmes, ID dos usuários, títulos dos filmes por ID, avaliações de cada usuário), além de descrições estatísticas a respeito das avaliações dadas e o número de IDs de usuários presentes no dataset.

## 2º - Primeira tentativa de recomendação
Métodos do pandas foram utilizados para realizar alterções no dataframe *ratings*, como a criação de duas colunas que contabilizavam o número total de avaliações e a média de avaliações de cada filme. Também conseguimos extrair informações para sabermos quais são os filmes com o maior número de avaliações recebidas no dataset, recomendado os dez primeiros ao usuário, acreditando que estes seriam os dez filmes mais populares.<br>
Com o método sort_values() aplicado na coluna das médias de avaliações, conseguimos ordenar o dataframe para indicar os dez filmes mais **bem avaliados** do dataset, utilizando uma query para filtrar um número mínimo de recomendações, evitando que filmes com baixa relevância, porém altas avaliações, chegassem ao usuário.

## 3º - Recomendações por similaridade de gênero
Nesta etapa do estudo, foram atribuidos diversos IDs de filmes à uma lista, contendo filmes que teriam sido assistidos pelo usuário que gostaríamos de recomendar filmes. Mais uma vez, realizamos uma query para buscar filmes cuja coluna de gêneros fosse preenchida da mesma forma que a coluna de gêneros do último filme assistido pelo usuário e, também, tais filmes foram ordenados pela média de avaliações, de forma decrescente, seguindo como filtro o requisito de, no mínimo, 1.000 recomendações.

## 4º - Cálculo da distância euclidiana
Na quarta etapa do estudo, foi estudado o conceito de distância euclidiana, demonstrando em um gráfico as diferentes avaliações de três personagens fictícios criados apenas para estudo e o uso do método *linal.norm* da biblioteca Numpy para realizar o cálculo da distância euclidiana entre eles. Descobrindo quais personagens tinham a menor distância entre si, foi possível concluir que ambos apresentavam um relativo grau de similaridade em relação aos seus gostos e que faria sentido recomendar filmes que um avaliasse positivamente para o outro que ainda não houvesse assistido tais filmes.
Na parte final desta etapa, foram criadas funções para extrair as avaliações e os IDs dos filmes avaliados de acordo com o ID informado de determinado usuário, por fim, pudemos calcular a distância euclidiana entre dois usuários do dataset em estudo.

## 5º - Algoritmo K-Nearest Neighbors
Na quinta etapa do estudo, foi realizada uma breve introdução a respeito do algoritmo K-nearest neighbors e de seu funcionamento para realizar classificações de acordo com dados próximos daquele que desejamos classificar. 
Por fim, os conceitos da distância euclidiana forma aplicados à funções que buscavam repetir o funcionamento do algoritmo K-nearest neighbors, realizando uma recomendação de filmes a um determinado usuário informado e buscando, no dataset, quais seriam os 10 usuários vizinhos mais próximos, de acordo com suas avaliações e gostos, para realizar a recomendação de mais 10 filmes ordenados pela avaliação média dos usuários vizinhos mais próximos e utilizando como filtro o requisito de que tal filme deveria ter sido avaliado por pelo menos metade dos k-vizinhos mais próximos informados como parâmetro na execução da função.

# Conclusão 
Visando realizar uma introdução ao tema das recomendações ao usuário, este estudo serviu para identificar formas simples de se produzir uma lista de recomendações através de informações contidas dentro do dataset.
Inicialmente, sem uso de conceitos muito complexos, o dataset foi organizado de forma a recomendar simplesmente os filmes mais avaliados, ou com maiores médias de avaliações desde que tivessem um determinado número mínimo de avaliações.
Posteriormente, foi possível abordar conceitos matemáticos como o da distâcnia euclidiana e seu funcionamento em algoritmos de **machine learning**, como **k-nearest neighbor**, presente na biblioteca **scikit-learn**. Construímos um algoritmo KNN absolutamente do zero, apenas através de definições de funções e sem o uso de bibliotecas importadas para tal, visando expandir o entendimento acerca do funcionamento deste algoritmo, amplamente utilizado para classificações, e como seu uso pode ser relevante para identificar gostos similares entre usuários de um dataset e realizar recomendações através do cálculo da distância entre tais usuários.

--

Bibliotecas utilizados
> - Pandas
> - Numpy
> - Matplotlib
