**Fonte, período e tamanho da coleta:**

> Dados de 1044 vídeos do Tiktok coletados através do Zeeschuimer de 13 de dezembro de 2020 até o dia 19 de agosto de 2026 .

**As duas variáveis que você criou (a contínua da Parte A e o rótulo da Parte B), com a fórmula/critério de cada uma:**

> Taxa de engajamento e se houve viralização ou não. A taxa de engajamento é medida através da fórmula: "likes"+ "comments" + "shares" / "plays". Enquanto a viralização é medida a partir de: do percentil 80 (os 20% mais viralizados definem o que é a viralização)

**As features usadas nas Partes A e B, e quais colunas você descartou por vazamento:**

> 'tam_legenda', 'n_emojis', 'n_hashtags'. Descartei as colunas "likes", "comments", "shares", "plays" pois se eu as tivesse utilizando na previsão eu não estaria prevendo nada, uma vez que essas variáveis estão diretamente associadas a formula utilizada para a previsão.

**Parte A — resultado:** MAE e R² do modelo bobo, da linear e da árvore. O seu melhor modelo bateu o bobo?

> Não, o modelo bobo deu o resultado mais favorável, uma vez que o MAE mais próximo de 0 e o R² mais próximo de 1 foi o do modelo bobo.

**Parte B — resultado:** a matriz de confusão e uma leitura: a favor de quem o modelo erra?

> A matriz de confusão retorna os valores: VN = 92; FP = 65; FN = 66; VP = 91; Ele está errando a favor dos falsos negativos. Isso é, existem 66 posts que, em suma, deveriam ter sido classificados como: sim, o post viralizou, mas na verdade, o modelo não fez isso, ele os classificou como: não, o post não virazlizou. Apesar disso, a precisão e o recall deram valores muito próximos (0,58; 0,58) pois o numero de FP e FN ficou quase igual> Isso nos diz que o modelo está errando de maneira semelhantes para ambos os lados, tanto dizendo que hove e que não houve viralização. Quando reduzimos o corte para 0,30 o modelo passa a classificar mais posts como virais, acertando 100% dos virais (como podemos observar no recall de 100%), porém com esse aumento de acertos, aumentam também a quantia de alarmes falsos o que joga a precisão para 0,50.

**Parte C — resultado:** quantos segmentos, como você escolheu `k`, e a descrição de cada segmento (uma frase com número).

> Escolhi 5 segmentos (cluster 0, 1, 2, 3 e 4). Cluster 0: Esse cluster parece agrupar cotas menores, minha hipótese é que sejam contas criadas recentemente ou que não sejam usadas com tanta frequência, uma vez que podemos ver que todas as métricas são baixas, comportamento normal para uma conta criada recentemente na rede. Cluster 1: Esse cluster já parece o oposto do clusten anterior, a hipótese é que ele está agrupando as maiores e mais viralizadas contas da amostra, umua vez que todas as métricas apresentam números extremamente altos. Cluster 2: Esse cluster parece conter as contas com tamanho moderado porém baixo engajamento: mesmo tendo 31 mil seguidores, o numero de likes é apenas 1175 e apresenta apenas 21.9 comentários. Cluster 3: Esse cluster parece apresentar contas usadas com frequência mas com o engajamento bem baixo: mesmo tendo quase o mesmo número de vídeos que o cluster 2, esse cluster apresenta apenas 44 likes e 2.7 seguidores. Cluster 4: Esse cluster parece apresentar contas com tamanho médio mas engajamento alto: mesmo tendo menos seguidores que o cluster 2, esse cluster mostra 80 mil likes e 1 milhão de likes, 20 vezes mais likes que o cluster 2.

**Uma conclusão que os seus dados sustentam** (sem extrapolar para além da sua coleta):

> Dado o tamanho da amostra da base de dados e a baixa variabilidade, o Modelo Bobo foi mais acertivo em relação a Regressão Linear e a Árvore de Decisão, uma vez que o seu MAE deu um resultado mais próximo de 0 e um R² mais próximo de 1 do que o MAE e o R² da Regressão Linear e da Árvore de Decisão.

**Revisão por pares:** nome do colega **da turma** que revisou, o que ele apontou, e o que você mudou (ou por que não mudou).

> Revisado por: Sabrina Lewin.
> Na parte B deste README, seria interessante colocar as metricas de recall e precisao para explicarem o porque de haver uma quantidade de falsos negativos e falsos positivos tao parecida. Nesse caso, recall e precisao sao iguais, ou seja, ao selecionar um post como viral, ele acertou 0,58 das vezes, mostrando que ele puxa uma quantidade de posts consideraveis como virais, porem tende a ter uma precisao considerada "mediana" tambem, justamente porque ao puxar varios posts que nao sao virais como virais (recall relativamente alto), a precisao diminui.

**Declaração de uso de IA:** ferramenta usada, em que trecho ou decisão, e o que você conferiu ou alterou depois (mesmo que seja "não usei IA nesta entrega"). Lembre: nesta entrega, IA não pode ser usada para gerar o código de análise.

> Usei IA nas linhas autodeclaradas (#IA) para solucionar erros que eu não conseguia encontrar soluções, ambos os usos foram para passar os valores para log para permitir maior eficácia no uso dos modelos. Usei o Claude, principalmente o modelo Sonnet 5, para realizar essa pesquisa. 