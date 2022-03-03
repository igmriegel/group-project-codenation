# Objetivo do projeto:
## Gerar leads de possiveis clientes com os dados passados

### Contextualização
Algumas empresas gostariam de saber quem são as demais empresas em um determinado mercado (população) que tem maior probabilidade se tornarem seus próximos clientes. Ou seja, a sua solução deve encontrar no mercado quem são os leads mais aderentes dado as características dos clientes presentes no portfólio do usuário.

Além disso, sua solução deve ser agnóstica ao usuário. Qualquer usuário com uma lista de clientes que queira explorar esse mercado pode extrair valor do serviço.

Para o desafio, deverão ser consideradas as seguintes bases:

Mercado: Base com informações sobre as empresas do Mercado a ser considerado. Portfolio 1: Ids dos clientes da empresa 1 Portfolio 2: Ids dos clientes da empresa 2 Portfolio 3: Ids dos clientes da empresa 3

Obs: todas as empresas(ids) dos portfolios estão contidos no Mercado(base de população).


Os datasets devem ser colocados neste 

```
  /arquivos_de_dados/
```

Arquivos do projeto:
#### Link para download das bases Mercado, Portfolio 1, Portfolio 2 e Portfolio 3 respectivamente:

https://codenation-challenges.s3-us-west-1.amazonaws.com/ml-leads/estaticos_market.csv.zip
https://codenation-challenges.s3-us-west-1.amazonaws.com/ml-leads/estaticos_portfolio1.csv
https://codenation-challenges.s3-us-west-1.amazonaws.com/ml-leads/estaticos_portfolio2.csv
https://codenation-challenges.s3-us-west-1.amazonaws.com/ml-leads/estaticos_portfolio3.csv

#### Descrição das colunas dos datasets market e portfolio1:
https://s3-us-west-1.amazonaws.com/codenation-challenges/ml-leads/features_dictionary.pdf


## Clusterização
Um dos grandes desafios do projeto foi determinar o algoritmo que mais se encaixava no o agrupamento de dados, visando identificar valores anômalos ou outliers, assim nos deparamos com alguns algoritmos de clusterização como K-Means, PAM, CLARA e DBSCAN.

Dado um conjunto de dados, estes algoritmos criam uma classificação de acordo com as métricas agrupando em clusters (agrupamentos). Durante nossa análise, escolhemos o algoritmo K-Means. Sua escolha está atrelada à vários motivos, e vamos mencionar alguns deles a seguir.

Já de inicio podemos citar a sua implementação relativamente simples, se comparado à ouros algoritmos como o PAM, CLARA e DBSCAN. Ele também trabalha muito bem com grandes conjuntos de dados, e sua densidade de variáveis dos pontos de dados não afetam seu algoritmo de agrupamento, assim o K-Means casou muito bem com o tipo e número de amostra que tínhamos para desenvolver nosso modelo.

O algoritmo PAM é um algoritmo de agrupamento muito similar ao algoritmo K -Means, pois ambos possuem o foco em trabalhar na divisão de um conjunto de dados em grupos, minimizando a distância entre os pontos rotulados em um cluster e outro ponto rotulado como o centro desse cluster. Um ponto relevante é que preferimos optar por uma abordagem de clusterização considerando a soma de distâncias euclidianas quadráticas entre os pontos. Sendo assim, seguimos com o K-Means, descartando o algoritmo PAM, já que, diferente do K-Means, seu método de trabalho busca minimiza a formação de pares de dados não similares. Seguindo a lógica, também descartamos utilizar o algoritmo CLARA, pois ele é uma extensão do método de clustering do PAM, porém com melhorias para grandes conjuntos de dados.

Continuando nossa análise dos algoritmos, enquanto no DBSCAN o número de clusters não precisa ser especificado, a definição de clusters no K-Means afeta diretamente os agrupamentos, ponto que também influenciou adotar este algoritmo em nossa abordagem, pois assim é possível evitar problemas com número de ruídos que podem ser gerados na nossa análise dos portfólios, pois uma análise com muitos ruídos poderia comprometer a nossa recomendação de leads para o cliente.

Assim, foi possível perceber que o algoritmo que mais se encaixava em nossa abordagem de desenvolvimento do modelo foi o K-Means, pois atendeu muito bem o objetivo de encontrar similaridades entre os dados e agrupá-los conforme o número de clusters passado pelo argumento k. Este algoritmo utiliza um método simples e eficiente baseado no conceito de distância, e fornece uma classificação de informações de acordo com os próprios dados, baseada em análise e comparações entre os valores numéricos. Desta maneira, o algoritmo vai fornecer uma classificação automática sem a necessidade de nenhuma supervisão humana, ou seja, sem nenhuma pré-classificação existente. De forma iterativa, ele atribui os pontos de dados ao grupo que representa a menor distância, ou seja, ao grupo de dados que seja mais similar. O objetivo é encontrar um padrão e assumir que esse padrão é o que estamos tentando ensinar ao computador, que por sua vez, vai reproduzir e encontrar esse padrão sempre quando for solicitado. Depois de descoberto o padrão, qualquer item novo que tenha uma similaridade com aquele segmento (agrupamento – cluster) fará parte daquele grupo.

### Referências
- https://acervolima.com/diferenca-entre-k-means-e-dbscan-clustering/
- https://medium.com/@gabriel.stankevix/segmenta%C3%A7%C3%A3o-em-r-kmeans-pam-clara-e-dbscan-37b47baf3922
- https://medium.com/pizzadedados/kmeans-e-metodo-do-cotovelo-94ded9fdf3a9
- https://medium.com/programadores-ajudando-programadores/k-means-o-que-%C3%A9-como-funciona-aplica%C3%A7%C3%B5es-e-exemplo-em-python-6021df6e2572
- https://ichi.pro/pt/qual-e-a-diferenca-entre-k-vizinhos-mais-proximos-e-agrupamento-de-k-medias-36508279026525
- https://aprenderdatascience.com/k-means-clustering-agrupamento-k-means/
- https://www.alura.com.br/conteudo/clustering-dados-sem-classificacao
- https://docero.com.br/doc/s8csvx8