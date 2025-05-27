# Impacto das Enchentes no Rio Grande do Sul na Saúde Mental: Análise de Dados do SUS

Este repositório contém um notebook de análise dos impactos das enchentes de 2024 no Rio Grande do Sul sobre os atendimentos de saúde mental, utilizando dados públicos do SUS (SIA) e CID-10.

Os dados fundamentaram a reportagem ["Atendimentos relacionados a saúde mental têm pico histórico no RS após enchente"](https://www1.folha.uol.com.br/equilibrioesaude/2025/05/atendimentos-relacionados-a-saude-mental-tem-pico-historico-no-rs-apos-enchente.shtml), publicada em 25 de maio de 2025 na edição impressa da Folha de S. Paulo.

## Metodologia

O processamento de dados para essa análise foi feito a partir da [PySUS](https://pysus.readthedocs.io/en/latest/), biblioteca Python projetada para facilitar o trabalho com os dados abertos do SUS. Para a verificação ambulatorial, a reportagem filtrou os CIDs (Classificação Internacional de Doenças) que começam com a letra "F" –ligados a transtornos mentais e comportamentais, que resultaram ema 6,3 milhões de registros.

Para garantir que só fossem analisadas interações diretas com pacientes, como consultas, uma terceira filtragem selecionou apenas códigos específicos de procedimentos de consulta ou atendimento. 

Para a análise dos Caps, os dados foram filtrados já de início pela CID "F" e pelos códigos dos locais de atendimento.

## Estrutura do Projeto

- `saudemental_RS_1ano.ipynb`: Notebook principal com todo o pipeline de ETL, análise e visualização.
- `municipios_RS.csv`: Lista de municípios do RS selecionados para a análise.
- `TD_Tab_SUS_Anexos_Repositorio_IPEA_Revisto_14_de_agosto_de_2023.xlsx`: Dicionários de procedimentos do SUS.
- `CID-10-SUBCATEGORIAS.CSV`: Dicionário de diagnósticos CID-10.

## Como reproduzir

1. **Instale as dependências**:
   ```bash
   pip install pandas duckdb matplotlib seaborn pyarrow tqdm
   ```

2. **Obtenha os dados**:
   - Baixe os arquivos do Datasus conforme instruções no notebook.
   - Coloque os arquivos auxiliares (`municipios_RS.csv`, CID-10, etc) na mesma pasta do notebook.

3. **Execute o notebook**:
   - Siga as células na ordem, ajustando caminhos se necessário.

## Principais etapas

- **ETL**: Download, filtragem e empilhamento dos dados ambulatoriais do SUS.
- **Análise**: Cálculo de médias mensais de atendimentos antes e depois das enchentes, por município e diagnóstico.
- **Visualização**: Gráficos e tabelas comparando períodos e destacando variações relevantes.

## Resultados

- Tabelas e gráficos mostram o aumento (ou redução) de atendimentos de saúde mental após as enchentes, com destaque para diagnósticos mais frequentes.
- Resultados detalhados por município.
