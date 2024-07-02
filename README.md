Análise Preditiva de Churn em Clientes de Telecomunicações

Resumo

Este repositório documenta o processo de análise preditiva de churn em um conjunto de dados de mais de 7 mil clientes de uma empresa de telecomunicações. O objetivo é desenvolver um modelo de machine learning para prever se um cliente cancelará o serviço no futuro.

Conjunto de Dados

O conjunto de dados original contém 33 variáveis sobre cada cliente, incluindo:

    Identificação do cliente
    Localização geográfica
    Gênero
    Idade (se cidadão sênior)
    Situação familiar (se tem parceiro e dependentes)
    Tempo como cliente
    Serviços contratados
    Informações sobre contrato, cobranças e pagamentos
    Se o cliente fez churn (cancelou o serviço)
    Pontuação de churn
    Customer Lifetime Value
    Motivo do churn

Análise Exploratória

Uma análise exploratória inicial foi realizada utilizando o Pandas Profiling, identificando:

    Colunas com valor constante: podem ser descartadas.
    Colunas com alta cardinalidade: como identificação do cliente e código postal, não são úteis para a modelagem.
    Redundância de informação: a correlação entre latitude/longitude e código postal permite manter apenas uma representação geográfica.
    Problema de formatação: a coluna "totalCharges" não está sendo reconhecida como numérica devido a valores com espaços em branco, exigindo limpeza.
    Missing values: alta porcentagem (73,5%) na coluna "ChurnReason" para clientes não-churn, o que é compreensível pois eles não teriam um motivo para churn.

Pré-processamento dos Dados

As seguintes transformações foram realizadas:

    Remoção de colunas irrelevantes: colunas constantes e de alta cardinalidade foram descartadas.
    Correção de formatação: a coluna "totalCharges" foi convertida para numérica após limpeza dos espaços em branco.
    Codificação de variáveis categóricas: as colunas booleanas foram transformadas em valores 0 ou 1.
    Separação de features: as colunas foram separadas em numéricas e categóricas.
    Padronização das features numéricas: as features numéricas foram padronizadas para ter média 0 e desvio padrão 1.
    One-hot encoding: as features categóricas foram codificadas utilizando one-hot encoding.

O processo de pré-processamento foi encapsulado em um pipeline para facilitar a aplicação em novos dados no futuro.

Seleção de Features

A correlação de cada feature com a variável-alvo de churn foi analisada utilizando Mutual Information. As features mais relevantes para a modelagem foram identificadas, incluindo:

    Customer Lifetime Value
    Meses como cliente
    Contratação de serviços como segurança online e streaming

Considerações Finais

O conjunto de dados está agora limpo, tratado e preparado para a aplicação de modelos de machine learning. Algumas sugestões adicionais para aprimorar a análise:

    Merge com outras bases de dados: dados geográficos como código postal e localização podem ser complementados com informações de outras bases.
    Agregação de features: diferentes formas de agregar e incorporar a variável "cidade" nas features podem ser exploradas.
    Experimentação de algoritmos: diversos algoritmos de classificação como random forest, SVM e redes neurais podem ser testados para otimizar o desempenho.

Próximos Passos

O próximo passo é desenvolver e avaliar diferentes modelos de machine learning para prever churn. A qualidade e consistência dos dados serão constantemente verificadas durante o processo, garantindo a robustez dos resultados.

Recursos

    Conjunto de dados: [Link para o conjunto de dados]
    Pipeline de pré-processamento: [Link para o código do pipeline]
    Análise de correlação: [Link para o código da análise de correlação]

Contribuições

Este repositório está aberto para colaboração e sugestões. Sinta-se à vontade para contribuir com ideias, comentários ou código para aprimorar a análise.
