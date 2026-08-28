# Quantidade de Posts vs Total de Likes nos Posts com as Hashtags

## Pergunta

> É verdade que quanto maior a quantidade de vídeos postados com essa hashtag, maior é a quantidade de likes total nos vídeos usando essa hashtag?

## Dados

**Fonte:** exportação do TikTok via Zeeschuimer

**Período coletado:** de 13 de dezembro de 2020 até o dia 19 de agosto de 2026 

**Tamanho da amostra:** 1044 posts

**Limites conhecidos da coleta:** Tiktok, termos de pesquisa relacionados a empresa júnior, marketing e etc.

## Método

Descreva o que foi calculado e como, incluindo toda decisão de tratamento (duplicatas removidas, denominador usado na taxa de engajamento, corte de linhas com denominador zero). Se usou uma fórmula, escreva a fórmula.
Primeiramente removi as duplicatas para evitar métricas duplicadas e posteriorimente deixei apenas os vídeos que estavam com a visualização válida, garantindo que esses vídeos estão em ciruculação na plataforma. Em seguida selecionei as variáveis que mais faziam sentido para a criação do meu gráfico e deixei apenas elas em um csv de resumo das hashtags. A variável "hashtags" é o nome das hashtags. A variável qtd_posts mede a quantidade total de posts que usaram aquela hashtag e a variável likes_total mede o total de likes que os vídeos extraídos daquela hashtag somaram. 

Depois disso parti para o código que gerou o gráfico. Iniciei com a linha: 
resumo_hashtags = resumo_hashtags[~resumo_hashtags["hashtags"].isin(["fy","faculdade","foryoupage","andteam","foryou","capcut","fyp","humor","fypシ","sucesso"])]
Usei ela para excluir as hashtags que tinham um volume grande de vídeos e apareciam no topo do data frame e focar apenas naquelas que faziam sentido com a minha pesquisa e que eu queria analisar.
Após isso usei o código da aula 6 para a geração do gráfico de disperção. Optei pelo gráfico de dispersão pois queria responder a pergunta "É verdade que quanto maior a quantidade de vídeos postados com essa hashtag, maior é a quantidade de likes total nos vídeos usando essa hashtag?" e o gráfico de dispersão mostra a relação entre duas variáveis numéricas.
Adicionei nesse códigos as linhas: 
fig, ax = plt.subplots(figsize=(9, 5), facecolor="#ABCCE7")
ax.set_facecolor("#A0C1E6")
ax.margins(y=0.15)
ax.margins(x=0.20)
A primeira e a segunda para definir a cor do background tanto da imagem quanto do próprio gráfico.
Já a terceira e a quarta foi para definir as margens do gráfico para que as hashtags não ficassem muito coladas nas maregsn tanto de cima quanto de baixo.
Também adicionei as seguintes linhas ao código:
for i, h in enumerate(top5["hashtags"]):
    ax.annotate(f"#{h}", (top5["qtd_posts"].iloc[i], top5["likes_total"].iloc[i] * 10000),
                xytext=(8, 4), textcoords="offset points", fontsize=9)
As adicionei para conseguir ver os nomes exatos das hashtags e não apenas os pontos em azul.
Por fim o gráfico foi gerado da melhor maneira para visualização da resposta de pergunta proferida.

## Achados

A partir da geração desso grafico_top5_hashtags.png consegui entender que não basta apenas utilizar as hashtags mais usadas na plataforma, ou no mesmo nicho que produzo o meu conteúdo. Apesar da #marketing ter o maior volume de vídeos da análise e ser de fato o maior número na soma dos likes, a segunda hashtag com mais vídeos não segue esse padrão, mostrando que isso não é necessariamente uma regra. Analisei que mesmo tendo um volume maior de vídeos postados com essas hashtags, esses vídeos somados não necessariamente tem mais likes do que outras hashtags menos usadas. Além disso nesse mesmo gráfico consegui entender que a #digitalmarketing mesmo tendo pouco mais da metade dos vídeos publicados que a #empresajunior soma muito mais likes. Também consegui entender nesse mesmo gráfico que o volume de postagens da #viral é bem menor que o da #marketing, mesmo que a minha hipótese fosse que a #viral era mais popular por ser uma hashtag que na minha concepção era usada para tentar impulsionare vídeos. Já no arquivo resumo_hashtags.csv consegui entender que as únicas hashtags com mais de 100 vídeos são as #marketing e #empresajunior. 


## Limitações

A coleta de diversas hashtags foi feita até o fim da aba de pesquisas de hashtags o que me fez gerar a hipótese de que o Tiktok não mostra todos os vídeos usando essas hashtags. Isso é uma limitação pois não consigo raspar 100% dos vídeos usando as hashtags e fazer uma análise maois ancorada. Outra limitação foi o fato de que diversos vídeos usam hashtags sobre a for you page o que polui a coleta, por isso tive que adicionar uma linha de código que remove essas hashtags como #fy e #fyp para deixar a coleta mais acertiva.

## Recomendações

É recomendado ancorar a estratégia para viralização de conteúdo em uma variável diferente das hashtags, uma vez que a geração do grafico_top5_hashtags.png mostra que apenas usar uma hashtag que tem um volume grande de vídeos, não garante a viralização do conteúdo. Outra recomendação é raspar outras hashtags que tenham mais de 100 vídeos postados cada, uma vez que nessa raspagen visualizada no arquivo resumo_hashtags.csv apenas 2 hashtags tem mais de 100 vídeos postados cada.

## Revisão por pares

**Revisado por:** 

Sabrina Lewin

**Comentários recebidos:**

> Sim, a pergunta está clara.
> Sim, os dados batem com o que é dito.
> Sim, o método está reproduzível.
> Sim, os achados possuem evidencia.
> Nao, as conclusoes nao extrapolam as evidências.
> Sim, achados e recomendacoes estam separados.

OBS: 
* é necessario colocar de que achado cada recomedacao depende. 
* é necessario colocar de onde foi retirado cada achado (ex: dados/resumo_hashtags)
* Seria ideal ter mais de 1 evidencia, pelo menos 3.
* Seria bom ter mais 1 recomendacao tambem.
* falta colocar o periodo de coleta (inicio do relatorio).

**O que mudou no relatório por causa da revisão (ou por que nada mudou):**

> Adicionei as referências de qual origem cada achado surgiu. Também adicionei mais 2 evidências e uma recomendação. Após isso coloquei a data certinha no relatório.

## Declaração de uso de IA

Usei IA quando tive dúvidas para melhorar a visualização do gráfico. As linhas descritas na parte de Método, como a acerca da correcão de margens e para adicionar os nomes das hashtags foram geradas com IA.