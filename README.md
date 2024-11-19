# Projeto: Previsão de Preço de Energia com Base em Temperatura e Consumo Energético  

Este projeto visa prever o preço da energia elétrica utilizando dados históricos de **temperatura**, **preço da energia** e **consumo energético** no estado da Califórnia, EUA, entre 2020 e 2023. A previsão é feita utilizando modelos de **regressão linear** e **Random Forest**. Os dados são coletados de três APIs principais: a API da EIA (Energy Information Administration) para dados de energia, a API Open-Meteo para dados climáticos e uma API adicional de consumo energético.

---

## Visão Geral  

O objetivo do projeto é entender como as variações de **temperatura** e **consumo energético** influenciam os preços da energia elétrica. Para isso, o projeto realiza:  
- Coleta de dados de três fontes externas;  
- Processamento e integração dos dados;  
- Treinamento de modelos de regressão linear e Random Forest;  
- Geração de previsões.  

O resultado pode ser usado para antecipar tendências futuras no preço da energia com base em condições climáticas e padrões de consumo.

---

## Funcionalidades  

1. **Coleta de Dados de Energia**:  
   - Utiliza a API da EIA para buscar dados mensais de preço e consumo de energia entre janeiro de 2020 e dezembro de 2023.  

2. **Coleta de Dados Climáticos**:  
   - Utiliza a API Open-Meteo para buscar dados históricos de temperatura horária para a Califórnia no mesmo período.  

3. **Integração de Dados**:  
   - Combina e padroniza os dados de energia e clima, garantindo alinhamento temporal e consistência.  

4. **Treinamento de Modelos**:  
   - Modelos de **regressão linear** e **Random Forest** são treinados para prever o preço da energia com base na temperatura.  

5. **Armazenamento e Visualização**:  
   - Os dados processados são armazenados em um banco de dados SQLite e exportados para CSV.  
   - Gráficos comparando preços reais e previsões de cada modelo são gerados e salvos em PNG.  

---

## Requisitos  

Certifique-se de ter os seguintes pacotes Python instalados:  

- `requests`: Requisições às APIs.  
- `sqlite3`: Banco de dados SQLite.  
- `pandas`: Manipulação de dados.  
- `scikit-learn`: Treinamento dos modelos.  
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
   - Configure as chaves de API nos parâmetros do código.  
   - Certifique-se de ter conexão à internet.  

2. **Executar as células do arquivo Jupyter**:  
```
Global Solution 2 - RPA.ipynb
```  

3. **Resultados Gerados**:  
   - Arquivo CSV com os dados combinados: `energia_sustentavel.csv`.  
   - Banco de dados SQLite: `energia_sustentavel.db`.  
   - Gráficos salvos em:  
     - `previsao_regressao_linear.png`  
     - `previsao_random_forest.png`  

---

## Estrutura do Código  

- **Funções Principais**:  
  - `fetch_energy_data()`: Busca dados de energia da API da EIA.  
  - `fetch_weather_data()`: Busca dados climáticos da API Open-Meteo.  
  - `process_data()`: Integra e padroniza os dados de preço e temperatura.  
  - `save_to_storage()`: Salva os dados em CSV e SQLite.  
  - `train_linear_model()`: Treina o modelo de regressão linear múltipla.  
  - `train_random_forest_model()`: Treina o modelo Random Forest.  
  - `plot_predictions()`: Gera gráficos comparativos entre dados reais e previstos.  

---

## Resultados  

Os modelos permitem prever preços de energia com base em:  
- **Temperatura média diária**.  

O desempenho é avaliado pelo **Erro Quadrático Médio (MSE)** e pelo **Coeficiente de Determinação (R²)**, indicando a precisão das previsões.

---

## Conclusão  

Este projeto demonstra como dados climáticos e padrões de consumo podem ser utilizados para prever preços de energia, fornecendo insights úteis para empresas e consumidores interessados em otimizar o uso e os custos de energia.