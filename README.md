# ecm967-trab-feeds


Lucas Ribeiro Gonçalves RA: 19.00194-0

Vinicius Savrutsky Ivankovich 19.01014-0

Quantas e quais funções Lambda foram desenvolvidas para a fase 1 do trabalho? Explique a forma como cada uma é associada e seu papel, ou seja, o que cada uma faz.
Foram feitas 5 funções lambda para a execução do trabalho, a obter_feed que contém o código responsável por listar todos os feedbacks, a obter_feed_esp que contém o código responsável por listar as informações de um feedback com um ID especifico, a inserir_feed que contém o código responsável por adicionar feeds ao banco de dados , o deletar_feed que tem o código responsável por deletar o feedback com um ID especifico e o index.mjs que orquestra quando o código de cada arquivo deve ser rodado, quando a requisição é GET e id é igual a 'all' ele chama o obter_feed, quando a requisição é GET mas i id não é 'all' chama a função obter_feed_esp , quando a requisição é POST ele chama a função inserir_feed e quando é DELETE chama o deletar_feed

Para cada endpoint existente na implementação/implantação da fase 1 do projeto, cite as transformações pelas quais cada requisição passa antes de ser entregue às funções Lambda. Em particular, para cada endpoint, explique qual tipo de transformação/tratamento acontece em cada um dos quatro quadros (Integration Request, Integration Response, Method Request, Method Response).
e a q2 A aplicação tem 2 recursos o /feedback e o /feedback/{id} . Para requisições GET dentro do /feedback tem-se na solicitação de integração um modelo de mapeamento {

"method": "$context.httpMethod",
"id": "all"
} , na requisição POST do /feedback tem-se na solicitação de integração um modelo de mapeamento 
{
"method": "$context.httpMethod",
"payload": $input.json('$')
} e dentro de Solicitação de método tem um modelo que verifica se a requisição possui os atributos, o schema que o modelo usa é {
 "$schema":"https://json-schema.org/draft/2020-12/schema#",
 "title":"FeedModel",
 "type":"object",
 "properties":{
 "produto":{"type":"string"},
 "comentario":{"type":"string"},
 "classificacao":{"type":"string"}
 },
 "required":["produto","comentario","classificacao"]
 } 
e para requisições GET dentro do /feedback/{id} tem-se na solicitação de integração um modelo de mapeamento 
{
"method": "$context.httpMethod",
"id": "$input.params().get('path').id"
}

fora oq falei nessas questões tem o dynamoDB q tem uma tabela com os atributos ID , produto , comentario e classificacao e o front foi feito em react hospedando no S3

e caso precise d algo especifico do código do lambda da pra pegar no git e olhar os arquivos com os nomes que falei na Q1
