# Gamifica.ai Challenge 

[JS02] - Gamifica.ai - JS Developer Tasks

## Contexto: 

Uma aplicação registra todas as "movimentações" do jogador nos "desafios" da gamificação. Algumas dessas movimentações é de difícil validação, pois são imagens e vídeos. Atualmente fazemos essa validação de forma manual. Porém dependendo do cliente, temos milhares de ações para validar. Neste contexto, desenvolva uma solução para validação semi-automática dos desafios
## Requisitos mínimos:
 - [ ] Usar Serverless Framework
     - Plugins
        - serverless-offline 
        - serverless-webpack 

- [ ] Usar uma conta pessoal com free tier da AWS
- [ ] Usar DynamoDB como persistencia
- [ ] Usar dynamoose como “ORM”
- [ ] Utilizar SQS para enfileirar sempre que o processamento for superior a 2 segundos
- [ ] Utilizar node.js

## Tarefas:
- [ ] Criar registros na tabela de forma manual (Não é necessário criar telas e endpoints para inserir esses dados no DynamoDB ou S3) 
- [ ] Ler de uma tabela do dynamo um registro com: dados do jogador, upload (caminho para um arquivo armazenado no S3), data do upload, array de strings contendo objetos que deveriam ter no upload, se foi validado ou não e meta dados da validação (tudo o que for gerado pela análise)
- [ ] Verificar qual o tipo do upload e validar conforme meta dados:
  ##### Se foto:
     - [ ] Verificar tamanho da foto
     - [ ] Verificar EXIF
     - [ ] Verificar data/hora dos metadados da foto
     - [ ] Verificar se não é uma foto preta
     - [ ] Usar AWS Rekognition para identificar se os objetos que deveriam ter na foto, estão lá
     - [ ] Considerar 50% como aceitável
  ##### Se vídeo:
     - [ ] Verificar tamanho da video
     - [ ] Verificar duração do vídeo
     - [ ] Verificar data/hora dos metadados do video
     - [ ] Verificar se não é uma foto preta
     - [ ] Usar AWS Rekognition para identificar o que tem em 3 frames aleatórios. 
     - [ ] Se tiver pelo menos 1 objeto em cada frame é aceitável
- [ ] Ao fim, marcar o upload como processado (validado ou não)


## Bonus:
- [ ] Front-end  listando os registros e ao clicar no item, exibir o upload, o resultado das análises e seus meta dados

- [ ] Otimizar o WebPack
- [ ] Subir as dependência de node_modules nas layers
