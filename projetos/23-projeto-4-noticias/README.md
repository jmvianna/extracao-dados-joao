# Aula 23 — Extração estruturada e busca semântica

Abra [23-extracao-busca-semantica.ipynb](23-extracao-busca-semantica.ipynb) no Google Colab. A aula mostra por que transformar notícias em fichas verificáveis ajuda um trabalho de clipping e comunicação, demonstra saída estruturada com Groq e compara busca por palavra e por significado. Use GPU para acelerar os embeddings. Cada estudante cria sua própria chave Groq em [GroqCloud](https://console.groq.com/keys); ela é digitada com `getpass` e não vai para o notebook salvo.

Depois faça [exercicios/projeto-4-noticias.ipynb](exercicios/projeto-4-noticias.ipynb): **Projeto 4, peso 2**, integrando as Aulas 21–23. A [base fechada](dados/noticias_lula_flavio_2026.csv) contém 40 títulos e resumos, com datas e links, distribuídos em quatro grupos de dez: Agência Brasil ou CNN Brasil × foco em Lula ou Flávio Bolsonaro. O foco é o critério de seleção, não uma avaliação de tom. As matérias completas permanecem nas páginas dos veículos. A extração com Groq usa 16 linhas amostradas; as contagens, tópicos e buscas usam as 40.

As notícias gerais das Aulas 21–22 vêm de [um corpus de 500 textos brasileiros](https://github.com/mauricio-seiji/Dataset-news-articles-pt-br).
