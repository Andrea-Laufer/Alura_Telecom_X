📖 README 📖
Projeto de Análise e Predição da Evasão de Clientes (Churn) - TelecomX
📝 Descrição do Projeto
Este projeto tem como objetivo principal compreender e analisar o fenômeno da evasão de clientes (Churn) em uma empresa de telecomunicações. Através de um processo de limpeza, tratamento e análise exploratória de dados, buscamos identificar os principais fatores e padrões que levam os clientes a cancelar seus serviços. O conhecimento desses fatores é crucial para que a empresa possa desenvolver estratégias proativas de retenção de clientes, otimizar serviços e, consequentemente, impulsionar o crescimento e a rentabilidade.

📁 Estrutura do Projeto / Como Usar
Este projeto foi desenvolvido em um ambiente de notebook (Google Colab) e pode ser facilmente executado e visualizado.

Dados:

O arquivo de dados original utilizado foi TelecomX_Data.json, que simula o retorno de uma API.
Bibliotecas Necessárias: Certifique-se de que as seguintes bibliotecas Python estejam instaladas em seu ambiente (no Google Colab, a maioria já vem pré-instalada):

pandas
numpy
scikit-learn
matplotlib
seaborn
Para Executar no Google Colab:

Faça o upload do arquivo TelecomX_Data.json para o ambiente de sessão do Google Colab. Você pode fazer isso clicando no ícone de pasta (Files) na barra lateral esquerda e, em seguida, no ícone de "Upload to session storage" (pasta com seta para cima).
Abra este notebook (.ipynb) no Google Colab.
Execute as células de código sequencialmente. Cada seção do notebook corresponde a uma etapa do processo de análise.
🚀 Etapas do Projeto
As seguintes etapas foram realizadas para preparar e analisar os dados:

1. Carregamento e Conversão Inicial dos Dados
Fonte: Dados em formato JSON (simulando API).
Ação: Carregamento do JSON e normalização para um DataFrame do Pandas utilizando pd.json_normalize(), que é essencial para transformar dados aninhados em um formato tabular plano.
2. Pré-processamento e Limpeza de Dados
Esta etapa focou em garantir a qualidade e a coerência dos dados para análise e modelagem.

Tratamento da Coluna Custo_Total: Convertida de string para float, com tratamento de espaços em branco (substituídos por NaN e preenchidos com 0).
Criação da Coluna Custo_Diario: Calculada a partir de Custo_Mensal (Custo_Mensal / 30), proporcionando uma granularidade diária do faturamento.
Verificação de Duplicatas: Realizada para assegurar a unicidade dos registros.
Ajuste de Tipos de Dados: A coluna customer.SeniorCitizen (Idoso) foi explicitamente convertida para tipo categórico (object).
Codificação de Variáveis Categóricas:
Variável Alvo (Churn): Codificada para 0 (Não Evadiu) e 1 (Evadiu) usando LabelEncoder.
Outras Variáveis Categóricas: Transformadas via OneHotEncoder, criando colunas binárias para cada categoria (ex: Genero_Feminino, Contrato_Mes_a_Mes).
Escalamento de Variáveis Numéricas: Colunas numéricas (Meses_Cliente, Custo_Mensal, Custo_Total, Custo_Diario) foram padronizadas (StandardScaler) para terem média 0 e desvio padrão 1.
Renomeação de Colunas: Todos os nomes das colunas foram traduzidos para o português e simplificados para melhorar a legibilidade e interpretabilidade (ex: customer.tenure para Meses_Cliente).
3. Análise Exploratória de Dados (EDA)
A EDA foi conduzida para descobrir padrões e obter insights sobre a relação entre as características dos clientes e a evasão.

Distribuição da Variável Alvo (Evasão_Cliente):
Análise: Um gráfico de barras foi gerado para visualizar a proporção de clientes que evadiram vs. os que não evadiram.
Insight: Foi identificado um desbalanceamento de classes, com a maioria dos clientes não evadindo, o que é um ponto importante para futuras etapas de modelagem.
Evasão por Variáveis Categóricas:
Análise: Gráficos de contagem (sns.countplot) foram utilizados para comparar a taxa de churn em diferentes categorias.
Insights:
Tipo de Contrato: Clientes com contrato "Mês a Mês" apresentaram uma taxa de evasão significativamente maior.
Serviço de Internet: Clientes com Fibra Óptica podem ter uma maior tendência à evasão em comparação com DSL.
Método de Pagamento: O "Cheque Eletrônico" frequentemente se correlaciona com taxas mais altas de churn.
Serviços Adicionais: A ausência de serviços como segurança online ou suporte técnico foi associada a maior churn.
Evasão por Variáveis Numéricas:
Análise: Gráficos de densidade (sns.kdeplot) e Box Plots (sns.boxplot) foram gerados para comparar as distribuições das variáveis numéricas entre clientes que evadiram e os que não evadiram.
Insights:
Meses_Cliente (Tenure): Clientes que evadiram tipicamente possuem um tempo de serviço muito menor com a empresa, sugerindo que a evasão ocorre mais cedo no ciclo de vida do cliente.
Custo_Mensal: Clientes com custos mensais mais altos podem estar mais propensos a cancelar.
Custo_Total: Clientes que evadem apresentam um custo total acumulado significativamente menor, o que é consistente com seu menor tempo de serviço.
📊 Conclusões e Insights
A análise aprofundada dos dados revelou padrões consistentes sobre o perfil de clientes propensos à evasão:

Compromisso vs. Risco: Clientes em contratos flexíveis ("Mês a Mês") são a base mais vulnerável. A falta de compromisso de longo prazo aumenta a probabilidade de churn.
Experiência Inicial: Os primeiros meses de serviço são críticos, pois a maioria dos churners abandona a empresa nesse período. A experiência do cliente logo no início é determinante.
Valor Percebido vs. Custo: Custos mensais mais altos e a ausência de serviços adicionais (que agregam valor e segurança) podem levar à insatisfação e à evasão.
Atrito no Pagamento: O método de pagamento via "Cheque Eletrônico" sugere um ponto de atrito ou insatisfação que merece investigação.
Esses insights são fundamentais para a empresa, pois permitem:

Identificar Clientes de Risco: Criar um perfil de cliente com alta probabilidade de evasão.
Focar Ações de Retenção: Direcionar recursos para os segmentos mais vulneráveis.
Fundamentar Decisões Estratégicas: Informar o desenvolvimento de novas ofertas, políticas de preço ou melhorias de serviço.
💡 Recomendações
Com base nas análises realizadas, as seguintes recomendações são sugeridas para a empresa reduzir a evasão de clientes:

Programas de Incentivo para Fidelização:
Oferecer descontos atrativos ou benefícios exclusivos para clientes com contratos "Mês a Mês" migrarem para planos de longo prazo (1 ou 2 anos).
Monitoramento e Ação Proativa nos Primeiros Meses:
Implementar um "Programa de Boas-Vindas" robusto com acompanhamento ativo (ligações, e-mails de satisfação, suporte prioritário) para clientes recém-adquiridos, especialmente nos primeiros 6 meses.
Análise de Custo-Benefício dos Serviços:
Reavaliar a precificação e o valor percebido de serviços com alta taxa de churn (ex: Fibra Óptica) e pacotes de alto custo mensal. Considerar bundles que incluam serviços de segurança e suporte.
Incentivo à Adoção de Serviços Agregados:
Promover os benefícios de segurança online, backup e suporte técnico. Oferecer períodos de teste gratuitos ou incluir esses serviços em pacotes mais competitivos para aumentar o engajamento e a lealdade.
Revisão do Processo de Pagamento:
Investigar a experiência do cliente com o método "Cheque Eletrônico" para identificar e resolver possíveis pontos de atrito. Incentivar a adoção de métodos de pagamento automático (cartão de crédito, débito automático).
Desenvolvimento de um Sistema de Alerta Precoce de Churn:
O próximo passo lógico é construir um modelo preditivo de Machine Learning utilizando as features preparadas. Este modelo poderá classificar clientes com base no seu risco de evasão, permitindo que as equipes de retenção atuem de forma direcionada antes que o churn ocorra.
Este relatório serve como um guia para entender o status atual dos dados e direcionar futuras estratégias de negócios.
