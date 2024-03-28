# Desafio Machine Learning 🤖

Durante o lab, seguindo as orientações, pude criar um modelo de previsão para uma suposta empresa de aluguel de bicicletas, com a finalidade de, a partir de dados referentes a um histórico de aluguel de bicicletas, prever o número de bicicletas alugadas esperadas em um determinado dia, considerando características meteorológicas e sazonais, inclusive. 

## 📝 Passo a passo do projeto:

O primeiro passo consiste em logar na conta Microsof Azure e criar um novo Recurso, voltado ao projeto, com isso iremos criar um novo Workspace de Azure Machine Learning e a partir dele acessar o Machine Learning Studio. 

Já no Machine Learning Studio o novo modelo de previsão é criado e treinado, para isso entramos na aba Automated ML e criamos um novo trabalho de Machine Learning automatizado, para isso vamos preencher algumas configurações, definir o tipo de treinamento (que nesse caso será Regressão) e adicionar o banco de dados que será utilizado para o modelo.

Para esse projeto em específico foram selecionados apenas os modelos RandomForest e LightGBM afim de tornar o experimento mais dinâmico. 

Uma vez que todas as configurações foram definidas, é hora de iniciar o trabalho de treinamento.

Após a conclusão do treinamento, é possível verificar qual foi o melhor modelo, e a partir dele visualizar as métricas que revisam o desempenho do modelo. 

O próximo passo será implantar e testar o modelo, então na guia do modelo selecionamos a opção Deploy (implantar) e a opção Web Service. Abrindo a janela de configurações fazemos os ajustes necessários e damos início a implantação, que deve durar alguns minutos. 

Uma vez que implantação foi bem sucessida, já será possível testá-la. Para isso, vamos entrar na guia Endpoint (pontos de extremidade), selecionar o modelo implantado e clicar na aba "teste". No painel com o nome "Input data to test endpoint" o modelo JSON será substituído pelo seguinte: 
````
{
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
````
 E na sequência podemos dar início ao teste, que irá retornar como resposta um valor correspondente ao número de aluguéis previstos em um determinado dia, no caso esse valor foi de: 344.7978642449826.

As informações e detalhes de configuração de cada passo, podem ser encontradas na página da [Microsoft Learn](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html).

 



