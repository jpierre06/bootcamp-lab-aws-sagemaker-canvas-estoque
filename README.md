# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

Bem-vindo ao desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas. Neste Lab DIO, você aprenderá a usar o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). Siga os passos abaixo para completar o desafio!

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter uma conta na AWS. Se precisar de ajuda para criar sua conta, confira nosso repositório [AWS Cloud Quickstart](https://github.com/digitalinnovationone/aws-cloud-quickstart).


## 🎯 Objetivos Deste Desafio de Projeto (Lab)

![image](https://github.com/digitalinnovationone/lab-aws-sagemaker-canvas-estoque/assets/730492/72f5c21f-5562-491e-aa42-2885a3184650)

- Dê um fork neste projeto e reescreva este `README.md`. Sinta-se à vontade para detalhar todo o processo de criação do seu Modelo de ML para uma "Previsão de Estoque Inteligente".
- Para isso, siga o [passo a passo] descrito a seguir e evolua as suas habilidades em ML no-code com o Amazon SageMaker Canvas.
- Ao concluir, envie a URL do seu repositório com a solução na plataforma da DIO.


## 🚀 Passo a Passo

### 1. Selecionar Dataset

-   Foi criado dataset de movimentação de estoque mais completo.
-   O dataset possui as seguintes colunas:
    - ID_PRODUTO;
    - DATA_MOVIMENTACAO;
    - ESTOQUE_INCIAL;
    - QUANTIDADE_COMPRA;
    - QUANTIDADE_VENDA;
    - ESTOQUE_FINAL;
    - ESTOQUE_SEGURANCA;
    - COMPRA_MINIMA;
    - PRECO_VENDA
      
-   O dataset possui dados de movimentacao de estoque e preço de venda de 25 itens durante o período de 01/08/2024 a 31/08/2024
-   Foi realizado o upload do dataset no SageMaker Canvas com nome de movimentacao_estoque_2.



### 2. Construir/Treinar

-   A coluna QUANTIDADE_COMPRA foi definida como variável target;
-   A coluna de ID_PRODUTO como identificador do produto;
-   E a coluna DATA_MOVIMENTACAO como Timestamp
-   Foi utilizado o modelo Time series forecasting
-   Todas as demais colunas foram definidas automaticamente como feature values
- 

### 3. Analisar

-   O modelo obteve as seguintes métricas de acuracidade:
    -   ![image](https://github.com/user-attachments/assets/bafd8636-e618-4115-8857-dd852f0619b0)

-   As colunas com maior impacto no modelo:
    -   ![image](https://github.com/user-attachments/assets/cce9903f-fa7a-4c58-86a9-1e82ed076c8e)


### 4. Prever

-   Como os itens analisados não são para pronta entrega a movimentação de estoque permite itens com estoque negativo.
-   No dataset de movimentação de estoque foi identificado que o item 13 tem histórico de estoque negativo.
-   Ao analisar as previsões de compra foi identificado uma previsão que ainda manteria um histórico de estoque negativo
  -  ![image](https://github.com/user-attachments/assets/d42491cf-ecf4-4696-83db-fd7afc96810c)

-   Como as colunas ESTOQUE_INCIAL e ESTOQUE_FINAL são colunas calculadas eo baixo impacto das colunas ESTOQUE_SEGURANCA e COMPRA_MINIMA foi decido fazer outro treinamento de modelo considerando apenas as colunas:

    - ID_PRODUTO;
    - DATA_MOVIMENTACAO;
    - QUANTIDADE_COMPRA;
    - QUANTIDADE_VENDA;
    - PRECO_VENDA

