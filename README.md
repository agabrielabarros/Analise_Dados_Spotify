
# 🎵 Análise Spotify: Sinais precoces de sucesso de uma música

Análise exploratória de dados das músicas mais populares do Spotify em 2023, com o objetivo de identificar **sinais precoces** que ajudem a prever o sucesso de uma faixa (medido em número de streams) e apoiar as decisões do time de curadoria editorial.

> Projeto individual de análise de dados, desenvolvido com **BigQuery (SQL)** e **Looker Studio**.

---

## 📌 Índice

- [Contexto de negócio](#-contexto-de-negócio)
- [Objetivo](#-objetivo)
- [Perguntas de negócio](#-perguntas-de-negócio)
- [Dados](#-dados)
- [Ferramentas e tecnologias](#-ferramentas-e-tecnologias)
- [Processo de análise](#-processo-de-análise)
- [Resultados e insights](#-resultados-e-insights)
- [Dashboard](#-dashboard)
- [Limitações](#-limitações)
- [Próximos passos](#-próximos-passos)
- [Estrutura do repositório](#-estrutura-do-repositório)
- [Links](#-links)
- [Autora](#-autora)

---

## 💼 Contexto de negócio

O Spotify gera receita por meio de assinaturas Premium e publicidade, e ambas dependem do tempo de uso da plataforma. Por isso, a descoberta de músicas novas, via algoritmos e playlists editoriais, é o coração do negócio.

A diretoria percebeu que o investimento no time editorial continua alto, mas os resultados de streams por playlist são **muito inconsistentes** de um lançamento para outro. A pergunta central é:

> **Isso é sorte, tendência de mercado, ou a curadoria realmente gera o retorno esperado?**

Neste cenário, o time de Analytics foi acionado para fornecer uma primeira posição fundamentada em dados, que complemente (e não substitua) o julgamento humano da curadoria.

## 🎯 Objetivo

Analisar o conjunto de dados para descobrir **se existem sinais precoces que indiquem o sucesso de uma música no Spotify**, separando sinal de ruído e traduzindo os achados em recomendações claras para o negócio.

## ❓ Perguntas de negócio

Priorizadas a partir da thread de e-mails com a VP de Produto:

**Perguntas de decisão (VP de Produto)**
1. Consigo defender, com dados, que a curadoria editorial gera valor?
2. Existem sinais que aparecem cedo e ajudariam a priorizar apostas editoriais?
3. Existe algum padrão (gênero, país, quantidade de artistas, época de lançamento) que deveria entrar na estratégia de curadoria?

**Perguntas analíticas (Head de Analytics)**
1. Músicas presentes em mais playlists do Spotify têm mais streams?
2. Músicas que entram nos charts do Spotify têm mais streams do que as que não entram?
3. Existe relação entre presença em múltiplas plataformas (Spotify, Apple Music, Deezer, Shazam) e volume de streams?
4. Características da música (número de artistas, gênero, país) se relacionam com os streams?
5. O momento de lançamento (ano, mês) influencia os streams acumulados?

## 🗂️ Dados

O dataset reúne informações sobre as músicas mais populares do Spotify em 2023, dividido em duas tabelas ligadas pela chave `track_id`.

### `Track_in_spotify`: desempenho no Spotify

| Coluna | Descrição |
|---|---|
| `track_id` | Identificador único da música (inteiro de 7 dígitos) |
| `track_name` | Nome da música |
| `artists_name` | Nome do(s) artista(s) |
| `artist_count` | Número de artistas na música |
| `main_music_genre` | Principal gênero musical |
| `main_country` | Principal país da música |
| `released_year` | Ano de lançamento |
| `released_month` | Mês de lançamento |
| `released_day` | Dia de lançamento |
| `in_spotify_playlists` | Nº de playlists do Spotify em que a música aparece |
| `in_spotify_charts` | Presença/posição nos rankings do Spotify |
| `streams` | Total de reproduções no Spotify |

### `Track_in_competition`: desempenho em outras plataformas

| Coluna | Descrição |
|---|---|
| `track_id` | Identificador único da música |
| `in_apple_playlists` | Nº de playlists do Apple Music |
| `in_apple_charts` | Presença/posição nos rankings do Apple Music |
| `in_deezer_playlists` | Nº de playlists do Deezer |
| `in_deezer_charts` | Presença/posição nos rankings do Deezer |
| `in_shazam_charts` | Presença/posição nos rankings do Shazam |

## 🛠️ Ferramentas e tecnologias

- **BigQuery (Google Cloud)**: armazenamento, limpeza, transformação e análise com SQL
- **Looker Studio**: construção do dashboard interativo
- **SQL**: nulos, duplicados, outliers, `JOIN`, agregações e correlações
- **IA generativa**: apoio na estruturação do briefing e da documentação (com validação manual)
- **GitHub**: versionamento e documentação do projeto

## 🔄 Processo de análise

1. **Entendimento do problema de negócio**: leitura da thread de e-mails, definição das perguntas de negócio e identificação das limitações dos dados (briefing estruturado com apoio de IA e validado manualmente).
2. **Configuração no BigQuery**: criação do projeto e do dataset e importação das duas tabelas.
3. **Limpeza dos dados**
   - Identificação e tratamento de **valores nulos**
   - Identificação e tratamento de **valores duplicados**
   - Tratamento de **valores atípicos** em variáveis categóricas
   - Tratamento de **valores atípicos** em variáveis numéricas
4. **Integração**: união das tabelas com `JOIN` pela chave `track_id`.
5. **Análise exploratória**: tabelas dinâmicas, gráficos e correlações entre variáveis.
6. **Dashboard**: conexão da base tratada ao Looker Studio.
7. **Conclusões e recomendações**: respostas às perguntas de negócio, diferenciando o que os dados sustentam do que ainda é hipótese.

> 📁 As consultas SQL utilizadas estão na pasta [`/sql`](./sql).

## 📊 Resultados e insights

> ⚠️ *Preencha esta seção com os achados da sua análise.*

| Pergunta | Resultado | Evidência |
|---|---|---|
| Mais playlists → mais streams? | _a preencher_ | _correlação / gráfico_ |
| Charts do Spotify → mais streams? | _a preencher_ | _comparativo_ |
| Presença em várias plataformas → mais streams? | _a preencher_ | _correlação_ |
| Gênero, país e nº de artistas influenciam? | _a preencher_ | _tabelas / gráficos_ |
| Época de lançamento influencia? | _a preencher_ | _gráficos_ |

### Principais insights

- _Insight 1_
- _Insight 2_
- _Insight 3_

### Recomendações para o negócio

- _Recomendação 1_
- _Recomendação 2_

> **Atenção:** correlação não implica causalidade. Músicas com mais playlists podem ter mais streams justamente porque a curadoria já as escolheu por parecerem promissoras.

## 📈 Dashboard

🔗 **[Acesse o dashboard no Looker Studio](#)** _(adicione o link)_

_Adicione aqui um print do dashboard:_

```md
![Dashboard](./images/dashboard.png)
```

## ⚠️ Limitações

- Não há dados de **investimento editorial por faixa**, então não é possível medir diretamente o efeito da curadoria.
- Não há **série temporal diária** de streams, o que limita a identificação de sinais "precoces" de fato.
- A análise é exploratória e mostra **associações**, não relações causais.
- O dataset cobre apenas as músicas populares de 2023, o que pode gerar **viés de sobrevivência** (não vemos as faixas que "sumiram").

## 🚀 Próximos passos

- Solicitar ao time de Data Engineering dados de série temporal e de investimento editorial por faixa.
- Testar a significância estatística das relações encontradas.
- Evoluir para modelos que estimem a probabilidade de sucesso de uma faixa.

## 📂 Estrutura do repositório

```
.
├── README.md
├── sql/                  # Consultas utilizadas (limpeza, JOIN, análises)
├── images/               # Prints do dashboard e gráficos
├── data/                 # (opcional) amostras dos dados
└── ficha-tecnica.md      # Ficha técnica completa do projeto
```

## 🔗 Links

- 📄 Ficha Técnica: _adicione o link_
- 📊 Dashboard (Looker Studio): _adicione o link_
- 🖥️ Apresentação (Google Slides): _adicione o link, se houver_

## 👩‍💻 Autora

**Gabi**
Estudante de Ciência da Computação em transição de Produto e Análise de Negócios para Engenharia de Software e IA/ML.

- GitHub: [@agabrielabarros](https://github.com/agabrielabarros)
- LinkedIn: _linkedin.com/in/imgabrielabarros_
