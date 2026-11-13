# Project setup

`./venv/bin/pip install -r requirements.txt`

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

# Dicionário de dados

| NOME_COLUNA | CATEGORIA | DESCRICAO |
| :--- | :--- | :--- |
| `NU_SEQUENCIAL` | Identificação | Identificador sequencial do participante no arquivo de resultados. |
| `NU_ANO` | Identificação | Ano de realização da edição do exame (ex: 2025). |
| `CO_ESCOLA` | Escola | Código INEP/Censo Escolar da escola do participante. |
| `CO_MUNICIPIO_ESC` | Escola | Código IBGE do município da escola. |
| `NO_MUNICIPIO_ESC` | Escola | Nome do município da escola. |
| `CO_UF_ESC` | Escola | Código numérico IBGE do estado (UF) da escola. |
| `SG_UF_ESC` | Escola | Sigla da Unidade da Federação da escola. |
| `TP_DEPENDENCIA_ADM_ESC` | Escola | Dependência administrativa (1: Federal, 2: Estadual, 3: Municipal, 4: Privada). |
| `TP_LOCALIZACAO_ESC` | Escola | Localização da escola (1: Urbana, 2: Rural). |
| `TP_SIT_FUNC_ESC` | Escola | Situação de funcionamento da escola no Censo Escolar. |
| `CO_MUNICIPIO_PROVA` | Local da Prova | Código IBGE do município onde o candidato realizou a prova. |
| `NO_MUNICIPIO_PROVA` | Local da Prova | Nome do município onde o candidato realizou a prova. |
| `CO_UF_PROVA` | Local da Prova | Código numérico IBGE do estado onde o candidato realizou a prova. |
| `SG_UF_PROVA` | Local da Prova | Sigla da Unidade da Federação onde o candidato realizou a prova. |
| `TP_PRESENCA_CN` | Presença | Presença em Ciências da Natureza (0: Faltou, 1: Presente, 2: Eliminado). |
| `TP_PRESENCA_CH` | Presença | Presença em Ciências Humanas (0: Faltou, 1: Presente, 2: Eliminado). |
| `TP_PRESENCA_LC` | Presença | Presença em Linguagens e Códigos (0: Faltou, 1: Presente, 2: Eliminado). |
| `TP_PRESENCA_MT` | Presença | Presença em Matemática (0: Faltou, 1: Presente, 2: Eliminado). |
| `CO_PROVA_CN` | Prova Objetiva | Código da prova/caderno de Ciências da Natureza. |
| `CO_PROVA_CH` | Prova Objetiva | Código da prova/caderno de Ciências Humanas. |
| `CO_PROVA_LC` | Prova Objetiva | Código da prova/caderno de Linguagens e Códigos. |
| `CO_PROVA_MT` | Prova Objetiva | Código da prova/caderno de Matemática. |
| `NU_NOTA_CN` | Notas Objetivas | Nota da prova de Ciências da Natureza (escalonada via TRI). |
| `NU_NOTA_CH` | Notas Objetivas | Nota da prova de Ciências Humanas (escalonada via TRI). |
| `NU_NOTA_LC` | Notas Objetivas | Nota da prova de Linguagens e Códigos (escalonada via TRI). |
| `NU_NOTA_MT` | Notas Objetivas | Nota da prova de Matemática (escalonada via TRI). |
| `TX_RESPOSTAS_CN` | Respostas | Vetor das respostas do participante na prova de Ciências da Natureza. |
| `TX_RESPOSTAS_CH` | Respostas | Vetor das respostas do participante na prova de Ciências Humanas. |
| `TX_RESPOSTAS_LC` | Respostas | Vetor das respostas do participante na prova de Linguagens e Códigos. |
| `TX_RESPOSTAS_MT` | Respostas | Vetor das respostas do participante na prova de Matemática. |
| `TP_LINGUA` | Prova Objetiva | Língua Estrangeira escolhida (0: Inglês, 1: Espanhol). |
| `TX_GABARITO_CN` | Gabarito | Vetor do gabarito oficial da prova de Ciências da Natureza. |
| `TX_GABARITO_CH` | Gabarito | Vetor do gabarito oficial da prova de Ciências Humanas. |
| `TX_GABARITO_LC` | Gabarito | Vetor do gabarito oficial da prova de Linguagens e Códigos. |
| `TX_GABARITO_MT` | Gabarito | Vetor do gabarito oficial da prova de Matemática. |
| `TP_STATUS_REDACAO` | Redação Final | Situação/status final da redação. |
| `NU_NOTA_COMP1` | Redação Final | Nota final na Competência 1 (Domínio da norma culta). |
| `NU_NOTA_COMP2` | Redação Final | Nota final na Competência 2 (Compreensão do tema/tipo textual). |
| `NU_NOTA_COMP3` | Redação Final | Nota final na Competência 3 (Organização/projeto de texto). |
| `NU_NOTA_COMP4` | Redação Final | Nota final na Competência 4 (Coesão e conectivos). |
| `NU_NOTA_COMP5` | Redação Final | Nota final na Competência 5 (Proposta de intervenção). |
| `NU_NOTA_REDACAO` | Redação Final | Nota total consolidada da redação (0 a 1000). |
| `TP_STATUS_REDACAO_AV1` | Redação AV1 | Status da redação atribuído pelo Avaliador 1. |
| `NU_NOTA_AV1` | Redação AV1 | Nota total da redação atribuída pelo Avaliador 1. |
| `NU_NOTA_COMP1_AV1` | Redação AV1 | Nota na Competência 1 atribuída pelo Avaliador 1. |
| `NU_NOTA_COMP2_AV1` | Redação AV1 | Nota na Competência 2 atribuída pelo Avaliador 1. |
| `NU_NOTA_COMP3_AV1` | Redação AV1 | Nota na Competência 3 atribuída pelo Avaliador 1. |
| `NU_NOTA_COMP4_AV1` | Redação AV1 | Nota na Competência 4 atribuída pelo Avaliador 1. |
| `NU_NOTA_COMP5_AV1` | Redação AV1 | Nota na Competência 5 atribuída pelo Avaliador 1. |
| `TP_STATUS_REDACAO_AV2` | Redação AV2 | Status da redação atribuído pelo Avaliador 2. |
| `NU_NOTA_AV2` | Redação AV2 | Nota total da redação atribuída pelo Avaliador 2. |
| `NU_NOTA_COMP1_AV2` | Redação AV2 | Nota na Competência 1 atribuída pelo Avaliador 2. |
| `NU_NOTA_COMP2_AV2` | Redação AV2 | Nota na Competência 2 atribuída pelo Avaliador 2. |
| `NU_NOTA_COMP3_AV2` | Redação AV2 | Nota na Competência 3 atribuída pelo Avaliador 2. |
| `NU_NOTA_COMP4_AV2` | Redação AV2 | Nota na Competência 4 atribuída pelo Avaliador 2. |
| `NU_NOTA_COMP5_AV2` | Redação AV2 | Nota na Competência 5 atribuída pelo Avaliador 2. |
| `TP_STATUS_REDACAO_AV3` | Redação AV3 | Status da redação atribuído pelo Avaliador 3 (terceira correção/desempate). |
| `NU_NOTA_AV3` | Redação AV3 | Nota total da redação atribuída pelo Avaliador 3. |
| `NU_NOTA_COMP1_AV3` | Redação AV3 | Nota na Competência 1 atribuída pelo Avaliador 3. |
| `NU_NOTA_COMP2_AV3` | Redação AV3 | Nota na Competência 2 atribuída pelo Avaliador 3. |
| `NU_NOTA_COMP3_AV3` | Redação AV3 | Nota na Competência 3 atribuída pelo Avaliador 3. |
| `NU_NOTA_COMP4_AV3` | Redação AV3 | Nota na Competência 4 atribuída pelo Avaliador 3. |
| `NU_NOTA_COMP5_AV3` | Redação AV3 | Nota na Competência 5 atribuída pelo Avaliador 3. |
| `TP_STATUS_REDACAO_AV4` | Redação AV4 | Status da redação atribuído pela Banca Examinadora (AV4). |
| `NU_NOTA_AV4` | Redação AV4 | Nota total da redação atribuída pela Banca Examinadora (AV4). |
| `NU_NOTA_COMP1_AV4` | Redação AV4 | Nota na Competência 1 atribuída pela Banca Examinadora (AV4). |
| `NU_NOTA_COMP2_AV4` | Redação AV4 | Nota na Competência 2 atribuída pela Banca Examinadora (AV4). |
| `NU_NOTA_COMP3_AV4` | Redação AV4 | Nota na Competência 3 atribuída pela Banca Examinadora (AV4). |
| `NU_NOTA_COMP4_AV4` | Redação AV4 | Nota na Competência 4 atribuída pela Banca Examinadora (AV4). |
| `NU_NOTA_COMP5_AV4` | Redação AV4 | Nota na Competência 5 atribuída pela Banca Examinadora (AV4). |