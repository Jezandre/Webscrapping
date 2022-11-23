Aula 01 Problema de negócio
Coletar informações de projetos de veradores do site da prefeitura de Inaial/ SC, e criar um banco de dados, que possa ter incrementais e depois criar um painel em power BI.
Webscraping.

Python
•	Coleta via Webscrapping
•	Inserção de dados em banco SQL server local
Power BI
•	Criar os painéis
A ideia principal do projeto é criar um banco de dados de forma que deixe um projeto grande mais leve para o powerBI.  Levando dados tratados para o powerBI.

Projeto Observatório Social
Utilizar técnicas de python para resolver problemas
Instalar bibliotecas 

Nota: Não consegui encontrar o Python 3.6.6 no site oficial para dowanload, por isso vou tentar utilizar a versão mais atual. Deus me abençoe.
Tentei instalar a primeira biblioteca e deu erro por que? Porque eu digitei python no cmd e esqueci de dar ctrl+z
Por preguiça de digitar os pips eu utilizei o google colab pra ler os notebooks.
Tava dano muito erro ai baixei o python de um site duvidoso...
Não instalou não faço ideia do que aconteceu. Ai eu deletei  e instalei a versão 3.7 e consegui instalar as bibliotecas
Continuou dando problema desisti e instalei o anaconda. Errado mas pelo menos vou conseguir acompanhar a aula do Joviano.
1 Conhecendo o problema
Webscrapping quando não tem uma API
Ele ensinou um sério de códigos em que converteu a URL do site em texto e em seguida utilizou duas bibliotecas, uma delas o pandas para transformar os textos em tabelas.
Ele ensionou elementos básicos de HTML


Praticando Webscrabing
Importando as bibliotecas e funções com o python no Jupyter
 

Importando a bliblioteca de Web scraping
 
As minhas versões estão mais atualizadas do que as do joviano, mas vamos ver se vai funcionar.
Depois de importar as bibliotecas resolvi pegar uma url diferente do meu time do coração pra testar os passos a passo em um site diferente. E ai percebi que tinha que importar o Iframe.
 

Colocando a url em memória e lendo
 

Inserindo o escudo do time
 
Importando o título do site
 
Agora utilizando um laço para criar o texto limpo
  











Aula 02
Iniciando a aula com a aplicação de itens para substituir valores reservados no python. O sitema utilizado foi um laço for e um dicionário chamado de para. A principio o Joviano substituiu apenas os valores que ele tinha certeza que poderiam ser palavras reservadas como false, true e none.
Função eval transforma texto literal em uma função
User agent – Procurar saber.
Print do Python serve apenas para mostrar as informações na tela
 Utilizando tratamento de erros para avaliar uma url. Utilizou funções juntamente com try para avaliar se uma url é válida.
Regras de time out.
Text Split. São delimitadores para quebrar os valores de um texto
Tipo bites não é possível converter em texte para isso, você utilizar .decode (‘utf-8’)
Remover html:
Utilizando a bs4
PANDAS = POWERQUERY DO PYTHON
Converter dt e dd em dicionário
Adicionando dados em dicionários de formar a obter as informações automaticamente.
Em seguida inserir os dados obtidos do webscraping em uma tabela utilizando pandas. Muito massa isso.
Utilizar time para evitar problemas com a policia federal.
While tomar cuidado com loop infinito











Botando a mão na massa
Primeiramente recaptulando a primeira aula, sempre que for possível acessar uma API utilizá-la, como diria o cara lá do chapolin Time is money, e se a API já traz as informações que você precisa seja prático e utilize-a.
 
Testando um erro comum. O python não identifica algumas palavras pois elas são palavras reservadas, por exemplo as palavras false, true e none.
 



Substituindo as palavras reservadas assim podemos criar um DataFrame e resolver o problema anterior. Para isso foi utilizada o laço for
 
Iniciando agora de fato o exercício. O primeiro passo é selecionar o agente e definir as variáveis resposta.
 

Criando levantamento de erros no 
 
Após este passo foram efetuados alguns tratamentos de erros a fim de reduzir os erros ao importar uma url. ASSIM É POSSÍVEL CAPTAR OS DADOS SEM ERROS PROVENIENTES DE UMA URL COM INFORMAÇÕES ERRADAS.
Utilizando Split para separa o texto por um limitador:
 
Utilizando funções para quebra de texto:
 
Importando a biblioteca beautiful soup e definindo as variáveis que armazenarão as informações de html e da soup.
 
Utilizando a função findAll para localizar ‘dd’ e obter a data e informações dos projetos.
 
Utilizando novamente o get_text no html podemos perceber que nem tudo são flores ainda precisamos melhorar o tratamento de dados. A partir daí podemos observar que o \n pode ter uma função interessante no processo de tratamentos. \n em algumas linguagens de programação é o código utilizado para ir para a próxima linha. E também podemos ver através do pd.read_html que a nossa url não está em formato de tabela então ainda precisamos fazer alguns ajustes.

 
Daí entra o ‘dd’ citado acima e o ‘dt’, ambos funcionam como par de dados o dt no caso seria o cabeçalho e o ‘dd’ os dados imputados no site. A partir daí vamos aplicar uma lógica para que nossos dados cheguem em forma de dicionário no python e posteriormente vamos inserir em um dataframe no pandas.
Após executar testes até obter o resultado desejado que são as informações da reunião esta é função que irá obter o dicionário para o nosso banco de dados.
 
Avançando na etapa de  inserção de dados agora  já utilizando a função anterior juntamente com as informações que precisavam ser acresentadas como ano e proposição, além disso adicionando as varáveis de proposição e ano é possível obter os dados específicos de cada proposição baseada também no ano então o código fica assim:
 
O próximo passo foi criar o encapsulamento da função, assim podemos utilizar uma lista para obter os valores dentro de um dicionário.
 
Finalizando a função agora inserindo o texto pertencente a proposição do vereador que fica desta forma:
 
Parte 03 Loop
Começando a entender os laços for e While para utilizar na automatização da obtenção dos dados.
 
 
Inserindo os dados na tabela:
 

Definindo a função para incorporar os dados em uma tabela
 
Para o próximo passo é preciso entender que dependendo da quantidade de dados que você extrai de um site dependendo do sistema isso pode acarretar a queda do site. Por isso é importante humanizar o sistema utilizando funções de tempo para que os dados sejam carregados de forma mais humana possível para isso importaremos a biblioteca time.
 

Laço While, observação importante é que esse laço precisa ser bem cuidadoso pois o mesmo pode cair em um loop infinito. Neste laço não quis arriscar digitando pois poderia acontecer um loop infinito e travar o processo.












Aula 03
A aula hoje iniciou com a informação de como utilizar os dados do site caso o site da prefeitura estivesse off-line.
Alguns dados não possuem deliberação e sendo assim ele retorna valor nulo.
Instalar o SQLserver
Utilizar a biblioteca pyodbc para conectar ao banco de SQL.
Dando continuidade ao processo aqui passo para ressaltar dois erros e concertos que tive que fazer. O primeiro erro é que eu estava fazendo as atividades em notebooks diferentes então a parte de analisar erro ignorei completamente, esse passo é super importante e simplesmente ignorei. Outro etapa importante que não considerei foi na hora de instalar o sql server, instalei em inglês pois pretendo ser bilíngue, porém quando fui começar a inserir os dados de data o formato obtido por webscrapping não é compatível com o formato do sql serve, para isso utilizei uma função antes da query que resolveu o problema.
Voltando a aula 
Esta é a função utilizada para chamar a url que iremos utilizar já com os tratamentos de erros
 
Utilizando o beautiful soup para tornar a página mais utilizável
 
Utilizando a função desenvolvida na aula anterior para obter os elementos que farão parte do nosso banco de dados
 
Utilizando a função para levar os dados do webscraping para um dicionário:
 
Utilizando o laço while para automatizar todo o processo de coleta de dados :
 





No SQL server precisamos criar um banco e uma tabela com as colunas para que possamos inserir os dados via webscrapping e despois conectamos com o banco, o código para estabelecer uma conexão entre o python e o SQL é o seguinte:
 
Utilizando a função fillna para substituir dados vazios
 











Através do seguinte código inseri os dados na tabela do SQL, e lembrem que tive que utilizar um comando para que não houvesse erro ao inserir os dados? Pois então o código tem que ser colocado antes da query ser executada que é o comando Set Language ‘Portuguese’
 






Testando se os dados estão sendo inseridos na tabela
 

Transformando os passos acima para criar uma função de querys no sql
 
Inserindo os dados no sql server
 

Criando a função truncate
 
Iniciando testes para a criação da função de inserção
 
O objetivo dessa parte é se caso ocorrer alguma evendualidade e o banco de dados precisar ser interrompido por algum motivo, quando o processo se reestabelecer ser possível continuar de onde parou.
 




Se caso o campo estiver vazio a condicional starta o processo a partir do 1
 
Criando a função para a inserção dos dados
 
Definindo funções de busca e de gravação assim o processo está quase pronto para inicar a gravar as informações no sql
 
Enfim a ultima etapa ainda estou enfrentendo alguns problemas pois o wbscrapping esta incorporando dados vazios desnecessários, parece que o mesmo identifica dados e não continua o processo
 
Depois de vários erros finalmente consegui terminar o WebScrepping rodando com dois dias aproximadamente. Estou aperfeiçoando o código porém acredito que não conseguirei entregar no prazo precisaria de mais tempo para otimizar mais o código porém consegui finalizar o Webscrapping seguindo algumas orientações do pessoal da mentoria e também limitando as tentativas de encontrar as páginas. Assim posso finalizar a etapa 4 com a criação do dashboard.
Aula 04
Anotações da aula:
Dashboard:
Criar pasta
Ferramentas da tabela:
Dimensão calendário no Dax:
dCalendario = CALENDAR(MIN(fProposicoes[DataReuniao]), Max(fProposicoes[´DataReuniao]))

Conta DAX
Tratamento de dados Power Query

PQ
dCalendario:
PowerQuery>Nova fonte de dados>power platform> fluxo de dados
Essa dica serve para quem trabalha em empresa e para não ter a necessidade de criar várias vezes a mesma tabela dimensão.
O Joviano ta ensinando como criar vários colunas de uma vez só
Corrigir dados
Execução
Para importar os dados utilizei o método de importar do banco de dados SQL server por meio de um SELECT. Como o processo importou dados desnecessários e vazios em data e outros campos utilizei o seguinte comando SQL para que no momento de importação vissem somente os dados que me interessavam:
Select * from Proposicoes Where DataReuniao <> '1900-01-01'"
Assim somente os campos possuíssem data de reunião registrada seriam importados.
Após este passo segui continuei com o tratamento de dados utilizando o power query. Criei uma dimensão calendário utilizando os passos do Joviano, que consiste em criar duas Listas vazias e posteriormente utilizar as seguintes fórmulas. A primeira para inserir a data máxima: 
E a segunda para inserir a data mínima:
 
Em seguida defini o dCalendario com a seguinte codificação M:
 
Após a criação o próximo passo tratar as informações:
Na coluna Autor foi removida a palvara vereador, os espaços e os pontos finais. Além disso Alguns erros na importação do websacraping foram corrigida. A informação vinha como “Diversos” e essa palavra foi removida.
 
O próximo passo é talvez um dos mais interessantes, alguns projetos possuíam vários autores o que poderia implicar em uma contagem errada se esta não fosse tratada. Para utilizou a opção referência de forma a não criar outra consulta da seguinte forma:
 
Depois foi criado uma coluna índicie iniciando do 1:
 
Depois selecionando as colunas autor e Indice exclui as demais colunas:
 
Em seguida dividi o nome dos autores em linhas separando pelo delimitador:
 
Utilizei a virgula e marquei a opção avançada para selecionar dividir por linhas ao invés de colunas
 
Assim o mesmo vereador possuiria um índice que corresponde ao projeto em que ele trabalhou em conjunto com outro vereador.
Depois disso criei outra referencia mas agora para criar uma dimensão de autores, assim teríamos apenas os nomes dos vereadores sem repetições.
 

Assim, o fim era só mesmo identificar o tipo de dados e corrigir alguns nomes.
O próximo passo é utilizar o power pivot para criar o relacionamento entre as tabelas da seguinde maneiras:
 
E a partir daí o próximo passo é criar as medidas e visualizações:
A Primeira medida elaborada foi o cálculo do total de proposições, que era simplesmente contar o total de linhas da tabela fato proposições:
 
O próximo passo foi calcular as proposições aprovadas:
 

Os dados para análise servem como avaliação de desempenho dos vereadores, Na primeira aba utilizei códigos e filtros para avaliarmos as relações entre proposições em pauta e proposições aprovadas da qual foi utilizada a seguinte função DAX:
 
Por fim elaborei um background no FIGMA, ferramenta que amo utilizar:
 









Assim ficou o Dashboard

 
O dashboard pode ser visualizado no seguinte link:

https://app.powerbi.com/reportEmbed?reportId=41c197fa-dd82-4898-a2c4-98345da5c22a&autoAuth=true&ctid=b44d1ab3-1ab0-45e5-8355-c36d33634a2a

