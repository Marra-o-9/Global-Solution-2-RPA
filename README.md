### Projeto: Previsão de Preço de Energia com Base em Temperatura e Consumo Energético  

Este projeto visa prever o preço da energia elétrica utilizando dados históricos de **temperatura**, **preço da energia** e **consumo energético** no estado da Califórnia, EUA, entre 2020 e 2023. A previsão é feita utilizando um **modelo de regressão linear**. Os dados são coletados de três APIs principais: a API da EIA (Energy Information Administration) para dados de energia, a API Open-Meteo para dados climáticos e uma API adicional de consumo energético.

---

## Visão Geral  

O objetivo do projeto é entender como as variações de **temperatura** e **consumo energético** influenciam os preços da energia elétrica. Para isso, o projeto realiza:  
- Coleta de dados de três fontes externas,  
- Processamento e integração dos dados,  
- Treinamento de um modelo de regressão linear,  
- Geração de previsões.  

O resultado pode ser usado para antecipar tendências futuras no preço da energia com base em condições climáticas e padrões de consumo.

---

## Funcionalidades  

1. **Coleta de Dados de Energia**:  
   - Utiliza a API da EIA para buscar dados mensais de preço e consumo de energia entre janeiro de 2020 e dezembro de 2023.  

2. **Coleta de Dados Climáticos**:  
   - Utiliza a API Open-Meteo para buscar dados históricos de temperatura para a Califórnia no mesmo período.  

3. **Integração de Dados**:  
   - Combina e padroniza os dados de energia e clima com os de consumo energético, garantindo alinhamento temporal e consistência.  

4. **Treinamento de Modelo**:  
   - Um modelo de **regressão linear múltipla** é treinado para prever o preço da energia com base em temperatura e consumo.  

5. **Armazenamento e Visualização**:  
   - Os dados processados são armazenados em um banco de dados SQLite e exportados para CSV.  
   - Um gráfico é gerado comparando preços reais e previsões, salvo em PNG.  

---

## Requisitos  

Certifique-se de ter os seguintes pacotes Python instalados:  

- `requests`: Requisições às APIs.  
- `sqlite3`: Banco de dados SQLite.  
- `pandas`: Manipulação de dados.  
- `scikit-learn`: Treinamento do modelo.  
- `matplotlib`: Visualização.  

Instale com:  
```bash
pip install requests pandas scikit-learn matplotlib
```

---

## APIs Utilizadas  

### **API da EIA (Energy Information Administration)**  
- **URL**: [https://api.eia.gov/v2/electricity/retail-sales/data/](https://api.eia.gov/v2/electricity/retail-sales/data/)  
- **Função**: Fornece dados de preço e consumo mensal de energia elétrica.  

### **API Open-Meteo**  
- **URL**: [https://archive-api.open-meteo.com/v1/era5](https://archive-api.open-meteo.com/v1/era5)  
- **Função**: Fornece dados históricos de temperatura horária.  

---

## Como Usar  

1. **Configuração do Projeto**:  
   - Configure as chaves de API no arquivo `.env`.  
   - Certifique-se de ter conexão à internet.  

2. **Executar o Script**:  
```bash
python previsao_energia.py
```  

3. **Resultados Esperados**:  
   - Dados combinados no arquivo CSV: `dados_processados.csv`.  
   - Banco de dados SQLite: `energia.db`.  
   - Gráfico salvo em `previsao_precos.png`.  

---

## Estrutura do Código  

- **Funções**:  
  - `fetch_energy_data()`: Busca dados de energia da API da EIA.  
  - `fetch_weather_data()`: Busca dados climáticos da API Open-Meteo.  
  - `integrate_data()`: Integra os dados de preço, temperatura e consumo.  
  - `train_model()`: Treina um modelo de regressão linear múltipla.  
  - `plot_results()`: Gera um gráfico comparativo entre dados reais e previstos.  

---

## Resultados  

O modelo de regressão linear múltipla permite prever preços da energia com base em:  
- **Temperatura média diária**.  
- **Consumo energético mensal**.  

O desempenho do modelo é avaliado pelo coeficiente de determinação (R²), permitindo análises precisas.  

---

## Conclusão  

Este projeto demonstra como dados climáticos e padrões de consumo podem ser utilizados para prever preços de energia. Ele fornece insights úteis para empresas e consumidores interessados em otimizar o uso de energia e custos.  

