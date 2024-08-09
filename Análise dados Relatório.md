Aqui está o texto formatado e melhorado em Markdown:

# Análise de Dados: Relatório Carteira de Trabalho

Os dados analisados foram retirados do site Emprega Brasil, do governo brasileiro. Eles referem-se à emissão da Carteira de Trabalho e Previdência Social (CTPS) nos períodos de 2023 e 2024. Como ainda estamos em 2024, os dados deste ano não estão completos. Outro detalhe é que a base de dados disponibilizou apenas o mês e o ano.

Identificamos três grupos principais na base de dados: Gênero (Masculino e Feminino), Raça/Cor, e Gerações. Não houve coleta de dados de pessoas transgênero, não binárias ou de outras identidades de gênero.

## Na categoria Gênero

Em 2023, os homens emitiram mais carteiras de trabalho do que as mulheres, totalizando 45 carteiras emitidas e 57 segundas vias. Já em 2024, foram emitidas 9 carteiras, sendo 7 primeiras vias e 2 segundas vias.

## Na categoria Raça/Cor

Em 2023, a maioria das carteiras foi emitida por pessoas brancas (40), seguidas por pardas (39), pretas (22) e uma pessoa amarela.

Em 2024, apenas pessoas brancas e pardas emitiram carteiras.

## Na categoria de Gerações

Em 2023, as categorias de gerações foram distribuídas da seguinte forma:

- Geração X: 36 pessoas
- Geração Y: 30 pessoas
- Geração Z: 23 pessoas
- Baby Boomers: 16 pessoas

Em 2024, as emissões foram realizadas apenas por:

- Baby Boomers: 3 pessoas
- Geração X: 3 pessoas
- Geração Z: 3 pessoas

Para atribuir as gerações aos anos na base de dados, utilizei o seguinte código DAX:

```dax
Gerações = 
SWITCH(
    TRUE(),
    'Dados Brutos'[Data Nascimento - Ano] >= 1940 && 'Dados Brutos'[Data Nascimento - Ano] <= 1964, "Baby Boomers",
    'Dados Brutos'[Data Nascimento - Ano] >= 1965 && 'Dados Brutos'[Data Nascimento - Ano] <= 1980, "Geração X",
    'Dados Brutos'[Data Nascimento - Ano] >= 1981 && 'Dados Brutos'[Data Nascimento - Ano] <= 1996, "Geração Y",
    'Dados Brutos'[Data Nascimento - Ano] >= 1997 && 'Dados Brutos'[Data Nascimento - Ano] <= 2010, "Geração Z"
)
```

Para os cartões de 1ª e 2ª via, foi utilizado o seguinte código DAX:

```dax
Contagem Protocolo 1 = CALCULATE(COUNTA('Dados Brutos'[Tipo Protocolo]), 'Dados Brutos'[Tipo Protocolo] IN {"1ª Via"})
```

# Dados Sexo, Cor/Raça e Gerações

Nesta página, existem gráficos com dados cruzados.

Um deles mostra o total por Raça/Cor e Gênero, onde o grupo dominante são pessoas brancas do gênero masculino (47 pessoas). O menor grupo são pessoas amarelas do gênero masculino.

O segundo gráfico mostra o Total por Gerações e Gênero. Novamente, o grupo masculino foi predominante, com a Geração X sendo a que mais emitiu carteiras de trabalho.

Outro dado disponível é o estado civil. O grupo dominante são as pessoas solteiras. O dado N/A refere-se às pessoas que não declararam seu estado civil.

Os dados de Data de Emissão por Gerações e Data de Emissão por Gênero mostram a porcentagem das populações nos anos de 2023 e 2024.

# Nível de Escolaridade e Gênero

Na terceira página do relatório, está a Contagem por Nível de Escolaridade e Gênero. Este gráfico possui uma funcionalidade de expansão para visualizar cada categoria individualmente. Como são muitas categorias, o gráfico foi colocado em uma página separada.

## Analisando

Mais pessoas do gênero masculino com 2º grau completo, técnico ou profissionalizante, foram as que mais emitiram carteira de trabalho nos anos de 2023 e 2024. 

Apenas uma mulher com doutorado emitiu a carteira nesse período.

# Regiões

Nesta última aba, vemos que pessoas de outras nacionalidades também emitiram a carteira de trabalho no Brasil, totalizando 10 pessoas. Os países de origem são Argélia, Argentina, Chile, Colômbia, Espanha e Grécia.