# EN-US #

You are tasked with writing a piece of software to do a token generation for cashless registration.
Your microservice should expose 2 different APIs

**You must use the .Net core platform to develop the solution.**

***We really encourage you to bring up any specific questions you might have about it.***

***Requirements:***
  • The application must be executable both in Windows and Unix based machines;
  • You don't have to worry about databases; it's fine to use in-process, in-memory storage;
  • It must be production quality according to your understanding of it - tests, README, Swagger, etc.

***General notes:***
  • Feel free to expand your design in writing;
  • You will submit the source code to git;
  
***Things we're looking for:***
  • Immutability;
  • Proper concurrency handling;
  • Separation of concerns;
  • Unit and integration tests;
  • API design;
  • Code readability;
  • Error handling.

**1 – API that receive customer card and save it on the db**

Request information:

***CustomerId*** - int
***Card Number*** – long - max 16 characters
***CVV*** – int - max 5 characters

Response information:

***Registration date – Date now in UTC
Token – long – (Size of token may vary)
CardId - int***

**2 – API that validate that token based on data provided in the request**

Request information:

***CustomerId – int
CardId - int
Token – long – (Size of token may vary)
CVV – int - max 5 characters***

Response information:

***Validated*** – bool

Algorithm

The algorithm used to create the token is:

  a) Get last 4 digits of card
  b) Apply algorithm described below in Problem #1 and the number of rotations would be the CVV number.

The algorithm to validate the token

  1. If creation date of token is more than 30 min, return as not valid
  2. Use the cardid to locate the card number
  3. If customer is not the owner of the card, return as not valid
  4. Print the card number in the console
  5. Process the algorithm described above in creation process to create the token again and compare with the token received in the request, if match return true otherwise false.


**Problem #1**

The operation called right circular rotation on an array of integers consists of moving the last array
element to the first position and shifting all remaining elements right one. Given an array of integers,
perform the rotation operation **a number of times.**

For each array, perform a number of right circular rotations and return this array.
For example, array a = [3, 4, 5], number of rotations k = 2.
First we perform the two rotations:
      [3, 4, 5] => [5, 3, 4] => [4, 5, 3]
The result of that would be [4, 5, 3]

**Explanation**

Given the array [1, 2, 3] after the first rotation, the array becomes [3, 1, 2].
After the second (and final) rotation, the array becomes [2, 3, 1].


# PT-BR #

Você tem a tarefa de escrever um software para gerar um token para registro sem dinheiro.
Seu microsserviço deve expor 2 APIs diferentes

**Você deve usar a plataforma .Net core para desenvolver a solução.**

***Nós realmente encorajamos você a trazer quaisquer perguntas específicas que você possa ter sobre isso.***

***Requisitos:***
  • O aplicativo deve ser executável em máquinas baseadas em Windows e Unix;
  • Você não precisa se preocupar com bancos de dados; não há problema em usar o armazenamento em processo e na memória;
  • Deve ter qualidade de produção de acordo com o seu entendimento - testes, README, Swagger, etc.

***Notas gerais:***
  • Sinta-se à vontade para expandir seu projeto por escrito;
  • Você enviará o código-fonte para o git;
  
***Coisas que estamos procurando:***
  • Imutabilidade;
  • Tratamento adequado da concorrência;
  • Separação de preocupações;
  • Testes unitários e de integração;
  • Projeto de API;
  • Legibilidade do código;
  • Manipulação de erros.

**1 – API que recebe cartão de cliente e salva no db**

Pedir informação:

***CustomerId*** - int
***Número do cartão*** – longo – máximo de 16 caracteres
***CVV*** – int - máximo de 5 caracteres

Informações de resposta:

***Data de registro – Data agora em UTC
Token – longo – (O tamanho do token pode variar)
CardId - int***

**2 – API que valida esse token com base nos dados fornecidos na solicitação**

Pedir informação:

***CustomerId – int
ID do cartão - int
Token – longo – (O tamanho do token pode variar)
CVV – int - máximo 5 caracteres***

Informações de resposta:

***Validado*** – bool

Algoritmo

O algoritmo usado para criar o token é:

  a) Obter os últimos 4 dígitos do cartão
  b) Aplique o algoritmo descrito abaixo no Problema #1 e o número de rotações seria o número CVV.

O algoritmo para validar o token

  1. Se a data de criação do token for superior a 30 min, retorne como inválido
  2. Use o cartão para localizar o número do cartão
  3. Se o cliente não for o titular do cartão, devolver como inválido
  4. Imprima o número do cartão no console
  5. Processe o algoritmo descrito acima no processo de criação para criar o token novamente e compare com o token recebido na solicitação, se corresponder retornar true caso contrário false.
  
  **Problema nº 1**

A operação chamada rotação circular à direita em um array de inteiros consiste em mover o último array
elemento para a primeira posição e deslocando todos os elementos restantes para a direita. Dada uma matriz de inteiros,
execute a operação de rotação **várias vezes.**

Para cada matriz, execute várias rotações circulares à direita e retorne essa matriz.
Por exemplo, array a = [3, 4, 5], número de rotações k = 2.
Primeiro realizamos as duas rotações:
      [3, 4, 5] => [5, 3, 4] => [4, 5, 3]
O resultado disso seria [4, 5, 3]

**Explicação**

Dada a matriz [1, 2, 3] após a primeira rotação, a matriz se torna [3, 1, 2].
Após a segunda (e última) rotação, a matriz se torna [2, 3, 1].
