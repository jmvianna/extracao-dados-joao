> Projeto 4: 

> Objetivo e Pergunta
O objetivo é transformar títulos e resumos em dados auditáveis e escrever uma conclusão. O trabalho traz este recorte de 40 matérias e não mede a cobertura total desses veículos. A pergunta é o que este recorte de notícias da Agência Brasil e da CNN Brasil mostra sobre a cobertura de Lula e Flávio Bolsonaro?

> Preparação
A preparação inicia com a fonte: noticias_lula_flavio_2026.csv, do repositório da aula. Já a tabela tem título, resumo publicado pela fonte, data, URL e o texto_analise. Não tem os artigos completos. A janela temporal é de 03/10/2026 a 13/10/2026. A regra de seleção é de dez matérias por combinação de veículo e foco no Lula ou no Flávio Bolsonaro. O foco é o critério de entrada da matéria na base, como por exemplo o título, e a base não é uma amostra aleatória. Para a tabela de denominadores: A base tem 40 matérias, e cada grupo tem 10. A Agência Brasil tem 10 matérias com foco em Flávio Bolsonaro e 10 com foco em Lula, num total de 20. A CNN Brasil também tem 10 com foco em Flávio Bolsonaro e 10 com foco em Lula, num total de 20. Para a extração com IA, usei uma amostra de 16 matérias. Ela tem, na Agência Brasil, 4 matérias com foco em Flávio Bolsonaro e 4 com foco em Lula, totalizando 8 matérias, e na CNN Brasil, 4 com foco em Flávio Bolsonaro e 4 com foco em Lula, também num total de 8. Na conferências da base achei que haviam 40 linhas, 0 textos de análise vazios e 0 duplicatas exatas.

> Revisão das aulas 21 e 22
Da Aula 21, usei a ideia de guardar o texto original e criar uma versão preparada ao lado, com regras que eu consiga explicar, olhando sempre o antes e o depois. Da Aula 22, usei o TF-IDF e o NMF, e só dei nome pra cada tópico depois de ler as manchetes de maior peso.

> Roteiro de análise
Carreguei e conferi a base, preparei o texto, apliquei o TF-IDF e o NMF com 4 tópicos e contei as menções a Lula e Flávio com o denominador de cada grupo. Depois extraí fichas de 16 matérias com o Groq, auditei quatro e comparei a busca por palavra com a busca semântica.

> Prática aplicada
Para a preparação textual preservei o texto_analise e criei o texto_preparado com a função preparar() da Aula 21. A mediana de tokens foi de 32,5 para 32,0 e a média de 32,0 para 31,6. Os três casos lado a lado foram P05 (nome próprio e negação), P11 (nome próprio composto e sigla) e P29 (números). No foco no Lula, as palavras mais frequentes são lula (23), canal (7), ato (7) e tse (6), e no foco em Flávio Bolsonaro são flávio (24), candidato (9), turno (8) e pl (6). As regras foram cinco, deixei tudo em minúsculas, para juntar Lula e lula, mas isso perde a marca de nome próprio e de sigla, como por exemplo Nunes Marques virou nunes marques em P05, e PL virou pl em P11. Mantive a remoção de URLs da aula, que não teve efeito porque o texto não tem URLs. Mantive os acentos, para preservar São Paulo e Flávio, e o TF-IDF remove os acentos depois. Defini o token como uma sequência de letras, o que apaga números, como em P29, escala 6x1 virou escala e 2º turno virou turno. E não tirei as stopwords da versão preparada, para preservar negações como o não de "não encontram" em P05. Sobre as menções a Lula e Flávio, contei as vezes que Lula e Flávio aparecem em título e resumo, com 10 matérias por grupo. Na Agência Brasil, no foco em Flávio Bolsonaro, Lula aparece 6 vezes e Flávio 13, e no foco no Lula, Lula aparece 13 vezes e Flávio 4. Na CNN Brasil, no foco Flávio Bolsonaro, Lula aparece 6 vezes e Flávio 11, e no foco Lula, Lula aparece 10 vezes e Flávio 2. Quanto aos tópicos, rodei o TF-IDF e o NMF com 4 tópicos e random_state=42 nos 40 textos, tirando lula, flávio e bolsonaro para os nomes não dominarem. O tópico 0 chamei de "segundo turno e reta final de Flávio" (P39, P38, P37). O tópico 1 virou "canal Exército do Lula e TSE" (P05, P27, P09). O tópico 2 virou "atos de campanha e apoios" (P04, P15, P06). O tópico 3 não consegui nomear (P26, P01, P16). Contando as matérias dos tópicos 0, 1, 2 e 3, nessa ordem, a Agência Brasil com foco em Flávio tem 1, 0, 6 e 3, e com foco em Lula tem 0, 3, 4 e 3. A CNN Brasil com foco em Flávio tem 6, 2, 1 e 1, e com foco em Lula tem 2, 2, 3 e 3. Após isso, quanto a extração com Groq, usei o modelo openai/gpt-oss-20b, com uma chamada de teste (P19) e um lote de 16 chamadas, salvo em fichas_extraidas.csv. No meio do trabalho o Colab desconectou por inatividade e a sessão foi reiniciada, então os arquivos que estavam só na sessão (fichas_extraidas.csv, tabela_topicos.csv e tabela_mencoes.csv) se perderam. Para recuperar, executei o notebook de novo do começo ao fim, o que rodou o lote da Groq mais uma vez, e baixei os três arquivos dessa nova execução. As quatro fichas que audito abaixo saíram iguais às da execução anterior, e as tabelas de tópicos e de menções também. As outras 12 fichas eu não consigo comparar com a execução anterior, porque aquele arquivo se perdeu. Ademais, a evidência é trecho literal do texto_analise nas 16 fichas (8 de cada veículo). Na chamada de teste, o campo limite veio com o texto "null" e não com uma limitação real. Por fim, sobre a busca, a pergunta fixa foi: "Quais reportagens mostram pesquisas de opinião da população sobre esses candidatos?" 

> Resultados do desafio
> Achados:
Achado 1: a busca por palavra não encontrou as matérias de pesquisa. As duas matérias de pesquisa do recorte são P23 (https://www.cnnbrasil.com.br/eleicoes/gerp-49-dos-brasileiros-desaprovam-governo-lula-45-aprovam/) e P24 (https://www.cnnbrasil.com.br/eleicoes/gerp-lula-e-rejeitado-por-53-dos-eleitores-flavio-por-42/). A busca por palavra trouxe P08, P33 e P17 no top 3, e a semântica trouxe P24 em primeiro lugar, com score 0,54.
Achado 2: o episódio do canal "Exército do Lula" aparece nos dois veículos. O tópico 1 reúne P05 (https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/tecnicos-do-tse-nao-encontram-conteudo-falso-no-canal-exercito-do-lula) e P09 (https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/campanha-registra-canal-exercito-do-lula-na-justica-eleitoral), da Agência Brasil, e P27 (https://www.cnnbrasil.com.br/blogs/gustavo-uribe/eleicoes/canal-exercito-do-lula-e-registrado-junto-ao-tse/) e P28 (https://www.cnnbrasil.com.br/eleicoes/janones-diz-que-cumprira-exigencias-do-tse-para-reativar-exercito-de-lula/), da CNN Brasil.
Achado 3: concentração de tópicos por grupo. O tópico 0 contém 6 das 10 matérias da CNN Brasil sobre Flávio, entre elas P37 (https://www.cnnbrasil.com.br/blogs/isabel-mega/eleicoes/centrao-mira-pastas-com-maior-orcamento-se-flavio-vencer/), P38 (https://www.cnnbrasil.com.br/blogs/jussara-soares/eleicoes/flavio-buscara-orientacao-de-bolsonaro-para-reta-final-dizem-aliados/) e P39 (https://www.cnnbrasil.com.br/eleicoes/flavio-bolsonaro-esta-satisfeito-com-1o-turno-e-deu-dicas-para-disputa/). O tópico 2 contém 10 das 20 matérias da Agência Brasil.

> Interpretação:
A contagem de menções acompanha o foco, então não indica qual veículo dá mais espaço para cada um dos candidatos. P37, P38 e P39 são todas de 13/10, a 12 dias do segundo turno, então o tópico 0 pode refletir o dia e não um tema recorrente da CNN Brasil. A busca por palavra falhou porque compara palavras exatas, e a semântica achou só uma das duas matérias de pesquisa. Com 40 textos curtos, 4 tópicos e parâmetros escolhidos por mim, nenhuma diferença no que vi me permitiu cravar algum viés do jornal, pois isso exigiria uma amostra maior, com seleção aleatória e leitura dos textos completos.

> Fichas auditadas:
Comparei as fichas com o texto_analise. Dei uma olhada nas matérias mas nada muito a fundo devido ao tempo. Assim, na P12 (Agência Brasil, com foco no Flávio), a ficha usa só o título e deixa de fora o resumo, em que ele aguarda o horário para visitar o pai, e o tema veio como "religion", em inglês. Na P02 (Agência Brasil, foco em Lula), também só o título entrou, e ficou de fora a votação do fim da escala 6x1. Na P37 (CNN Brasil, com foco no Flávio), ficou de fora o apoio dos partidos ao senador no segundo turno, e a atribuição é ambígua, porque a pessoa central é Flávio, mas quem age na frase é o Centrão. Na P28 (CNN Brasil, foco no Lula), ficou de fora a suspensão do grupo até o registro no TSE, e a pessoa central é Janones, enquanto o foco do grupo é Lula. Nas quatro, o fato e a evidência só repetem o título, então a checagem de evidência literal é fraca. As quatro fichas auditadas batem com as linhas do fichas_extraidas.csv. Olhando o campo limite nesse arquivo, ele nem sempre traz uma limitação de verdade. Por exemplo, em 4 fichas veio escrito null ou none, e nas outras costuma vir um pedaço solto do texto, como 48 horas na P09 e Copacabana na P06. Na P01 veio 2026-11-04, uma data que nem aparece no texto. No mesmo arquivo também há fichas em que a evidência é o título e o resumo juntos (P01, P06 e P23), o que mostra que a checagem de evidência literal é fraca.

Links das fichas:
P12: https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/flavio-bolsonaro-participa-de-missa-na-catedral-de-brasilia-0

P02: https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/ato-pela-reeleicao-de-lula-leva-milhares-a-avenida-paulista

P37: https://www.cnnbrasil.com.br/blogs/isabel-mega/eleicoes/centrao-mira-pastas-com-maior-orcamento-se-flavio-vencer/

P28: https://www.cnnbrasil.com.br/eleicoes/janones-diz-que-cumprira-exigencias-do-tse-para-reativar-exercito-de-lula/

> Tópico confuso
O tópico 3 (campanha, casa, presidente, vida, site, oferece, pretende) mistura assuntos sem relação. As palavras casa e vida vêm de P01 (Minha Casa, Minha Vida) e de P26 (custo de vida e gravação em casa de apoiadores), e site e oferece vêm das matérias sobre criptomoedas (P16 e P19). O tópico reúne 10 matérias dos quatro grupos, e P40 (0,041) e P24 (0,050) ficaram em tópicos com peso baixo.

> Comparação de buscas
Na busca por palavra, o top 3 foi P08, P33 e P17, e nenhuma delas trata de pesquisa de opinião. As três contêm a palavra "sobre". Na semântica, o top 3 foi P24 (0,54), P21 (0,502) e P14 (0,463). Só a P24, que traz o Gerp com Lula rejeitado por 53% e Flávio por 42%, é relevante. A P21 e a P14 tratam de apoio a candidatos, sem pesquisa. A P23 ficou fora do top 3 nos dois métodos. O TF-IDF compara palavras exatas, então "pesquisas" não encontra "pesquisa", e a semântica trouxe duas matérias sem relação com scores próximos do acerto. 

Links:

P08: https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/pf-nega-existencia-de-depoimento-envolvendo-vorcaro-e-lula

P33: https://www.cnnbrasil.com.br/eleicoes/o-que-sabemos-sobre-a-propaganda-de-flavio-que-foi-exibida-sem-audio/

P17: https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/mendonca-multa-flavio-por-impulsionar-post-negativo-contra-lula

P24: https://www.cnnbrasil.com.br/eleicoes/gerp-lula-e-rejeitado-por-53-dos-eleitores-flavio-por-42/

P21: https://www.cnnbrasil.com.br/eleicoes/mdb-em-dez-estados-do-norte-e-nordeste-declaram-apoio-a-reeleicao-de-lula/

P14: https://agenciabrasil.ebc.com.br/politica/noticia/2026-10/flavio-bolsonaro-recebe-apoios-de-governadores-eleitos-e-cury

P23: https://www.cnnbrasil.com.br/eleicoes/gerp-49-dos-brasileiros-desaprovam-governo-lula-45-aprovam/

> Limitações
O lote da Groq rodou mais de uma vez, porque o Colab desconectou e precisei gerar os arquivos de novo, então o fichas_extraidas.csv é o da última execução. Além disso, a base tem só 40 matérias em 11 dias, então as conclusões valem só para o recorte. Só tem título e resumo, e a contagem de menções soma ocorrências e não matérias, e os quatro tópicos dependem de min_df, ngram_range e das stopwords. A extração cobre 16 das 40 matérias, a auditoria cobre 4 fichas e a relevância das buscas foi avaliada por um leitor, com uma pergunta, o que explicita uma limitação a interpretação desse leitor com base nessa pergunta.

> Entrega
A pasta 23-projeto-4-noticias/ tem o notebook (projeto-4-noticias.ipynb), este README.md, tabela_topicos.csv, tabela_mencoes.csv e fichas_extraidas.csv. A entrega foi feita em commits: primeiro o notebook salvo pelo Colab (e salvo de novo depois da nova execução) e depois o README.md com as tabelas. Conferi que tabela_topicos.csv e tabela_mencoes.csv batem com as saídas do notebook e que as quatro fichas auditadas batem com o fichas_extraidas.csv.

> Declaração de uso de IA
Usei o Claude para revisar os códigos depois de finalizado, conferir se o README.md estava contendo tudo que o escopo do projeto pedia e criar a caixinha [x] da checklist. Além disso, o Claude me orientou com o que devia fazer depois de ter perdido as tabelas por conta do colab ter reiniciado.

> Checklist
[x] 40 linhas: 10 por veículo × foco.
[x] Chave pessoal fora dos arquivos entregues.
[x] Extração em amostra de 16, com quatro auditorias.
[x] Conclusões citam IDs e links e respeitam o recorte.
[x] Notebook executa de cima a baixo no Colab.