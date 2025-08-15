# Telecom X - Parte 2: Previsão de Churn

<img width="1584" height="396" alt="Challenge (6)" src="https://github.com/user-attachments/assets/869f4fab-c464-4b5b-865d-8531369a4428" />


## Visão Geral do Projeto

Este projeto se concentra na criação de um pipeline de modelagem preditiva para a empresa Telecom X, com o objetivo de antecipar a evasão de clientes, um fenômeno conhecido como churn. Através da análise de dados históricos, foram desenvolvidos e avaliados modelos de classificação para identificar clientes com maior probabilidade de cancelar seus serviços. O projeto abrange desde o pré-processamento dos dados até a interpretação dos resultados e a formulação de estratégias de retenção.

## Estrutura do Projeto

O projeto está organizado da seguinte forma:

- **`ChallengeTelecomX2.ipynb`**: Notebook principal contendo todo o processo de análise, desde a extração dos dados até a avaliação dos modelos e a conclusão estratégica.
- **`dados_telecomx.csv`**: Arquivo com os dados brutos utilizados na análise.
- **`README.md`**: Este arquivo, que fornece uma visão geral completa do projeto.

## Preparação dos Dados

A preparação dos dados foi uma etapa fundamental para garantir a qualidade e a eficácia dos modelos preditivos. O processo incluiu:

1.  **Remoção de Colunas Irrelevantes**: As colunas `customerID` e `Contas Diarias` foram removidas por não agregarem valor preditivo.
2.  **Classificação de Variáveis**: As variáveis foram divididas em:
    * **Numéricas**: `Idoso`, `Parceiro`, `Dependentes`, `Meses Contrato`, `Servico Telefonico`, `Fatura Online`, `Mensalidade` e `Gasto Total`.
    * **Categóricas**: `Sexo`, `Multiplas Linhas`, `Servico Internet`, `Seguranca Online`, `Backup Online`, `Protecao Dispositivo`, `Suporte Tecnico`, `Streaming TV`, `Streaming Filmes`, `Tipo Contrato` e `Forma Pagamento`.
3.  **Codificação e Normalização**:
    * **One-Hot Encoding**: Aplicado às variáveis categóricas para convertê-las em um formato numérico que os modelos de machine learning possam entender.
    * **Standard Scaler**: Utilizado para normalizar as variáveis numéricas, colocando-as na mesma escala e evitando que variáveis com magnitudes maiores dominem o processo de treinamento.
4.  **Divisão em Treino e Teste**: Os dados foram divididos em 80% para treino e 20% para teste, utilizando uma amostragem estratificada para manter a proporção da variável alvo `Churn` em ambos os conjuntos.
5.  **Balanceamento de Dados**: A técnica SMOTE (Synthetic Minority Over-sampling Technique) foi aplicada apenas ao conjunto de treino para corrigir o desbalanceamento entre as classes de clientes que evadiram e os que permaneceram.

## Análise Exploratória de Dados (EDA) e Insights

A análise exploratória revelou insights importantes sobre os fatores que influenciam o churn:

* **Tempo de Contrato vs. Evasão**: Clientes com contratos mais longos têm uma probabilidade significativamente menor de cancelar o serviço. Isso sugere que a fidelização aumenta com o tempo.
* **Gasto Total vs. Evasão**: Clientes que permanecem na empresa tendem a ter um gasto total acumulado maior, o que está diretamente relacionado ao tempo de contrato.
* **Mensalidade vs. Evasão**: Há uma correlação positiva entre o valor da mensalidade e a probabilidade de churn, indicando que clientes com mensalidades mais altas são mais propensos a cancelar.

<img width="918" height="602" alt="image" src="https://github.com/user-attachments/assets/5e47bf82-812b-47b2-a13c-bd491c2e06cf" />

*Matriz de Correlação entre as variáveis numéricas, destacando a forte correlação negativa entre "Meses Contrato" e "Churn".*

## Modelagem e Avaliação

Dois modelos de classificação foram treinados e avaliados:

1.  **Regressão Logística**: Um modelo linear que serve como uma excelente linha de base por sua simplicidade e interpretabilidade.
2.  **Random Forest**: Um modelo de conjunto mais complexo, capaz de capturar relações não-lineares nos dados.

### Resultados dos Modelos

| Modelo | Acurácia | Precisão (Churn=1) | Recall (Churn=1) | F1-Score (Churn=1) |
| :--- | :---: | :---: | :---: | :---: |
| **Regressão Logística** | 75.23% | 52.20% | **79.14%** | 62.91% |
| **Random Forest** | 78.71% | 60.22% | 58.29% | 59.24% |

A **Regressão Logística** foi escolhida como o modelo mais adequado para a estratégia de retenção, devido ao seu **Recall** superior, que é a métrica mais crítica para este problema de negócio.

## Como Executar o Notebook

Para replicar a análise, siga os passos abaixo:

1.  **Clone o repositório**:
    ```bash
    git clone [https://github.com/seu-usuario/telecom-x-parte-2.git](https://github.com/seu-usuario/telecom-x-parte-2.git)
    cd telecom-x-parte-2
    ```
2.  **Instale as bibliotecas necessárias**:
    ```bash
    pip install pandas matplotlib seaborn scikit-learn imbalanced-learn
    ```
3.  **Execute o Jupyter Notebook**:
    Abra o arquivo `ChallengeTelecomX2.ipynb` em um ambiente Jupyter e execute as células sequencialmente. Certifique-se de que o arquivo `dados_telecomx.csv` esteja no mesmo diretório.

## Conclusão Estratégica

A análise revelou que o **tempo de contrato** é o principal fator de retenção, enquanto o **custo mensal** é um fator de risco significativo para o churn. Com base nesses insights, recomenda-se que a Telecom X implemente as seguintes estratégias:

-   **Incentivar contratos de longo prazo** com benefícios claros para os clientes.
-   **Gerenciar a percepção de valor** dos serviços, especialmente para planos de maior custo como a fibra óptica.
-   Implementar um **programa de onboarding** para novos clientes, que apresentam maior risco de evasão.
-   Utilizar o modelo de **Regressão Logística para ações de retenção direcionadas** e proativas.

A implementação dessas estratégias, baseadas em dados, tem o potencial de reduzir significativamente as taxas de churn e fortalecer a base de clientes da empresa.
