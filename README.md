 # Simulação de circuitos LogSim

ARQUITETURA E ORGANIZAÇÃO DE COMPUTADORES
- DOCUMENTAÇÃO: CIRCUITO DIGITAIS

ALUNO: 
Rafael da Silva

 # Objetivo

Este trabalho apresenta o projeto e a implementação de um laboratório prático de circuitos digitais, com o objetivo de proporcionar atividades e experiência os fundamentos da eletrônica digital. Foram construídos alguns circuitos, desde componentes básicos como portas lógicas e registradores até sistemas mais complexos como ULA. A prática laboratorial abrangeu desde o projeto e simulação e teste dos circuitos, utilizando ferramenta LogSim.

# Conteúdos

1. Registrador Flip-Flop do tipo D e do tipo JK
2. Multiplexador de quatro opções de entrada.
3.  Porta lógica XOR usando os componentes: AND, NOT, e OR.
4.  Somador de 8 bits que recebe um valor inteiro e soma com o valor 4.
5.  Memória ROM de 8 bits.
7.  Banco de Registradores de 8 bits.
8.  Somador de 8 bits.
9.  Detector de sequência binária para identificar a sequência "101" em um fluxo de entrada.
10.  ULA de 8 bits com as seguintes operações: AND, OR, NOT, NOR, NAND, XOR, SHIFT de 2 bits à esquerda, SHIFT de bits à direita, soma e subtração.
11.  Extensor de sinal de 4 bits para 8 bits
12.  Considerações finais

# Circuitos

# 1. Registrador Flip-Flop do tipo D

1. Funcionamento
   
O circuito flip-flop D possui duas entradas principais:
    • D (Data): Entrada de dados. O valor presente em D no instante da borda de subida do sinal de clock será armazenado no flip-flop. 
    • CLK (Clock): Sinal de clock. A transição do sinal de clock (geralmente a borda de subida) desencadeia a operação de armazenamento. 
    
E duas saídas:
    • Q: Saída principal. Representa o valor atualmente armazenado no flip-flop. 
    • Q' (Q barra): Saída complementar. É o complemento lógico de Q. 
    
O funcionamento do flip-flop D pode ser resumido da seguinte forma:
 * 1. Armazenamento: Quando ocorre uma transição positiva no sinal de clock, o valor presente na entrada D é copiado para a saída Q. A saída Q' assume o valor oposto.
 * 2. Manutenção: O flip-flop mantém o valor armazenado em Q até que ocorra uma nova transição positiva no sinal de clock. 
Implementação Lógica

O flip-flop D pode ser implementado utilizando diversas configurações de portas lógicas. Uma implementação comum utiliza duas portas NAND conectadas em configuração mestre-escravo. A primeira porta NAND funciona como um latch mestre, armazenando o valor de D durante o pulso de clock. A segunda porta NAND funciona como um latch escravo, transferindo o valor armazenado no latch mestre para a saída Q na borda de descida do clock.


![REGISTRADOR TIPO D](https://github.com/user-attachments/assets/7ceeb413-4a1f-4ce1-94e1-d804df640bf2)

# 1.1 Registrador tipo JK

Descrição dos Componentes e sua Funcionalidade
Pinos:

* J e K: Entradas de controle que determinam a próxima saída, dependendo do estado atual do flip-flop.
*  Clock: Sinal de clock que sincroniza as mudanças de estado.  
* Q e Q' (Q negado): Saídas complementares, representando o estado atual e seu complemento. 
* Set e Clear: Entradas assíncronas que forçam o flip-flop a um estado específico, independentemente do clock. 
    
![regitrador JK](https://github.com/user-attachments/assets/20c35a84-3e73-4186-8083-f259d7c5ed31)

Lógica:

A tabela verdade do flip-flop JK resume seu comportamento:

![tabela verdade jk](https://github.com/user-attachments/assets/1f88b911-835d-4939-a7c7-01439ec75beb)

Onde:
* J e K são as entradas. 
* Q(t) é o estado atual. 
* Q(t+1) é o próximo estado.
  
Funcionalidade:
* J=0, K=0: Mantém o estado atual. 
* J=0, K=1: Reseta para 0. 
* J=1, K=0: Seta para 1. 
* J=1, K=1: Complementa (inverte) o estado. 

    Testes do Componente
    
Pinos de Entrada: J, K, Clock, Set, Clear.

Conexões Ativas:
* Para testar cada condição da tabela verdade, diferentes combinações de J e K devem ser aplicadas, com o clock pulando.
* As entradas Set e Clear podem ser usadas para inicializar o flip-flop em um estado conhecido antes de aplicar os sinais J e K. 
    
Resultado dos Pinos de Saída:
* Monitorar as saídas Q e Q' para verificar se correspondem aos valores esperados de acordo com a tabela verdade e as entradas aplicadas. 
      
Descrição dos Testes:
- Teste 1: Mantendo o Estado
    * J = 0, K = 0: Aplicar pulsos de clock. Verificar se Q e Q' mantêm seus valores iniciais. 
- Teste 2: Reset
    * J = 0, K = 1: Aplicar um pulso de clock. Verificar se Q se torna 0 e Q' se torna 1. 
- Teste 3: Set
    * J = 1, K = 0: Aplicar um pulso de clock. Verificar se Q se torna 1 e Q' se torna 0. 
- Teste 4: Complementação
    * J = 1, K = 1: Aplicar pulsos de clock alternadamente. Verificar se Q alterna entre 0 e 1. 
- Teste 5: Entradas Assíncronas
    * Set = 1: Verificar se Q se torna 1, independentemente dos valores de J, K e Clock. 
    * Clear = 1: Verificar se Q se torna 0, independentemente dos valores de J, K e Clock.
 
 # 2. Multiplexador de quatro opções de entrada.

Pinos e Funcionalidade:

* E0, E1, E2, E3: São as quatro entradas de dados. Cada uma pode ter um valor lógico 0 ou 1. 
* S0, S1: São as linhas de seleção. Essas duas linhas, juntas, formam um código binário de 2 bits que determina qual das quatro entradas será conectada à saída. 
* S: É a saída do multiplexador. O valor da saída será igual ao valor da entrada selecionada.
   
Lógica de Funcionamento:

A tabela verdade abaixo mostra como o multiplexador funciona para todas as combinações possíveis dos sinais de seleção:

![MULTPLEX TAB](https://github.com/user-attachments/assets/7ded86c1-dd38-40cc-817d-ddbabe26707a)

Como funciona na prática:
* Seleção da entrada: Os valores de S1 e S0 determinam qual das portas AND será ativada. 
* Saída: A saída do multiplexador será o valor da entrada conectada à porta AND ativada.

Os testes do componente

- Pinos de entrada: E0, E1, E2, E3, S0, S1.
 
Conexões ativas:
* Variar as entradas de dados: Para cada combinação de S0 e S1, defina o valor de apenas uma das entradas E0, E1, E2 ou E3 como 1, mantendo as demais em 0. 
* Combinar os sinais de seleção: Varie os valores de S0 e S1 para selecionar cada uma das quatro entradas.
  
* Resultado dos pinos de saída:

![multplexador](https://github.com/user-attachments/assets/204de77c-cb44-4aa0-a4db-8f9e40249520)

  
- Verificar a saída:
* A saída S deve corresponder ao valor da entrada selecionada de acordo com a tabela verdade.
  
- Descrição dos testes
1. Selecionando E1: 
* S0 = 0, S1 = 1 
* E1 = 1, E0 = E2 = E3 = 0 
* Verificar se S = 1.  

 # 3.  Porta lógica XOR usando os componentes: AND, NOT, e OR.

1. Descrição do Componente XOR e sua Funcionalidade
Pinos:
* A e B: Entradas digitais. 
* S: Saída digital.

![xor](https://github.com/user-attachments/assets/8405d860-b23a-4280-8f53-d1fbbd989a6b)

  
Lógica: 
* A saída S é 1 (verdadeiro) se e somente se uma e apenas uma das entradas A e B for 1. Em outras palavras, a saída é 1 quando as entradas são diferentes. A tabela verdade resume seu funcionamento:

![tabela xor](https://github.com/user-attachments/assets/1e3ad822-803b-4a2c-9d2e-197eae6abe74)


2. Funcionalidade: A porta XOR realiza a operação de ou exclusivo. Ela é utilizada em diversas aplicações, como:
* Comparadores: Para verificar se dois bits são diferentes. 
* Detectores de paridade: Para verificar se o número de bits 1 em um dado é par ou ímpar. 
* Somador de meio-somador: Para calcular a soma de dois bits, gerando a soma e o carry.
  
3. Testes do Componente XOR
   
Pinos de Entrada:

A, B. Conexões Ativas:
* Aplicar todas as combinações possíveis para as entradas A e B (00, 01, 10, 11). 
Resultado dos Pinos de Saída:
* Verificar se a saída S corresponde aos valores da tabela verdade para cada combinação de entrada.
  
4. Descrição dos Testes
- Teste 1: Ambas as entradas 0
* A = 0, B = 0 
* Verificar se S = 0.
- Teste 2: Uma entrada 0 e outra 1
* A = 0, B = 1 
* Verificar se S = 1. 
* A = 1, B = 0 
* Verificar se S = 1.
  
- Teste 3: Ambas as entradas 1
* A = 1, B = 1 
* Verificar se S = 0. 

# 4.  Somador de 8 bits que recebe um valor inteiro e soma com o valor 4.

1. Soma com valor 4:
* Nesse caso específico, o circuito está configurado para somar um número binário de 8 bits a um valor constante de 4 (representado em binário como 00000100). Isso significa que uma das entradas do somador sempre terá o valor 4.

![SOMADOR 8 BITS 4](https://github.com/user-attachments/assets/9c32f53a-4b8b-47bb-a526-f11a29c001e9)


2. Pinos e Funcionalidade:

Entradas: 
- A: Um número binário de 8 bits (A7A6A5A4A3A2A1A0). 
- B: Um número binário de 8 bits fixo em 00000100 (valor 4).

  Saídas: 
- S: A soma dos dois números de entrada (S7S6S5S4S3S2S1S0). 
- Cout: O bit de carry-out, indicando se houve um overflow na soma. 
Lógica de Funcionamento: O circuito utiliza somadores completos para realizar a soma bit a bit. Um somador completo tem três entradas (dois bits a serem somados e um carry-in) e duas saídas (soma e carry-out). O carry-out de cada somador completo é conectado ao carry-in do próximo somador mais significativo.

# 5.  Memória ROM de 8 bits.

1. Pinos e Funcionalidade:
* Entradas: 
* Endereço: Um conjunto de linhas que selecionam uma palavra de 8 bits específica armazenada na ROM. O número de linhas de endereço determina o número total de palavras que a ROM pode armazenar. 
* Saídas: 
2. Dados: Um conjunto de 8 linhas que fornecem o valor da palavra de 8 bits selecionada. 
Lógica de Funcionamento: A ROM funciona como uma tabela de verdade gigante. Cada combinação possível das linhas de endereço corresponde a uma única palavra de dados armazenada. Internamente, a ROM é construída com portas lógicas (AND, OR) que implementam essa tabela verdade. Quando um endereço específico é aplicado, as portas lógicas conectam a saída da ROM aos dados correspondentes.

![MEMORIA RON 8 B](https://github.com/user-attachments/assets/9118aa3f-6036-4796-bf73-2e622739ef65)

3. Os testes do componente
   
Pinos de entrada: Linhas de endereço.
Conexões ativas:
* Variar o endereço: Aplicar todas as combinações possíveis para as linhas de endereço. 
Resultado dos pinos de saída:
* Verificar os dados: Observar os valores nos pinos de dados para cada combinação de endereço. Esses valores devem corresponder aos dados pré-armazenados na ROM. 
4. Descrição dos testes
Exemplo de teste:
* Selecionar um endereço específico: Aplicar um valor binário nas linhas de endereço para selecionar uma determinada palavra. 
* Verificar a saída: Os pinos de dados devem indicar o valor da palavra selecionada, conforme a programação da ROM.
   
Outros testes: Repetir o procedimento acima para todas as combinações possíveis de endereços, garantindo que os dados lidos correspondam aos dados programados na ROM.

# 7.  Banco de Registradores de 8 bits.

1. Componentes e Funcionalidade:
   
Flip-flops D: São os elementos básicos de memória. Eles armazenam um bit de informação. A entrada D determina o valor que será armazenado no próximo pulso de clock. 
* Clock: Um sinal de clock sincroniza a operação de todos os flip-flops. Quando o clock muda de estado, os flip-flops atualizam seus valores de saída. 
* Entradas: As entradas servem para fornecer os dados que serão armazenados nos registradores. 
* Saídas: As saídas correspondem aos valores armazenados em cada registrador.
  
2. Como funciona: Quando um pulso de clock chega, o valor presente na entrada D de cada flip-flop é copiado para a saída do flip-flop. Dessa forma, a informação é armazenada.
![registrador 8 bits](https://github.com/user-attachments/assets/54b8a1d4-6de2-4de5-af8e-50d8d864a7e4)


3. Os testes do componente:
   
Pinos de entrada:
* Clock: Sinal de clock para sincronizar a operação dos flip-flops. 
* Entradas de dados: Linhas que fornecem os dados a serem armazenados em cada registrador.
  
Conexões ativas:
* Variar os dados de entrada: Aplicar diferentes combinações de bits nas entradas de dados. 
* Aplicar o sinal de clock: Gerar pulsos de clock para fazer com que os flip-flops atualizem seus valores.
  
4. Resultado dos pinos de saída:
* Verificar os valores armazenados: Observar os valores nas saídas para verificar se correspondem aos dados de entrada.
*  
5. Descrição dos testes
   
teste:
* Inicialização: Zerar todos os registradores. 
* Escrita: Aplicar um valor binário nas entradas de dados e gerar um pulso de clock. 
*  Leitura: Verificar se o valor nas saídas corresponde ao valor escrito. 
* Repetir: Realizar os passos 2 e 3 para diferentes combinações de dados de entrada. 


# 8.  Somador de 8 bits.

1. Componentes e Funcionalidade:
   
Somadores completos: A base de um somador de 8 bits. Cada somador completo recebe dois bits de entrada (um de cada número a ser somado) e um carry-in (vai um do bit menos significativo) e produz a soma e o carry-out. 

* Entradas: Duas entradas de 8 bits cada, representando os números a serem somados. 
* Saída: Uma saída de 8 bits representando a soma dos dois números de entrada e, possivelmente, um bit de carry-out.
  
2. Como funciona:
* Os somadores completos são conectados em cascata. O carry-out de um somador é conectado ao carry-in do próximo somador mais significativo. Dessa forma, a adição é realizada bit a bit, propagando o carry-out quando necessário.

   ![somador de 8 bits](https://github.com/user-attachments/assets/d307674b-7498-43f4-9d7d-f0155304d734)


3. Os testes do componente
   
Pinos de entrada:
* Entradas A e B: Dois conjuntos de 8 bits cada, representando os números a serem somados. 
Conexões ativas:

* Variar as entradas A e B: Aplicar diferentes combinações de bits nas entradas A e B.
   
Resultado dos pinos de saída:
* Verificar a soma: Observar os valores nas saídas para verificar se correspondem à soma dos números de entrada. 
* Verificar o carry-out: Se houver um bit de carry-out, verificar se ele é gerado corretamente em casos de overflow.
  
4.  Descrição dos testes
   
Exemplo de teste:
* 1. Soma de números pequenos: Somar números pequenos para verificar se a soma está sendo realizada corretamente. 
* 2. Soma de números grandes: Somar números grandes para verificar se o carry-out está sendo gerado corretamente em casos de overflow. 
* 3. Casos de borda: Testar casos onde um dos números é zero, onde ambos os números são iguais ao valor máximo, etc. 

# 9.  Detector de sequência binária para identificar a sequência "101" em um fluxo de entrada.

- Entradas: Uma sequência de bits de entrada, que representa o fluxo de dados.
   
* Circuito Combinacional: A parte central do circuito, composta por portas lógicas AND e OR, é responsável por detectar a sequência "101". Cada porta AND verifica a presença de um bit específico da sequência, e as portas OR combinam os resultados para indicar a ocorrência da sequência completa.

- Saída: Um único bit que indica se a sequência "101" foi detectada. Quando a sequência ocorre, a saída assume o valor lógico 1.
Como funciona:

2. O circuito funciona analisando os três bits de entrada de cada vez. Se os três bits corresponderem à sequência "101", a saída será 1, indicando a detecção da sequência. Caso contrário, a saída será 0.


![detector ](https://github.com/user-attachments/assets/731b09e3-bb76-46f9-9ef1-8f95797262f0)


3. Os testes do componente
Pinos de entrada:

* Entrada de dados: Uma sequência de bits de entrada.
  
Conexões ativas:

* Variar a entrada de dados: Aplicar diferentes combinações de bits nas entradas de dados.
Resultado dos pinos de saída:

* Verificar a saída: Observar o valor da saída para cada combinação de entrada. A saída deve ser 1 somente quando a sequência "101" estiver presente na entrada.
4. Descrição dos testes
Exemplo de teste:

* Sequência "101" no meio: Aplicar uma sequência de bits com "101" no meio e verificar se a saída é 1.
* Sequência "101" no início: Aplicar uma sequência de bits com "101" no início e verificar se a saída é 1.
* Sequência "101" no final: Aplicar uma sequência de bits com "101" no final e verificar se a saída é 1.
* Sequência "101" ausente: Aplicar várias sequências de bits sem a sequência "101" e verificar se a saída é sempre 0.

# 10.  ULA de 8 bits: AND, OR, NOT, NOR, NAND, XOR, SHIFT de 2 bits à esquerda, SHIFT de bits à direita, soma e subtração.

1. Componentes e Funcionalidades
* Entradas: Duas entradas de 8 bits cada, provavelmente representando os operandos para as operações aritméticas e lógicas. 
* Circuito Combinacional: Composto por portas lógicas AND, OR e possivelmente outras, realiza as operações lógicas e aritméticas básicas. 
* Multiplexador: Seleciona qual resultado da operação lógica ou aritmética será enviado para a saída. 
* Saída: Uma saída de 8 bits, que representa o resultado da operação selecionada. 
* Componentes Adicionais: Os componentes rotulados como "right", "count" e "bount" sugerem a possibilidade de operações de shift (deslocamento de bits) ou contagem, mas a ausência de detalhes impede uma afirmação definitiva. 
2. Funcionalidades Possíveis
*
Com base na estrutura, podemos inferir as seguintes funcionalidades:
* Operações Lógicas: AND, OR, NOT e possivelmente XOR. 
* Operações Aritméticas: Soma e subtração, possivelmente com complemento de dois. 
* Operações de Shift: Deslocamento de bits para a direita ou esquerda. 
* Operações de Contagem: Contagem de bits ou palavras.

![ula](https://github.com/user-attachments/assets/3f3eb24e-8d61-42a9-86b1-00ebc57a0cfa)


3. Como Funciona
  
* Entradas: Os dois operandos de 8 bits são fornecidos como entrada. 
* Circuito Combinacional: Realiza as operações lógicas e aritméticas básicas, como soma, subtração e operações lógicas. 
* Multiplexador: Seleciona qual resultado será enviado para a saída, com base em um sinal de controle (não explicitado na imagem). 
* Saída: O resultado selecionado pelo multiplexador é enviado para a saída de 8 bits. 
4. Testes e Simulação

* Identificar todos os componentes: Determinar o tipo de cada porta lógica e a função de cada componente adicional. 
* Definir as entradas: Criar um conjunto de testes com diferentes combinações de entrada para os operandos e o sinal de controle do multiplexador. 

# 11.  Extensor de sinal de 4 bits para 8 bits.

1. Descrição (os pinos e a lógica) do componente e sua funcionalidade

Um extensor de sinal é um circuito digital que duplica os bits de um número binário para aumentar sua largura em bits. No caso específico, este circuito expande um número de 4 bits para um número de 8 bits.

![extensor de sinal](https://github.com/user-attachments/assets/d219c016-d9cc-4407-ad31-02504756a2bb)


2. Os componentes principais são:
* Entradas: Quatro bits de entrada (A3, A2, A1, A0), representando o número de 4 bits a ser expandido. 
* Portas AND: Cada porta AND tem uma entrada conectada a um dos bits de entrada e a outra entrada conectada ao bit mais significativo (A3). 
* Saída: Oito bits de saída, sendo os quatro bits mais significativos cópias dos quatro bits menos significativos.
  
3. Como funciona:
Cada porta AND verifica se o bit mais significativo (A3) é 1. Se for, a saída da porta AND será igual ao bit de entrada correspondente. Isso garante que os bits mais significativos do número de 8 bits sejam cópias dos bits menos significativos.

4. Os testes do componente
   
Pinos de entrada:
* Entradas de 4 bits: Os quatro bits que representam o número a ser expandido. 
Conexões ativas:
* Variar as entradas de 4 bits: Aplicar diferentes combinações de bits nas entradas de 4 bits. 
5. Resultado dos pinos de saída:
* Verificar a saída: Observar os valores nas saídas para verificar se os quatro bits mais significativos são cópias dos quatro bits menos significativos. 
6. Descrição dos testes
----------------------------------
7. teste:
* Entrada 0000: Aplicar 0000 nas entradas de 4 bits e verificar se a saída é 00000000. 
* Entrada 1111: Aplicar 1111 nas entradas de 4 bits e verificar se a saída é 11111111. 
* Entrada aleatória: Aplicar diferentes combinações aleatórias de bits nas entradas de 4 bits e verificar se os quatro bits mais significativos são cópias dos quatro 8. bits menos significativos. 

12 Considerações Finais
Este trabalho apresentou o laboratório e implementação dos componentes dos circuitos. O objetivo principal era desenvolver os componentes, capaz de executar um conjunto básico de instruções. Os resultados obtidos demonstram que os circuitos é capaz de executar as instruções implementadas e atinge uma frequência de clock. A principal contribuição deste trabalho é a criação de um laboratório para o estudo de arquitetura de computadores. Como trabalhos futuros, sugere-se a implementação de um conjunto de instruções mais completo, a otimização do desempenho dos componentes e simplificado para rodar no processador.

 
  
