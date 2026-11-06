# Roteiro de analise de dados

### 1. Disparidade Socioeconômica e Escolar

* **Desempenho por Dependência Administrativa (`TP_DEPENDENCIA_ADM_ESC`)**:
* **O que comparar**: Média e distribuição das notas (`NU_NOTA_CN`, `NU_NOTA_CH`, `NU_NOTA_LC`, `NU_NOTA_MT`, `NU_NOTA_REDACAO`) entre escolas **Federais, Estaduais, Municipais e Privadas**.
* **Tipo de Gráfico**: *Boxplot* ou *Violin Plot* lado a lado para cada área do conhecimento.


* **Escola Urbana vs. Rural (`TP_LOCALIZACAO_ESC`)**:
* **O que comparar**: A diferença percentual no alcance de notas altas (ex: redação > 800) entre estudantes de escolas urbanas e rurais.
* **Tipo de Gráfico**: Gráfico de barras agrupadas ou *ridge plot*.



---

### 2. Análise Detalhada da Redação (Comportamento das Correções)

* **Consistência entre Avaliadores (`AV1` vs `AV2` vs `AV3`)**:
* **O que comparar**: Quantidade de redações que precisaram do 3º avaliador (`NU_NOTA_AV3` preenchida) ou da banca examinadora (`AV4`), revelando o grau de discrepância na correção.
* **Tipo de Gráfico**: Gráfico de Rosca / Pizza (porcentagem de casos corrigidos por 2, 3 ou 4 avaliadores) ou matriz de dispersão (*Scatter plot*) comparando `NU_NOTA_AV1` vs `NU_NOTA_AV2`.


* **Perfil de Competências mais Críticas**:
* **O que comparar**: A média nacional obtida nas 5 competências (`NU_NOTA_COMP1` a `NU_NOTA_COMP5`).
* **Tipo de Gráfico**: Gráfico de Radar (Teia de Aranha) ou barras horizontais ordenadas para identificar a competência onde os alunos mais perdem pontos.


* **Motivos de Anulação/Nota Zero (`TP_STATUS_REDACAO`)**:
* **O que comparar**: A proporção de redações anuladas por fuga ao tema, texto em branco, cópia ou não atendimento ao tipo textual.
* **Tipo de Gráfico**: Gráfico de barras verticais ordenadas por frequência.



---

### 3. Comportamento e Estratégia dos Participantes

* **Escolha de Língua Estrangeira (`TP_LINGUA`) vs. Desempenho em Linguagens (`NU_NOTA_LC`)**:
* **O que comparar**: Distribuição de preferência por Inglês vs. Espanhol e como o desempenho na prova de Linguagens difere entre os dois grupos.
* **Tipo de Gráfico**: Histograma sobreposto ou *KDE Plot* (densidade).


* **Taxa de Abstenção por Prova e Região (`TP_PRESENCA_*` x `SG_UF_PROVA`)**:
* **O que comparar**: A porcentagem de faltantes no 1º dia (CH/LC) vs. 2º dia (CN/MT) por Estado.
* **Tipo de Gráfico**: Mapa de Calor (*Heatmap*) ou gráfico de barras empilhadas.



---

### 4. Desempenho Técnico e Padrão de Respostas

* **Taxa de Chute e Consistência (Gabarito vs. Respostas)**:
* **O que comparar**: Cruzamento do vetor de respostas (`TX_RESPOSTAS_*`) com o gabarito (`TX_GABARITO_*`) para calcular a taxa de acertos por posição da questão (início vs. fim da prova), avaliando o efeito do cansaço.
* **Tipo de Gráfico**: Gráfico de linha (Índice de acerto por número da questão, do item 1 ao 45).


* **Distribuição TRI por Área do Conhecimento**:
* **O que comparar**: Comparar as curvas de distribuição das notas objetivas para visualizar qual área teve o maior "teto" ou "piso" de nota (ex: Matemática costuma atingir notas mais altas no topo do que Linguagens).
* **Tipo de Gráfico**: Gráfico de densidade de curvas sobrepostas.



---

### 5. Geografia do Exame (Análise Regional)

* **Deslocamento/Mobilidade de Prova (`CO_MUNICIPIO_ESC` vs `CO_MUNICIPIO_PROVA`)**:
* **O que comparar**: Quantidade de alunos que precisaram fazer a prova em um município diferente daquele onde estudavam.
* **Tipo de Gráfico**: Gráfico de barras com a proporção de estudantes "em trânsito" por Estado (`SG_UF_ESC`).


* **Ranking de Desempenho Médio por UF (`SG_UF_PROVA`)**:
* **O que comparar**: A média geral (soma de todas as provas + redação) por Estado do Brasil.
* **Tipo de Gráfico**: Choropleth Map (Mapa temático do Brasil colorido por faixa de nota).



---
