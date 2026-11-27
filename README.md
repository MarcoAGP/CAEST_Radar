# CAEST Radar — Marketing digital do CAEST

Painel de análise do Instagram do CAEST da UNEMAT e da pesquisa de percepção estudantil em Rondonópolis e Alto Araguaia. O projeto compara o que os estudantes dizem precisar com os temas e formatos publicados pelo perfil. Essa comparação subsidia o planejamento editorial do CAEST de Barra do Bugres.

A aplicação funciona localmente em um navegador moderno. A interface, os estilos, os gráficos e a lógica de importação estão em um único HTML, escrito em HTML5, CSS e JavaScript. Basta abrir o arquivo e selecionar os relatórios. Não há instalação de pacotes, servidor, credenciais da Meta ou etapa de consolidação em Excel.

## Estrutura do repositório

| Caminho                                                                  | Conteúdo                                             |
| ------------------------------------------------------------------------ | ---------------------------------------------------- |
| [CAEST_Radar_V3_CSV_Originais.html](./CAEST_Radar_V3_CSV_Originais.html) | Aplicação que deve ser aberta no navegador           |
| [CSV/](./CSV/)                                                           | Relatórios de entrada do Instagram e do questionário |
| README.md                                                                | Guia de uso e interpretação                          |
| LICENSE                                                                  | Arquivo de licença MIT.                              |

## Primeira execução

1. No GitHub, abra **Code → Download ZIP** e extraia a pasta do projeto. Também é possível usar uma cópia clonada do repositório.
2. Abra **CAEST_Radar_V3_CSV_Originais.html** no navegador. A tela inicial aguarda a importação. A pasta `CSV/` organiza os arquivos e a seleção é feita a cada sessão.
3. Em **Bases e filtros independentes**, mantenha **Detectar automaticamente** e clique em **Carregar CSVs originais**. Selecione os arquivos desejados dentro de `CSV/` ou arraste-os para a área de importação.
4. Leia o resultado de cada arquivo e confira no inventário as quantidades, a cobertura e as datas. É possível começar apenas com o questionário ou com o relatório de publicações.
5. Escolha os filtros, confira os campos reconhecidos e revise os temas das legendas antes de interpretar os cruzamentos. Exporte os resultados de interesse antes de recarregar ou fechar a página.

## Arquivos de entrada

Os nomes abaixo exemplificam os relatórios esperados. Preserve os cabeçalhos e, nos relatórios com várias seções, a estrutura original da exportação.

| Arquivo em CSV/                                                                                                                      | O que o painel utiliza                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Respostas do Google Forms, `Pesquisa sobre o Instagram do CAEST da UNEMAT — Rondonópolis e Alto Araguaia.csv` com o nome da pesquisa | Campus, curso e respostas às perguntas sobre canal, exposição, eficácia, imagem institucional, formato, assunto, utilidade e sugestões |
| CSV de publicações da Meta, `Feb-28-2026_Nov-08-2026_1480283953982101.csv` geralmente identificado pelo intervalo de datas           | Uma linha por publicação, com data, formato, identificação ou legenda e métricas disponíveis                                           |
| Views.csv                                                                                                                            | Visualizações por dia                                                                                                                  |
| Reach.csv                                                                                                                            | Alcance por dia                                                                                                                        |
| Interactions.csv                                                                                                                     | Interações por dia                                                                                                                     |
| Visits.csv                                                                                                                           | Visitas por dia                                                                                                                        |
| Link clicks.csv                                                                                                                      | Cliques em links por dia                                                                                                               |
| Follows.csv                                                                                                                          | Novos seguidores registrados por dia                                                                                                   |
| Top content formats.csv                                                                                                              | Quantidades agregadas por formato, conforme a exportação                                                                               |
| Audience.csv                                                                                                                         | Retrato dos seguidores, com total, distribuição por idade e gênero e principais cidades e países, conforme disponibilidade             |

O importador aceita arquivos de texto com extensões `.csv`, `.tsv` e `.txt`, com vírgula, ponto e vírgula ou tabulação. Reconhece UTF-8 e variantes de UTF-16 e tenta Windows-1252 quando a leitura em UTF-8 produz caracteres inválidos. Para datas com barras, interpreta o questionário como dia/mês/ano e os relatórios Meta como mês/dia/ano. Também reconhece datas em `AAAA-MM-DD`.

### Como atualizar as bases

- **Questionário e publicações.** Cada nova importação substitui a base correspondente. Para analisar todo o período, carregue a exportação completa desejada. Nas publicações com ID repetido, prevalece a última ocorrência.
- **Séries diárias.** Os seis relatórios individuais são combinados pela data. Reimportar uma métrica substitui a série inteira daquela métrica e preserva as demais. Valores ausentes permanecem ausentes.
- **Importação em lote.** Use detecção automática e inclua um relatório de cada tipo por lote. Se algum falhar, confira a mensagem específica. Os demais podem ter sido importados com sucesso.
- **Troca de conta.** Exporte as revisões que deseja guardar, use **Limpar todas as bases** e carregue os arquivos da nova conta. Prefira relatórios com intervalos equivalentes.

## Filtros e escopo

| Controle                         | Dados afetados                                                                                                       |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Campus e curso                   | Respostas do questionário. A lista de cursos acompanha o campus escolhido.                                           |
| Perfil                           | Publicações atribuídas à conta selecionada.                                                                          |
| Início e fim                     | Data de publicação e datas da série diária. O questionário e o retrato de audiência mantêm seus próprios escopos.    |
| Série diária: origem confirmada? | Permite declarar que a série importada pertence ao perfil selecionado. Confira a conta de origem antes de confirmar. |

## Leituras disponíveis

- **Questionário.** Distribuições por campus e curso, canais preferidos, exposição declarada, eficácia percebida, imagem institucional, formatos, assuntos e utilidade em escala de 1 a 5. A conferência dos campos permite distinguir uma pergunta sem respostas de um cabeçalho que o importador deixou de reconhecer. As sugestões têm leitura integral e agrupamento indicativo por palavras-chave.
- **Instagram.** Regularidade mensal, distribuição e desempenho por formato, ranking das dez publicações com maior valor na métrica escolhida, séries diárias agregadas por mês e retrato da audiência.
- **Análises cruzadas.** Compare, por exemplo, campus e canal preferido, exposição e eficácia percebida, ou preferência dos respondentes e oferta editorial. Os cruzamentos entre questionário e Instagram usam grupos e proporções. A aplicação não identifica qual respondente visualizou uma publicação específica.
- **Diretrizes editoriais.** O painel relaciona evidências do recorte a decisões e indicadores, propõe um calendário semanal para Barra do Bugres e apresenta um protocolo de acompanhamento. As metas servem ao planejamento de um piloto.
- **Auditoria.** Confira dados ausentes e classificação editorial, procure publicações pela legenda, formato ou tema e ajuste o tema sugerido. A alteração recebe a marca **Manual** e pode ser exportada.

## Como interpretar os indicadores

| Indicador                       | Cálculo ou limite de interpretação                                                                                                                |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Percentual do questionário      | Contagem da alternativa dividida pelo número de respostas válidas da pergunta no recorte. Perguntas distintas podem ter denominadores diferentes. |
| Interações por publicação       | Soma de curtidas, comentários, compartilhamentos e salvamentos. O cálculo exige os quatro componentes.                                            |
| Taxa de engajamento por alcance | 100 × interações ÷ alcance da publicação, quando as interações estão completas e o alcance é positivo.                                            |
| Taxa ponderada                  | 100 × soma das interações ÷ soma do alcance, considerando apenas as publicações elegíveis para o cálculo da taxa.                                 |
| Alcance diário somado           | Uma mesma conta pode ser alcançada em vários dias. O total mensal dessa série pode contar a mesma conta mais de uma vez.                          |
| Desempenho por formato          | As medianas resumem o desempenho por publicação. Observe também o número de publicações de cada formato.                                          |

As métricas das publicações são acumuladas até a exportação (_Lifetime_). Ao filtrar por data, o painel seleciona as publicações feitas naquele intervalo. Uma publicação antiga pode ter acumulado interações durante mais tempo que uma recente.

A ausência de Stories no relatório individual pode refletir a cobertura do arquivo. Consulte o relatório agregado de formatos antes de interpretar essa ausência. Na análise do TCC, registre o perfil, o período, a data da exportação, o número de observações válidas e as revisões manuais. As associações observadas sustentam hipóteses de comunicação e não demonstram causalidade.

## Exportação e privacidade

| Ação                                          | Resultado                                                                                                                                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Exportar CSV de publicações classificadas** | Gera `caest_publicacoes_classificadas.csv` com toda a base de publicações da sessão, métricas, tema e marca de revisão, inclusive registros fora do filtro atual.                                   |
| **Exportar snapshot JSON**                    | Gera `caest_dados_analisados.json` com as bases carregadas e as informações de origem. Pode incluir respostas abertas. A interface importa relatórios de texto e não oferece restauração pelo JSON. |
| **Imprimir / PDF**                            | Abre a impressão do navegador. Escolha salvar em PDF para guardar a visualização.                                                                                                                   |

O processamento ocorre no navegador. Publicar arquivos na pasta `CSV/` de um repositório público torna esses arquivos acessíveis a terceiros, inclusive colunas que o painel não exibe. Antes de publicar a pesquisa, revise cabeçalhos, identificadores e textos livres. Quando necessário, disponibilize uma cópia anonimizada, preservando o texto das perguntas para que o painel reconheça os campos.

## Solução de problemas

| Situação                                                   | O que conferir                                                                                                                                                      |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O HTML abriu com os painéis vazios                         | Selecione os CSVs no importador e verifique o inventário.                                                                                                           |
| Curso, eficácia, utilidade ou sugestões aparecem sem dados | Em **Conferência dos campos do questionário**, verifique o cabeçalho associado e o preenchimento. Remova os filtros de campus e curso para conferir a base inteira. |
| Um segundo relatório do mesmo tipo foi recusado            | Importe-o separadamente se a intenção for substituir a versão anterior.                                                                                             |
| A taxa de uma publicação está ausente                      | Verifique se o alcance é positivo e se há valores nos quatro componentes de interação.                                                                              |
| Datas ou totais parecem incompatíveis                      | Confira o formato de data, o perfil, a cobertura de cada arquivo e a diferença entre métricas diárias e acumuladas por publicação.                                  |

## Licença

Este projeto está sobre a licença **MIT**. Veja o arquivo [`LICENSE`](LICENSE) na raiz do repositório para mais detalhes.
