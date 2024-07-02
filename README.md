Conjunto de Dados

O conjunto de dados contém informações de mais de 7 mil clientes, com 33 variáveis sobre cada um.

As variáveis incluem:


    Identificação do cliente
    Localização geográfica
    Gênero
    Se é cidadão sênior (65 anos ou mais)
    Se tem parceiro
    Quantidade de dependentes
    Tempo como cliente da empresa
    Serviços contratados (telefone, internet, streaming etc.)
    Informações sobre contrato, cobranças e pagamentos
    Se o cliente fez churn (cancelou o serviço)
    Pontuação de churn
    Customer Lifetime Value
    Motivo do churn


Análise Inicial dos Dados

Fazemos uma análise exploratória inicial utilizando o Pandas Profiling.

Identificamos:


    Algumas colunas com valor constante, que podem ser descartadas
    Colunas com alta cardinalidade (muitos valores distintos), como identificação do cliente e código postal, que não são úteis para a modelagem
    Correlação entre latitude/longitude e código postal, então vamos manter apenas uma representação geográfica
    A coluna "totalCharges" não está sendo reconhecida como numérica devido a valores com espaços em branco, então faremos uma limpeza nesses dados
    Alta porcentagem de missing values (73,5%) na coluna "ChurnReason" para clientes não-churn, o que é compreensível pois eles não teriam um motivo para churn


Identificamos também que há 3 colunas relativas a churn: uma com o status, outra com a pontuação e outra com o motivo. Essas colunas contêm informações sobre o alvo que estamos tentando prever, portanto não podem ser utilizadas como features.
Pré-processamento dos Dados

Realizamos as seguintes transformações nos dados:


    Remoção das colunas constantes e não úteis para modelagem
    Conversão da coluna "totalCharges" para numérica após limpeza
    Transformação das colunas booleanas em valores 0 ou 1
    Separação das colunas em numéricas e categóricas
    Padronização das features numéricas
    One-hot encoding das features categóricas


Esse processo de pré-processamento é encapsulado em um pipeline para facilitar a aplicação em novos dados no futuro.

Também analisamos a correlação de cada feature com a variável-alvo de churn utilizando Mutual Information, identificando quais são mais relevantes para a modelagem. As principais são: Customer Lifetime Value, meses como cliente, contratação de serviços como segurança online e streaming.
Considerações Finais

O conjunto de dados está agora limpo, tratado e preparado para a aplicação de modelos de machine learning para prever se um cliente fará churn ou não.

Algumas sugestões adicionais são:


    Fazer merge com outras bases de dados externas utilizando informações geográficas como código postal e localização
    Testar diferentes formas de agregar e incorporar a variável "cidade" nas features
    Experimentar vários algoritmos de classificação como random forest, SVM, redes neurais etc.


O mais importante é sempre verificar a qualidade e consistência dos dados antes de aplicar os modelos, fazendo as transformações e limpezas necessárias. E iniciar com um conjunto pequeno de good features, avaliando o desempenho antes de aumentar a complexidade.
