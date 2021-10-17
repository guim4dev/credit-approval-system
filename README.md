# EEL891 - 2021.1 - Relatório do Trabalho 1
Classificação: sistema de apoio à decisão para aprovação de crédito

Aluno: Thiago Guimarães

## Sobre o Repositório

Nesse repositório podem ser encontrados um [notebook](https://github.com/guim4dev/credit-approval-system/blob/main/notebook.ipynb), que foi utilizado
para realizar o pré-processamento dos dados e o treinamento do modelo, além da geração de um arquivo [submission.csv](https://github.com/guim4dev/credit-approval-system/blob/main/submission.csv), que é o arquivo entregado no Kaggle. Há também uma pasta [data](https://github.com/guim4dev/credit-approval-system/tree/main/data), na qual estão armazenados os datasets fornecidos e afins.

## Pré-processamento

Por meio da análise dos dados utilizando pandas e das informações fornecidas no kaggle, foram mapeadas colunas inúteis que poderiam ser descartadas, colunas que precisariam passar por um processo de one_hot_encoding, fora outros processamentos. As colunas que sofreram tais tipos de alteração estão mapeadas detalhadamente no arquivo de [anotações](https://github.com/guim4dev/credit-approval-system/blob/main/anotacoes.txt).
Em resumo temos:

**1. Colunas removidas:**

```
'grau_instrucao',
'estado_onde_nasceu',
'codigo_area_telefone_residencial',
'estado_onde_trabalha',
'codigo_area_telefone_trabalho',
'profissao',
'profissao_companheiro',
'grau_instrucao_companheiro',
'local_onde_reside',
'local_onde_trabalha',
'nacionalidade'
```

**2. Colunas que são binarizadas:**

```
'sexo',
'possui_telefone_residencial',
'vinculo_formal_com_empresa',
'possui_telefone_trabalho',
'possui_telefone_celular'
```

**3. Colunas que sofrem one_hot_encode:**

```
'regiao',
'produto_solicitado',
'forma_envio_solicitacao',
'tipo_endereco',
'estado_civil',
'tipo_residencia',
'ocupacao'
```

**4. Outras alterações:**
Além disso, no Estado do dataset, foi aplicado um processo de agrupamento por região do Brasil, de forma a agruparmos as linhas do dataset por região, não mais por Estado.

Também foi utilizado um Imputer para consertar alguns dados que estavam nulos, de forma a possibilitar a utilização do modelo. A métrica utilizada pelo imputer foi a mediana.


## Implementação do modelo classificador

Tendo tanto o dataframe de teste como o de treino em mãos, foram treinados diversos modelos, dentre estes: RandomForest, AdaBoost, NaiveBayes, KNN e GradientBoosting. Após uma grande quantidade de testes, o melhor modelo em questão de performance foi o Gradient Boosting. Assim, foi realizado um processo de fine tuning dos hiperparâmetros deste modelo, de forma a encontrar o melhor resultado para sua accuracy. Como foram feitos diversos testes e para facilitar o processo de leitura do notebook, estes testes de modelos diferentes foram retirados no Notebook para despoluí-lo.


## Resultados

Assim
O modelo encontrou uma acurácia de 0.574 no teste utilizando train_test_split. Já no kaggle, o accuracy encontrado foi de 0.575