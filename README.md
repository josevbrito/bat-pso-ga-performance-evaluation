# Comparação de Algoritmos Evolutivos: GA vs PSO vs Bat Algorithm

Este projeto implementa e compara o desempenho de diferentes algoritmos de otimização metaheurística, incluindo Algoritmos Genéticos (AG) com técnicas de clusterização, Particle Swarm Optimization (PSO) e Bat Algorithm.

## 📋 Descrição do Projeto

### Atividade I - Algoritmos Genéticos com Clusterização
Implementação de variações do Algoritmo Genético utilizando técnicas de clusterização para manter a diversidade da população:
- **AG Padrão**: Implementação clássica do algoritmo genético
- **AG com K-Means**: Utiliza clusterização K-Means para preservar diversidade
- **AG com Clustering Hierárquico**: Aplicação de clustering hierárquico
- **AG com DBSCAN**: Implementação usando densidade-based clustering

### Atividade II - Comparação com Outros Algoritmos
Extensão da comparação incluindo:
- **PSO (Particle Swarm Optimization)**: Algoritmo baseado em inteligência de enxames
- **Bat Algorithm**: Algoritmo inspirado no comportamento de morcegos

## 🎯 Funções de Benchmark

O projeto utiliza duas categorias principais de funções de teste:

### Funções Monomodais
- **Sphere**: Função esférica simples para teste de convergência básica
- **Rosenbrock**: Função clássica com vale estreito

### Funções Multimodais
- **Schwefel**: Função com múltiplos ótimos locais
- **Ackley**: Função multimodal com estrutura complexa
- **Griewank**: Função com componentes globais e locais
- **Alpine**: Função com múltiplos picos e vales

## 🔧 Estrutura do Código

### Arquivos Principais

#### Algoritmos Genéticos
- `GA.R`: Implementações dos AGs (padrão, K-means, hierárquico, DBSCAN)
- `init.population.R`: Inicialização da população
- `selection.R`: Métodos de seleção (roleta e torneio)
- `crossover.R`: Operadores de crossover (simples e aritmético)
- `mutation.R`: Operador de mutação uniforme

#### Técnicas de Clusterização
- `clustering.R`: Implementação das técnicas de clusterização
  - K-Means para diversidade populacional
  - Clustering hierárquico (Ward.D2)
  - DBSCAN para clustering baseado em densidade

#### Outros Algoritmos
- `PSO.R`: Implementação do Particle Swarm Optimization
- `BAT.R`: Implementação do Bat Algorithm

#### Análise e Comparação
- `comparison.R`: Framework de comparação experimental
- `Benchmarks.R`: Funções de teste para otimização
- `main.R`: Script principal de execução

## ⚙️ Parâmetros dos Algoritmos

### Algoritmos Genéticos
- **População**: 50 indivíduos
- **Gerações**: 500
- **Probabilidade de crossover**: 0.6
- **Probabilidade de mutação**: 0.01
- **Frequência de clusterização**: A cada 10 gerações
- **Número de clusters**: 5

### PSO
- **Partículas**: 50
- **Iterações**: 500
- **Peso de inércia (w)**: 0.9 (com decaimento de 0.99)
- **Coeficientes de aceleração**: c1 = c2 = 2.0

### Bat Algorithm
- **População**: 50 morcegos
- **Iterações**: 500
- **Intensidade sonora inicial (A)**: 0.5
- **Taxa de pulso inicial (r)**: 0.5
- **Faixa de frequência**: [0, 2]
- **Coeficientes**: α = γ = 0.9

## 📊 Metodologia Experimental

### Configuração dos Testes
- **Execuções independentes**: 30 por algoritmo/função
- **Dimensão do problema**: 10
- **Seed aleatória**: 123 (para reprodutibilidade)

### Funções Testadas
1. **Sphere** (Monomodal): Domínio [-5.12, 5.12]
2. **Schwefel** (Multimodal): Domínio [-500, 500]

### Análise Estatística
- **ANOVA**: Teste de significância entre grupos
- **Tukey HSD**: Comparações pareadas post-hoc
- **Ranking médio**: Classificação baseada em desempenho
- **Estatísticas descritivas**: Média, desvio padrão, mediana, min/max

## 📈 Visualizações

O sistema gera automaticamente:
- **Gráficos de convergência**: Evolução do melhor fitness ao longo das gerações
- **Box plots**: Distribuição dos resultados finais
- **Rankings**: Classificação consolidada dos algoritmos

## 🚀 Como Executar

### Pré-requisitos
```r
# Instalar pacotes necessários
install.packages("dbscan")
```

### Execução
```r
# Carregar todas as dependências
source("main.R")

# Executar experimento completo
experiment_results <- main()
```

### Saída Esperada
O programa gerará:
1. Análise estatística completa no console
2. Gráficos de convergência e distribuição
3. Ranking consolidado dos algoritmos
4. Testes de significância estatística

## 🎯 Técnicas de Clusterização Implementadas

### K-Means
- Agrupa a população em k clusters
- Seleciona o melhor indivíduo de cada cluster
- Substitui os piores indivíduos da população atual

### Clustering Hierárquico
- Utiliza linkage Ward.D2 para formar clusters
- Corta o dendrograma em k grupos
- Mantém diversidade através da seleção inter-clusters

### DBSCAN
- Clustering baseado em densidade
- Parâmetros: eps=0.5, minPts=3
- Lida automaticamente com pontos de ruído
- Número variável de clusters

## 📋 Resultados Esperados

O sistema fornece uma análise abrangente comparando:
- **Eficácia**: Qualidade das soluções encontradas
- **Eficiência**: Velocidade de convergência
- **Robustez**: Consistência entre execuções
- **Diversidade**: Capacidade de exploração do espaço de busca

### Métricas de Avaliação
- Fitness médio e desvio padrão
- Melhor e pior resultado por algoritmo
- Taxa de convergência
- Significância estatística das diferenças

## 🔍 Insights Obtidos

### Algoritmos Genéticos com Clusterização
- **Objetivo**: Manter diversidade populacional e evitar convergência prematura
- **Mecanismo**: Substituição periódica dos piores indivíduos por representantes diversos de clusters
- **Benefício**: Melhor exploração do espaço de busca em funções multimodais

### Comparação Entre Algoritmos
- **PSO**: Eficiente em convergência rápida, especialmente em funções monomodais
- **Bat Algorithm**: Equilíbrio entre exploração e explotação através de echolocation
- **GA com clustering**: Superior em manter diversidade em paisagens complexas

## 🛠️ Possíveis Extensões

1. **Novos algoritmos**: Differential Evolution, Firefly Algorithm
2. **Funções adicionais**: CEC benchmark functions
3. **Análise de parâmetros**: Otimização dos hiperparâmetros
4. **Problemas reais**: Aplicação em datasets do mundo real
5. **Hibridização**: Combinação de diferentes metaheurísticas
