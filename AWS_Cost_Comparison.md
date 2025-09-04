# Entrega 2 - Comparação de Custos AWS

## Objetivo

Comparar custos **On-Demand (100%)** de **máquina Linux** entre **São Paulo (sa-east-1)** e **Virgínia do Norte (us-east-1)** com a configuração especificada e justificar a escolha considerando **acesso rápido aos dados** e **restrições legais**.

## Configuração Alvo

- **2 vCPUs**
- **1 GiB de memória** 
- **Até 5 Gbps de rede**
- **50 GB de armazenamento (EBS)**
- **Sistema Operacional:** Linux
- **Modelo de pagamento:** On-Demand (100%)

## Comparação de Custos

### Instância Selecionada: t3.micro

A instância **t3.micro** foi selecionada pois atende aos requisitos mínimos:
- **vCPUs:** 2
- **Memória:** 1 GiB
- **Performance de rede:** Até 5 Gbps
- **Otimizada para:** Cargas de trabalho com uso variável de CPU

### Estimativas de Custo (Setembro 2025)

| Componente | São Paulo (sa-east-1) | N. Virginia (us-east-1) | Diferença |
|------------|----------------------|-------------------------|-----------|
| **EC2 t3.micro** | Incluído no total | Incluído no total | - |
| **EBS (50GB)** | Incluído no total | Incluído no total | - |
| **TOTAL MENSAL** | **$16.56** | **$9.84** | **+$6.72 (+68%)** |

### Premissas da Estimativa

1. **Instância:** t3.micro rodando 24/7 (730 horas/mês)
2. **Armazenamento:** EBS 50GB HDD Throughput Optimized (st1)
3. **Tráfego:** Considerado apenas tráfego interno (sem custos de saída significativos)
4. **Preços:** Baseados em setembro de 2025 via AWS Pricing Calculator
5. **Configuração:** 2 vCPUs, 1 GiB RAM, até 5 Gbps de rede, 50GB storage st1
6. **Observação:** Instância já inclui volume EBS root padrão (~8GB) para boot do SO

## Análise de Fatores de Decisão

### 1. Latência e Acesso aos Dados

**São Paulo (sa-east-1):**
- ✅ **Menor latência** para usuários no Brasil
- ✅ **Melhor experiência** para aplicações em tempo real
- ✅ **Proximidade geográfica** com sensores e fontes de dados agrícolas brasileiras
- ✅ **Roteamento otimizado** para conexões domésticas

**N. Virginia (us-east-1):**
- ❌ **Maior latência** (~150-200ms vs ~20-50ms)
- ❌ **Possível impacto** na experiência do usuário
- ✅ **Maior disponibilidade** de serviços AWS
- ✅ **Primeira região** a receber novos recursos

### 2. Restrições Legais e Compliance

**Considerações Importantes:**

1. **Lei Geral de Proteção de Dados (LGPD):**
   - Dados pessoais de brasileiros devem preferencialmente permanecer no território nacional
   - Transferência internacional requer adequações específicas

2. **Marco Civil da Internet:**
   - Dados de usuários brasileiros têm proteções específicas
   - Armazenamento local é preferível

3. **Regulamentações Setoriais:**
   - Dados agrícolas podem ter regulamentações específicas
   - Órgãos como INCRA/MAPA podem ter requisitos de localização

### 3. Viabilidade Operacional

**São Paulo:**
- ✅ **Compliance facilitado** com legislação brasileira
- ✅ **Suporte em português**
- ✅ **Menor complexidade jurídica**
- ❌ **Custo 68% maior**
- ❌ **Menor variedade** de serviços disponíveis

**N. Virginia:**
- ✅ **Custo 68% menor**
- ✅ **Maior variedade** de serviços
- ✅ **Primeira a receber** inovações
- ❌ **Complexidade legal** para dados brasileiros
- ❌ **Maior latência**

## Decisão Recomendada

### **Região Escolhida: São Paulo (sa-east-1)**

**Justificativa Técnica:**

1. **Compliance Legal:** A LGPD e outras regulamentações brasileiras favorecem fortemente o armazenamento local de dados, especialmente dados pessoais e sensíveis.

2. **Performance:** Para uma aplicação agrícola que pode envolver coleta de dados de sensores IoT em tempo real, a latência reduzida (20-50ms vs 150-200ms) é crucial.

3. **Custo vs. Benefício:** Embora 68% mais cara, a diferença de ~$6.72/mês é aceitável considerando os benefícios legais e de performance.

4. **Sustentabilidade:** Menor latência resulta em menor consumo de energia para transmissão de dados.

**Cenários onde N. Virginia seria preferível:**
- Aplicação sem dados pessoais de brasileiros
- Necessidade de serviços específicos não disponíveis em sa-east-1
- Orçamento extremamente restrito
- Aplicação global com usuários predominantemente internacionais

## Considerações Técnicas do Storage

### **HDD Throughput Optimized (st1) - Análise:**

**✅ Vantagens:**
- **Custo-benefício** para grandes volumes de dados sequenciais
- **Ideal** para data lakes, analytics e backup
- **Throughput alto** para workloads sequenciais (até 500 MiB/s)

**⚠️ Considerações:**
- **Não pode ser volume de boot** - mas instância já inclui volume root padrão
- **IOPS limitado** - não ideal para aplicações com muitas operações aleatórias  
- **Volume adicional** - st1 seria usado como storage adicional para dados

**🎯 Para Aplicação Agrícola:**
- ✅ **Adequado** para armazenamento de dados históricos de sensores
- ✅ **Bom** para processamento batch de dados ML
- ⚠️ **Considerar gp3** se houver necessidade de acesso aleatório frequente

## Considerações Adicionais

### Otimizações de Custo Futuras

1. **Reserved Instances:** Desconto de até 75% para compromissos de 1-3 anos
2. **Spot Instances:** Economia de até 90% para workloads tolerantes a interrupções
3. **Auto Scaling:** Ajuste automático de recursos conforme demanda
4. **Scheduled Scaling:** Para workloads com padrões previsíveis

### Monitoramento de Custos

- **AWS Cost Explorer:** Análise detalhada de gastos
- **AWS Budgets:** Alertas de orçamento
- **AWS Trusted Advisor:** Recomendações de otimização

## Conclusão

A escolha da região **São Paulo (sa-east-1)** é justificada pela necessidade de compliance com a legislação brasileira, melhor performance para usuários locais e proximidade com as fontes de dados agrícolas. O custo adicional de ~$6.72/mês é um investimento razoável considerando os benefícios legais e técnicos obtidos.

Para o contexto específico de uma aplicação agrícola brasileira, os fatores de compliance e latência superam a vantagem de custo da região de N. Virginia.
