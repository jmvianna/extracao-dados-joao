# Comandos da Aula 23

| Código | Para quê |
|---|---|
| `getpass("Sua chave Groq: ")` | Receber chave sem mostrá-la no notebook. |
| `requests.post(..., json=...)` | Enviar uma notícia para a API Groq. |
| `response_format={"type": "json_schema", ...}` | Pedir campos com formato definido. |
| `pd.crosstab(veiculo, foco)` | Conferir o denominador dos quatro grupos. |
| `groupby(["veiculo", "foco_amostral"]).sample(n=4, random_state=42)` | Criar a amostra de 16 para a IA. |
| `SentenceTransformer(...).encode(textos)` | Calcular embeddings. |
| `cosine_similarity(pergunta, textos)` | Ordenar resultados por semelhança. |

Se houver erro `429`, aguarde. Não repita as 16 chamadas apenas para redesenhar uma tabela. O modelo Groq usado na aula é `openai/gpt-oss-20b`.
