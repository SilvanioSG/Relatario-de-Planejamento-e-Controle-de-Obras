# Relatório de Planejamento e Controle de Obras (PCO) — Casa Térrea 10x25

## Autor

**Silvanio Gois** — Gestor de Operações e Negócios Orientado a Dados

- Website: https://www.silvaniogois.com.br
- LinkedIn: https://www.linkedin.com/in/silvanio-gois/
- GitHub: https://github.com/SilvanioSG

---

## 1. Objeto do Projeto

Este projeto consiste na construção de um **relatório analítico de Planejamento e Controle de Obras (PCO)** aplicado a uma residência térrea de dimensões 10 x 25 metros, executada ao longo de aproximadamente seis meses (janeiro a junho de 2024). O objeto de estudo é o comportamento físico-financeiro real da obra em contraste com o planejamento original, avaliado sob a ótica de Gestão de Valor Agregado (Earned Value Management — EVM), análise de desvios, produtividade de mão de obra e fluxo de medições.

O projeto integra disciplinas de Engenharia Civil (planejamento, orçamentação e controle) com técnicas de Análise de Dados e Business Intelligence, transformando uma base operacional de controle de obra em um produto analítico capaz de subsidiar decisões gerenciais e servir de modelo replicável para empreendimentos futuros.

---

## 2. Origem dos Dados

A base de dados foi construída a partir do acompanhamento real da obra, consolidada em um arquivo Excel estruturado (`PCO_CasaTerrea10x25.xlsx`) composto por oito abas interdependentes:

| Aba | Conteúdo |
|---|---|
| `Base_Corrigida` | EAP completa, orçamento unitário e total, durações planejadas e reais, custos, equipes e status de execução por serviço |
| `Curva_S_Diaria` | Série temporal diária com VP, VA, CR, índices IDP e IDC, VPR e VCR |
| `Calendario` | Calendário de obra com dias úteis, fins de semana e feriados |
| `Medicoes` | Medições mensais acumuladas e percentual físico-financeiro |
| `Resumo_Etapa` | Consolidação por etapa (custo, prazo, mão de obra e desvios) |
| `KPIs` | Indicadores executivos consolidados na data de corte |
| `Histograma_MO` | Alocação diária de mão de obra por função, etapa e semana |
| `Cronograma_Diario` | Distribuição diária de VP, VA e CR por serviço (EAP) |

Os dados **não são sintéticos**: representam a execução real de uma obra residencial, o que confere ao projeto valor analítico autêntico e aderência a cenários práticos de gestão.

---

## 3. Objetivo Analítico e Business Intelligence

O projeto foi concebido para responder, com base em dados, às seguintes perguntas de negócio:

**Pergunta de negócio principal:**
> A obra foi entregue dentro do prazo e do orçamento planejados? Em quais etapas houve maior desvio e quais fatores explicam esse comportamento?

**Perguntas secundárias:**
- Como evoluiu a performance de prazo (IDP) e de custo (IDC) ao longo do ciclo?
- Quais etapas da EAP concentraram maior desvio de custo e de prazo?
- Qual foi o comportamento do fluxo financeiro mensal frente ao cronograma físico?
- Qual o nível de utilização de mão de obra por função e onde estão os picos de demanda?
- Qual o custo final projetado (EAC) e a variação esperada no término (VAC)?

O intuito é aplicar técnicas de Análise de Dados e conceitos de Business Intelligence a um domínio tradicionalmente tratado por planilhas operacionais, elevando o padrão da gestão de obras por meio de visualizações, KPIs e narrativa analítica.

---

## 4. Metodologia Técnica Adotada

O projeto foi conduzido em seis etapas encadeadas:

### 4.1 Engenharia e Modelagem de Dados
- Leitura estruturada das oito abas do Excel com `pandas`.
- Normalização de tipos (datas, numéricos, categóricos).
- Validação de consistência entre VP, VA, CR e medições.
- Estruturação do calendário de obra para análise temporal em dias úteis.

### 4.2 Gestão de Valor Agregado (EVM)
- Cálculo de **VP (Valor Planejado)**, **VA (Valor Agregado)** e **CR (Custo Real)** em base diária e acumulada.
- Cálculo dos índices **IDP = VA / VP** (desempenho de prazo) e **IDC = VA / CR** (desempenho de custo).
- Apuração de **VPR (Variação de Prazo)** e **VCR (Variação de Custo)**.
- Projeção de **EAC (Estimativa no Término)** e **ETC (Estimativa para Concluir)**.

### 4.3 Análise de Desvios
- Comparação por etapa entre custo planejado e realizado (absoluto e percentual).
- Comparação entre duração planejada e real por serviço da EAP.
- Ranking dos maiores ofensores de prazo e de custo.

### 4.4 Análise de Produtividade e Mão de Obra
- Consolidação de Homem-Dia (Hh) por função e por etapa.
- Heatmap Etapa x Mês para identificação de picos e sobreposição de frentes.

### 4.5 Análise Financeira
- Curva S acumulada (VP x VA x CR) com destaque de zona de atraso.
- Evolução mensal das medições e do acumulado financeiro.

### 4.6 Dashboard Executivo
- Painel único consolidando IDP, IDC, VP, VA, CR até o corte, avanço físico e projeções.
- Tabela sumarizada de KPIs e recomendações gerenciais.

### Ferramentas Utilizadas
- **Python 3** — linguagem de análise
- **pandas / numpy** — manipulação e modelagem de dados
- **matplotlib / seaborn** — visualização analítica
- **Jupyter Notebook** — ambiente de desenvolvimento e relatório técnico
- **nbconvert** — exportação do relatório final em HTML e PDF

---

## 5. Resultados e Insights Analíticos

A obra foi **concluída com avanço físico de 100%** dentro do horizonte analisado, com desempenho consolidado superior ao planejado em ambas as dimensões de controle:

- **Desempenho de Custo (IDC final ≈ 1,026):** o custo real ficou **abaixo do planejado**, gerando economia financeira positiva (VCR positivo).
- **Desempenho de Prazo (IDP final ≈ 1,000):** a obra foi entregue **no prazo**, sem variação relevante acumulada.
- **Custo Final Projetado (EAC):** levemente inferior ao orçamento inicial, indicando maturidade do planejamento.

### Principais Insights

1. **Concentração de economia em etapas de acabamento.** MURO, REVESTIMENTO e PINTURA apresentaram os maiores desvios positivos de custo, sugerindo ganho de escala ou negociação eficiente de insumos nessas frentes.
2. **Atenção pontual em ALVENARIA.** Foi a etapa com desvio de custo negativo mais relevante, sinalizando oportunidade de revisão de composições unitárias e reaproveitamento de traço em obras futuras.
3. **Desvios de prazo positivos localizados.** Serviços de ALVENARIA e REVESTIMENTO tiveram duração real superior à planejada, mas foram absorvidos pela folga do cronograma sem impacto no término global.
4. **Alta concentração de mão de obra em poucas funções.** Pedreiro + Ajudantes e Encanador responderam pela maior parcela do Homem-Dia total, evidenciando pontos críticos de dimensionamento de equipe.
5. **Fluxo financeiro aderente ao cronograma físico.** A curva de medições mensais acompanhou a evolução física, sem antecipações ou atrasos materiais no faturamento.

### Recomendações Gerenciais Derivadas
- Padronizar composições de ALVENARIA para reduzir variabilidade de custo.
- Implantar alertas automáticos quando IDP ou IDC < 0,95.
- Automatizar a geração da Curva S a partir do cronograma (já estruturado na aba `Curva_S_Diaria`).
- Reutilizar o notebook como template para novos empreendimentos, bastando substituir a base Excel.

---

## 6. Arquivos do Projeto

### Arquivos de Entrada
| Arquivo | Descrição |
|---|---|
| `PCO_CasaTerrea10x25.xlsx` | Base consolidada da obra, com todas as abas de orçamento, cronograma, EVM, medições, KPIs e histograma de mão de obra |

### Arquivos Gerados
| Arquivo | Descrição |
|---|---|
| `Relatorio_PCO_CasaTerrea10x25.IPYNB` | Notebook analítico completo com todo o pipeline de dados, cálculos, visualizações e narrativa |
| `Relatorio_PCO_CasaTerrea10x25.html` | Versão web do relatório (sem código visível), própria para apresentação e leitura |
| `Relatorio_PCO_CasaTerrea10x25.pdf` | Versão PDF do relatório, própria para envio corporativo e arquivamento |
| `SG_Site.png` | Imagem institucional utilizada no cabeçalho do notebook |

---

## 7. Competências Demonstradas

- Planejamento e Controle de Obras (PCO) com aplicação de EVM.
- Modelagem e engenharia de dados em Python.
- Construção de Curva S, índices de desempenho e projeções de término.
- Análise de desvios físicos e financeiros.
- Análise de produtividade e histograma de mão de obra.
- Data Storytelling técnico aplicado a relatórios executivos.
- Business Intelligence orientado à decisão gerencial em construção civil.
- Automação de relatórios analíticos e exportação multiplataforma (HTML/PDF).

---

## 8. Como Reproduzir

1. Clonar este repositório.
2. Garantir que `PCO_CasaTerrea10x25.xlsx` e `SG_Site.png` estejam na raiz do projeto.
3. Instalar as dependências:
4. Abrir o notebook `Relatorio_PCO_CasaTerrea10x25.IPYNB` no Jupyter.
5. Executar todas as células em ordem (Run All).

Para gerar as versões de apresentação:
jupyter nbconvert --to html --no-input --output Relatorio_PCO_CasaTerrea10x25.html Relatorio_PCO_CasaTerrea10x25.IPYNB

---

## 9. Contato

**Silvanio Gois** — Gestor de Operações e Negócios Orientado a Dados

- Website: https://www.silvaniogois.com.br
- LinkedIn: https://www.linkedin.com/in/silvanio-gois/
- GitHub: https://github.com/SilvanioSG
- E-mail: sg@silvaniogois.com.br