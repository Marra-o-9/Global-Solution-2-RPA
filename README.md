# Projeto: Previsão de Preço de Energia com Base em Temperatura

Este projeto visa prever o preço da energia elétrica utilizando dados históricos de temperatura e preço da energia no estado da Califórnia, EUA, entre 2020 e 2023. A previsão é feita utilizando um modelo de regressão linear, e os dados são coletados de duas APIs: a API da EIA (Energy Information Administration) para dados de energia e a API Open-Meteo para dados climáticos.

## Visão Geral

O objetivo é entender como as variações na temperatura influenciam os preços da energia elétrica. Para isso, o projeto realiza a coleta de dados de duas fontes externas, processa esses dados, treina um modelo de regressão linear e gera previsões que podem ser usadas para entender tendências futuras no preço da energia com base na temperatura.

## Funcionalidades

1. **Coleta de Dados de Energia**: Utiliza a API da EIA para buscar dados mensais de preço da energia entre janeiro de 2020 e dezembro de 2023.
2. **Coleta de Dados Climáticos**: Utiliza a API Open-Meteo para buscar dados históricos de temperatura para a Califórnia entre janeiro de 2020 e dezembro de 2023.
3. **Processamento de Dados**: Os dados climáticos e de energia são combinados, padronizados e processados para garantir que estejam alinhados temporalmente.
4. **Modelo de Previsão**: Um modelo de regressão linear é treinado para prever o preço da energia com base na temperatura.
5. **Armazenamento dos Dados**: Os dados processados são armazenados em um banco de dados SQLite e também são exportados para um arquivo CSV.
6. **Visualização**: O projeto gera um gráfico que compara os dados reais e as previsões do modelo, além de salvar o gráfico em um arquivo PNG.

## Requisitos

Antes de executar o projeto, é necessário garantir que você tenha os seguintes pacotes Python instalados:

- `requests`: Para realizar as requisições às APIs.
- `sqlite3`: Para manipulação de banco de dados SQLite.
- `pandas`: Para manipulação e análise de dados.
- `scikit-learn`: Para treinamento do modelo de regressão linear.
- `matplotlib`: Para visualização de dados.
- `time`: Para manipulação de datas e horas.

Você pode instalar as dependências necessárias com o seguinte comando:

```bash
pip install requests pandas scikit-learn matplotlib
```

## APIs Utilizadas

### 1. **API da EIA (Energy Information Administration)**
- **URL da API**: [https://api.eia.gov/v2/electricity/retail-sales/data/](https://api.eia.gov/v2/electricity/retail-sales/data/)
- **Função**: A API fornece dados mensais de preço de energia elétrica nos Estados Unidos. Utilizamos os dados para o estado da Califórnia entre 2020 e 2023.
- **Parâmetros utilizados**:
  - `start`: "2020-01" (data de início)
  - `end`: "2023-12" (data de término)
  - `frequency`: "monthly" (dados mensais)
  - `data[0]`: "price" (informação sobre preço da energia)
  - `facets[stateid][]`: "CA" (dados para o estado da Califórnia)

### 2. **API Open-Meteo**
- **URL da API**: [https://archive-api.open-meteo.com/v1/era5](https://archive-api.open-meteo.com/v1/era5)
- **Função**: A API fornece dados históricos de temperatura, permitindo o acesso a informações de temperatura horária para um intervalo de datas específico.
- **Parâmetros utilizados**:
  - `latitude`: 36.7783 (latitude da Califórnia)
  - `longitude`: -119.4179 (longitude da Califórnia)
  - `start_date`: "2020-01-01" (data de início)
  - `end_date`: "2023-12-31" (data de término)
  - `hourly`: "temperature_2m" (temperatura medida a cada hora)

## Como Usar

1. **Configuração do Projeto**:
   - Defina a chave da API da EIA (`EIA_API_KEY`) no código.
   - Certifique-se de ter uma conexão à internet para acessar as APIs.

2. **Executando o Script**:
   Execute o script Python para coletar, processar e analisar os dados:

   ```bash
   python energia_sustentavel.py
   ```

3. **Saídas Esperadas**:
   - Um arquivo CSV contendo os dados de energia e clima processados: `energia_sustentavel.csv`.
   - Um banco de dados SQLite com os dados armazenados na tabela `consumo_energia` no arquivo `energia_sustentavel.db`.
   - Um gráfico comparando os preços reais da energia com as previsões geradas pelo modelo, salvo em `previsao_energia.png`.

## Estrutura do Código

- **Funções**:
  - `convert_date_to_timestamp(date_str)`: Converte uma data para timestamp UNIX.
  - `fetch_energy_data()`: Coleta os dados de preço da energia da API da EIA.
  - `fetch_weather_data()`: Coleta os dados climáticos da API Open-Meteo.
  - `process_data(energy_data, weather_data)`: Processa e combina os dados de energia e clima.
  - `save_to_storage(dataframe)`: Salva os dados processados em um arquivo CSV e banco de dados SQLite.
  - `train_model(dataframe)`: Treina o modelo de regressão linear para prever o preço da energia com base na temperatura.
  - `plot_predictions(model, dataframe)`: Plota um gráfico comparando os dados reais com as previsões do modelo.

## Resultados

Após a execução do script, você terá:

- Um modelo de regressão linear treinado, com uma avaliação de precisão (R²) mostrando o desempenho do modelo.
- Previsões de preços de energia com base na temperatura.
- Um arquivo de visualização (PNG) comparando os dados reais com as previsões.

## Conclusão

Este projeto permite entender como as variações de temperatura podem impactar os preços da energia elétrica. Ele oferece uma visão sobre a relação entre clima e consumo de energia, algo valioso para empresas de energia e consumidores que buscam compreender padrões de consumo e otimizar seus custos.