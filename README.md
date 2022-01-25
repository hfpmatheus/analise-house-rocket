# Projeto de Insights: House Rocket Company.

<img src="https://www.mundi.com.br/rimg/dimg/72/59/d4891b32-city-7054-17745b4e13e.jpg?width=1366&height=768&xhint=1003&yhint=1402&crop=true" alt="drawing" width="80%"/>

## 1. Questão de negócio:

A House Rocket Company é uma startup que atua no mercado imobiliário de King County, EUA. Funciona como uma plataforma de marketplace onde a empresa compra, reforma e revende imóveis, ou vendedores terceiros podem cadastrar seu próprio imóvel para venda. Entretanto, o CEO encontra muitos obstáculos quando trabalha no primeiro pilar: compra, reforma e revenda, visto que não tem um time de dados para responder algumas de suas perguntas em relação ao enorme portfólio de imóveis disponíveis para aquisição na região. Estes imóveis, por sua vez, possuem muitos atributos a serem considerados e é inviável analisar cada um deles manualmente.

Dito isso, o CEO contratou uma consultoria de Ciência de Dados para auxiliar a responder a seguinte pergunta: ***Quais imóveis nós deveríamos comprar e quais atributos reformar para revendê-los com mais lucro?***

## 2. Premissas de negócio:

#### 2.1: Para auxiliar na análise, foram derivadas três novas colunas a partir dos atributos já existentes:

   - recomendation: após separar os imóveis por "zipcode", que se compara ao nosso "cep", tirei a mediana de seus preços em cada zipcode. Sendo assim, considerei três possíveis      valores:
     - 'buy' = imóveis abaixo da mediana de seu zipcode e com condição superior a 3. (preço abaixo do mercado e boas condições)
     - 'not_buy' = imóveis acima da mediana de seu zipcode e com condição superior a 3. (preço acima do mercado, mesmo com boas condições)
     - 'low_quality' = qualquer imóvel com condição inferior a 3. (baixa qualidade devido a coluna condição)

   - dormitory_type: 
     
     - 'studio' = imóveis com 1 quarto ou menos
     - 'apartament' = imóveis com 2 quartos
     - 'house' = imóveis com 3 quartos ou mais

   - age:

     - 'old' = imóveis construídos em 1990 ou antes
     - 'new' = imóveis construídos depois de 1990

#### 2.2:

  - Com “imóveis baratos”, quero dizer os que tem o atributo “recomendation” igual a “buy”.
  - Com “imóveis caros”, quero dizer os que tem o atributos “recomendation” igual a “not_buy”

## 3. Planejamento da solução: 

Nesse tópico, mostro qual foi o meu racícionio pra resolver o problema em questão.

#### 3.1. Entendimento do negócio:

- 3.1.1: Entregável:

  Resposta da pergunta: Agrupar as casas por região e tirar a mediana de seus preços. Todas que ficarem abaixo da mediana e apresentarem boas condições serão boas opções de       compra, visto que estarão abaixo do valor de mercado e bem preservadas.

  Formato de entrega: Tabela interativa.
  
  Local de entrega: App no streamlit.

- 3.1.2: Processo (passo a passo do que é preciso ser feito):

  Resposta da pergunta:

  - Criar nova coluna “recomendation" no dataset
  - Agrupar as casas por “zipcode” e tirar a mediana de seus preços.
  - Todas as casas que tiverem em boas condições e abaixo da mediana de preço do seu zipcode, terão “buy” na coluna recomendação.
  - As que tiverem em boas condições, porém acima do preço, terão “not_buy”
  - As que tiverem em más condições terão “low_quality”

  Formato e local de entrega: Mostrar o dataset no streamlit apenas com as colunas “id” e “recomendação”, e adicionar filtros interativos que permitam ao usuário selecionar       quais atributos a mais desejam visualizar.


- 3.1.3: Ferramentas:

  Fonte de dados: https://www.kaggle.com/harlfoxem/housesalesprediction
  Ferramentas: 

  - Python 3.8
  - Jupyter Notebook
  - PyCharm
  - Streamlit
  - Heroku

#### 3.2. Coleta de Dados: Extração da tabela CSV.

#### 3.3. Descrição e Limpeza de Dados: Descrição estatística dos dados e limpeza de colunas desnecessárias para a análise e outliers.

#### 3.4. Feature Engineering: Criação de novas colunas derivadas de atributos já existentes.

#### 3.5. Análise Exploratória: Criação e validação de hipóteses.

###@ 3.6. Deploy na nuvem: Deploy do app streamlit no Heroku pra visualização em qualquer dispositivo com internet.

## 4. Os 5 principais insights dos dados:

#### Hipótese 1: Os imóveis mais caros a preço de mercado tem 1 quarto a mais do que os mais baratos.

R: **De fato, quando se compara a mediana de ambos o resultado é de que os mais caros tem 1 quarto a mais. Logo, uma boa sugestão para a empresa seria construir 1 quarto a mais nos imóveis comprados, pois isso aumentaria seu valor de revenda.**

##

#### Hipótese 2: Em média, imóveis baratos e com vista para a água tem 30% menos área total do que os que não tem vista para a água.

R: **Falso. Em média, imóveis baratos com vista para a água são 142% maiores do que os que não tem. Verificou-se também que os que possuem vista para a água são 8% mais baratos.
Dentre outros fatores, talvez os imóveis sem vista para a água sejam mais caros por estarem mais protegidos da maresia.**

##

#### Hipótese 3: Imóveis antigos (com data de construção abaixo de 1990) são 50% mais baratos do que os mais novos.

R: **Obversamos que, em média, os imóveis antigos são 20% mais baratos do que os mais novos. Uma sugestão seria modernizar a fachada dos mais antigos para aumentar seu valor de venda.**

##

#### Hipótese 4: Imóveis com 3 banheiros tem um crescimento de preço YoY (Year over Year) de 20%. (Uma sugestão seria construir mais banheiros nos imóveis adquiridos)

R:

##

#### Hipótese 5: Apartamentos são, em média, 20% mais baratos do que casas.

R:

## 5. Resultados financeiros para o negócio:

## 6. Conclusão:

## 7. Próximos passos e pontos que podem ser melhorados:
