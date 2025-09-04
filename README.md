# FarmTech - Machine Learning para Agricultura

**Autor:** Gustavo Zanette Martins  
**RM:** 564523  
**Disciplina:** Fase 5 - Tratores digitais - Hardwares para IA

---

## 📋 Sobre o Projeto

Este projeto aplica técnicas de **Machine Learning** para prever o rendimento de safras agrícolas com base em variáveis climáticas, além de realizar análise de **custos de infraestrutura em nuvem AWS** para implementação de soluções agrícolas.

## 🎯 Objetivos

### Entrega 1 - Machine Learning
- Prever **Rendimento (t/ha)** de culturas agrícolas
- Realizar análise exploratória de dados climáticos
- Aplicar técnicas de **clusterização** para identificar padrões
- Desenvolver e comparar **5 modelos de ML** distintos
- Identificar **outliers** e cenários discrepantes

### Entrega 2 - Computação em Nuvem (AWS)
- Comparar custos entre regiões **São Paulo** e **N. Virginia**
- Analisar configuração: 2 vCPUs, 1 GiB RAM, 50GB storage
- Justificar escolha considerando **compliance** e **performance**

## 📊 Dataset

**Arquivo:** `crop_yield.csv`

**Variáveis:**
- **Cultura** (categoria)
- **Precipitação** (mm/dia)
- **Umidade específica a 2m** (g/kg)
- **Umidade relativa a 2m** (%)
- **Temperatura a 2m** (°C)
- **Rendimento** (t/ha) - *variável alvo*

## 🚀 Como Executar

### 1. Configurar Ambiente

```bash
# Instalar dependências
pip install pandas numpy scikit-learn matplotlib seaborn plotly scipy xgboost lightgbm jupyter
# ou
pip install -r requirements.txt
```


### 2. Executar Notebook

```bash
jupyter notebook GUSTAVOZANETTEMARTINS_rm564523_pbl_fase4.ipynb
```

## 🤖 Modelos Implementados

1. **Ridge Regression** - Regularização L2
2. **Random Forest** - Ensemble de árvores
3. **XGBoost** - Gradient boosting otimizado
4. **Support Vector Regression (SVR)** - Kernel RBF
5. **K-Nearest Neighbors (KNN)** - Baseado em proximidade

### Técnicas Utilizadas
- **Validação Cruzada** (5-fold)
- **Grid Search** para otimização de hiperparâmetros
- **Pipelines** com pré-processamento automático
- **Métricas múltiplas:** RMSE, MAE, R²

## 📈 Resultados de Clusterização

### Algoritmos Aplicados
- **K-Means** - Particionamento em k clusters
- **DBSCAN** - Detecção de outliers baseada em densidade
- **Gaussian Mixture Model** - Clusters probabilísticos

### Análise de Outliers
- Identificação de condições climáticas extremas
- Análise por cultura e região
- Impacto no rendimento agrícola

## ☁️ Análise AWS - Custos de Infraestrutura

### Configuração Analisada
- **Instância:** t3.micro (2 vCPUs, 1 GiB)
- **Armazenamento:** 50GB EBS gp3
- **Sistema:** Linux
- **Modelo:** On-Demand (100%)

### Comparação de Custos (Mensal)
| Região | Custo Total | Diferença |
|--------|-------------|-----------|
| **São Paulo** | **$16.56** | +68% |
| **N. Virginia** | **$9.84** | Base |

### **Decisão: São Paulo (sa-east-1)**

**Justificativas:**
- ✅ **LGPD Compliance** - Dados brasileiros permanecem no país
- ✅ **Menor Latência** - 20-50ms vs 150-200ms
- ✅ **Proximidade** com sensores agrícolas brasileiros
- ✅ **Suporte local** e menor complexidade jurídica

## 📁 Estrutura do Projeto

```
fiap-fase5-ml-cap1/
├── GUSTAVOZANETTEMARTINS_rm564523_pbl_fase4.ipynb
├── crop_yield.csv                                   
├── requirements.txt                                
├── AWS_Cost_Comparison.md                          
└── README.md                                       
```

## 🔗 Links Importantes

### 📚 Documentação
- **Notebook Jupyter:** [GUSTAVOZANETTEMARTINS_rm564523_pbl_fase5.ipynb](./GUSTAVOZANETTEMARTINS_rm564523_pbl_fase5.ipynb)
- **Análise AWS:** [AWS_Cost_Comparison.md](./AWS_Cost_Comparison.md)

### 🎥 Vídeos Demonstrativos
- **Vídeo 1 - Machine Learning:** [Link será adicionado após gravação]
- **Vídeo 2 - AWS Cost Analysis:** [Link será adicionado após gravação]

## 🛠️ Tecnologias Utilizadas

### Machine Learning
- **Python 3.x**
- **Pandas** - Manipulação de dados
- **NumPy** - Computação numérica
- **Scikit-learn** - Modelos de ML
- **XGBoost/LightGBM** - Gradient boosting

### Visualização
- **Matplotlib** - Gráficos estáticos
- **Seaborn** - Visualizações estatísticas
- **Plotly** - Gráficos interativos

### Infraestrutura
- **Jupyter Notebook** - Ambiente de desenvolvimento
- **AWS EC2** - Análise de custos de compute
- **AWS EBS** - Análise de custos de storage

## 📊 Principais Métricas Alcançadas

- **RMSE:** Erro médio quadrático das predições
- **MAE:** Erro absoluto médio
- **R²:** Coeficiente de determinação
- **Silhouette Score:** Qualidade dos clusters

## 🔍 Insights Obtidos

### Machine Learning
- Diferentes culturas apresentam padrões climáticos distintos
- Variáveis climáticas têm correlações específicas com rendimento
- Outliers representam condições climáticas extremas
- Modelos ensemble apresentaram melhor performance

### AWS Cloud
- Região São Paulo oferece melhor compliance para dados brasileiros
- Diferença de custo (+68%) é compensada pelos benefícios de localização
- Latência é fator crítico para aplicações agrícolas em tempo real

## ⚠️ Limitações Identificadas

1. **Dataset limitado** - Poucas variáveis e amostras
2. **Ausência de dados temporais** - Não há informações sazonais
3. **Falta de dados geográficos** - Localização das culturas
4. **Variáveis de solo** - Não incluídas no dataset atual

## 📞 Contato

**Gustavo Zanette Martins**  
RM: 564523  
FIAP - Fase 5  

---

*Este projeto foi desenvolvido como parte da disciplina de Machine Learning da FIAP, demonstrando aplicação prática de IA na agricultura brasileira.*
