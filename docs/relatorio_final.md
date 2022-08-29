# Predicitve Health Expenses


**Carlos Dias Maia, carlosdiasmaia@gmail.com**

**Pedro Henrique Lima Colini, pedrodoriocolini@gmail.com**

---

Professores:

** Hugo Bastos de Paula **

---

_Curso de Ciência de Dados, Unidade Praça da Liberdade_

_Instituto de Informática e Ciências Exatas – Pontifícia Universidade de Minas Gerais (PUC MINAS), Belo Horizonte – MG – Brasil_

---

O merdcado de saúde cada vez mais, como consequência da grande nescessidades por esses serviços. Com isso, surgem cada vez mais planos de saúde com diversos preços e propostas diferente, algo que deixa os cidadãos em dúvidas sobre qual é um valor justo para isso e quanto devem esperar gastar.

O Predictive Health Expanses é um sistema inteligente que tem como objetivo auxiliar no planejamento de gastos familiares e pessoas com planos de saúde dos norte-americanos.

O projeto, em sua conclusão, apresenta um coeficiente de determinação de 80%, mostrando como o mesmo pode auxíliar muito as pessoas.

---

###    Contextualização

Em 2020, segundo o Federal Census Bureau, as 5.929 companhias privadas de planos de saúde presentes 
nos Estanos Unidos cobriam 66,5% da população americana. Essa alta aquisição fez com que o setor 
movimentasse 2.831,2 bilhões de dólares, gerando um valor de mercado superior a 2.8 trilhões de dólares. 
Contudo, estima-se que o mercado de planos de saúde tenha uma taxa de crescimento anual composta de 4,6%, 
aumentando o valor desse mercado para 4 trilhões em 2027, segundo o Global Market Insights.

###    Problema

Com o grande número de empresas que apresentam serviços de planos de saúde, os cidadões que buscam tais 
serviços muitas vezes não tem noção do quanto irão gastar com os mesmos. Com isso, não conseguem se planejar
financeiramente, gerando dívidas com serviços médicos.

###    Objetivo geral

O projeto visa criar um sistema para estimar os gastos dos clientes em diferentes
planos de saúde, a partir de informações pessoais deles.

####    Objetivos específicos

Formular um modelo de sistema capaz de fornecer estimativas de gastos
em diversos planos de saúde, baseado em dados pessoais dos clientes.

Desenvolver uma ferramenta para comparar os diferentes resultados entre os
serviços analisados pelo estudo.

###    Justificativas

O projeto foi criado para auxiliar o cliente a escolher o plano de saúde que mais
o beneficia, pelo menor custo do mercado. Já que os preços cobrados podem ser abusivos
em algumas situações.

##    Público alvo

O Predictive Health Expenses busca auxíliar indivíduos e famílias a planejarem seus gastos com planos de saúde.

## Análise exploratória dos dados

###    Dicionário de dados

A base de dados contém 1338 entradas sendo elas: 

<img width="700" alt="Screenshot_1" src="https://user-images.githubusercontent.com/59835112/166927871-259a767e-de14-4a85-8656-bcadf1319b25.png">

###    Descrição de dados

<img width="700" alt="Describe dados" src="https://user-images.githubusercontent.com/59835112/166925920-ed692c81-e168-4ae4-b947-c0994ebe0d4a.png">

<img width="715" alt="Plot1" src="https://user-images.githubusercontent.com/59835112/166928585-b1c095b1-d140-4abe-a16e-130b8ae37283.png">

<img width="731" alt="Plot2" src="https://user-images.githubusercontent.com/59835112/166928624-91b3aeb2-f173-46dd-996a-c3c553322bc5.png">



## Preparação dos dados

Removemos o atributo região do assegurado devido ao seu pequeno impacto na predição do modelo.
Também não haviam dados faltantes ou omissos na base de dados.
As categorias usadas foram: Idade, sexo, índice de massa corporal (BMI), número de 
dependentes do plano, condição de fumante e o valor real pago ao plano.
As colunas sexo  e condição de fumante foram tranformadas em valores numéricos.

## Indução de modelos

### Modelo 1: Regressão Linear

Como as variáveis independentes aprensentam grande relação com a váriavel dependente, a modelo de regressão linear se adequa muito bem para esse caso.
Para melhorar a precisão do modelo de regressão linear, foi ultilizado o polynomial features e aplicado o logarítimo em todos os valores da váriavel dependente.
Sendo assim, susando a biblioteca sci-kit learn a base da dados foi dívidida pare se realizar o treinamento do modelo e o teste.
![Screenshot_1](https://user-images.githubusercontent.com/59835112/176252108-afdb3f41-4598-4bbc-bf0d-4c3acdf3b660.png)

Para o treinamento foi ultilizado os paramêtros base de regressão linear so sci-kit learn.
![Screenshot_2](https://user-images.githubusercontent.com/59835112/176252313-b445a43f-fa92-4681-8c17-37592ff94de3.png)


### Modelo 2: Floresta de decisão

O algoritimo de floresta de decisão foi escolhido por conta de se enquandrar e representar bem aos dados.
O algoritmo Foi treinado sem a ultilização do polynomial features.
![Screenshot_3](https://user-images.githubusercontent.com/59835112/176253685-898b6fe6-0128-4900-a691-b7a2226e8e6b.png)

Alguns paramêtros do modelo foram trocados a fim de aumentar sua eficácia, como pode ser observado a baixo:
![Screenshot_4](https://user-images.githubusercontent.com/59835112/176253904-44850265-38ed-490b-99e8-4c3365c17ec5.png)


## Resultados

### Resultados obtidos com o modelo 1.

O modelo 1 apresentou um coeficiente de determinação de 79%. 
![Screenshot_5](https://user-images.githubusercontent.com/59835112/176254235-3f8303a3-283a-4284-b6a5-9f81991e47fd.png)


### Interpretação do modelo 1

Para se ver o reasoning do modelo 1, podemos analisar a feture importance do mesmo: 

![Screenshot_6](https://user-images.githubusercontent.com/59835112/176254438-252f9c2c-4ef6-4074-bafc-adb4eee221ac.png)

![Screenshot_7](https://user-images.githubusercontent.com/59835112/176255255-02cb256e-0db3-4a34-a3c8-7b210acb1ddb.png)

Por meio dela, pode-se observar que a principal feature para a previsão, segundo a regressão linear é a coluna "smoker", algo bem lógico, já que
fumantes tem mais problemas de saúde, seguida pela quantidade de filhos, que também é de grande importância.

### Resultados obtidos com o modelo 2.

O modelo 1 apresentou um coeficiente de determinação de 80%. 
![Screenshot_9](https://user-images.githubusercontent.com/59835112/176256881-2f7e62ae-2d09-4fe1-bd5e-da99353b059c.png)


### Interpretação do modelo 2

Para se ver o reasoning do modelo 2, podemos analisar a feture importance do mesmo:

![Screenshot_8](https://user-images.githubusercontent.com/59835112/176255884-87a9a972-03ee-4a3f-9552-a7fe977d30a4.png)

![Screenshot_10](https://user-images.githubusercontent.com/59835112/176257010-11835dfc-0b24-433b-a8d7-9a854183c0ab.png)

Por meio dele, pode-se observar como a idade acabou se tornando um fator predominante, algo que também é bem lógico, uma vez que pessoas mais velhas tendem
a ter mais despesas médicas, seguido pelo coluna de fumantes.

## Análise comparativa dos modelos

Os modelos tem um índece de acerto satisfátorio, mas ainda não alto o bastante, talvez pela falta de feature ou pelo volume de dados.
O modelo de regressão linear depende muito da feature "smoker", algo que pode prejudicar o mesmo, tendo em vista que a saúde do usuário nem sempre é muito prejudicada pelo fato do mesmo ser fumante ou não.
Ambos apresentam um problema sério com prever casos foras da curva, ou seja, pessoas que gastam valores muito altos.


## 8. Conclusão

Nestre projeto, foi desenvolvido um sistema inteligente que visa prever gastos anuais com saúde de cidadãos 
estado unidenses,a fim de ajudar no planejamento de gastos dos mesmos. 
Foram obtidos resultados parcialmente satisfatórios, uma vez queos modelos apresentaram um coenficiente de 
determinação de cerca 0,8, usando-se pouca mémoria e nescessitando de pouco poder de processamento.
Por outro lado, tal coeficiente poderia ser signficativamente maior com uma maior coleta de dados dos pacientes.


# APÊNDICES

**Colocar link:**

(https://github.com/ICEI-PUC-Minas-PPL-CD/2022-1-pcd-si-predictive-health-expenses/blob/main/src/PredictiveHealthExpansesNotebook.ipynb)

(https://github.com/ICEI-PUC-Minas-PPL-CD/2022-1-pcd-si-predictive-health-expenses/blob/main/docs/imagens/Pitch%20PHS.pdf)

(https://youtu.be/WQ_u9R7pQ5o)



