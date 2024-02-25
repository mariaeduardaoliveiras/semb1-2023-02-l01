# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.

A compilação cruzada, também conhecida como "cross-compilation" em inglês, é o processo de compilar código-fonte em um ambiente de desenvolvimento para que possa ser executado em uma plataforma ou arquitetura diferente daquela em que foi compilado. Isso significa que o código-fonte é compilado em uma máquina diferente daquela em será executado. 
Esta compilação é utilizada em desenvolvimento de software para sistemas embarcados, dispositivos móveis e outras plataformas onde a arquitetura de hardware pode ser diferente daquela dos computadores tradicionais de desenvolvimento. 

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?

Um código de inicialização é um conjunto de instruções de baixo nível que é executado assim que um sistema embarcado ou um programa de computador é inicializado. Sua finalidade é preparar o ambiente de execução para a execução do programa principal. Um exemplo é a Inicialização de Bibliotecas: em muitos sistemas, o código de inicialização é resposável por iniciar bibliotecas padrão e outras dependências necessárias para a execução do programa. 

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.

O arquivo Makefile é um arquivo de configuração, seu objetivo é a automatização nos processos de compliação de projetos de desenvolvimento de software, ele especifica as regras e os comandos que o sistema de compilação deve seguir para criar os executáveis finais a partir do código-fonte e de outros arquivos associados ao projeto. Ele atua reconhecendo as alterações que foram feitas no arquivo de código-fonte e com isso reconhece quais partes do código precisam ser recompiladas e realiza apenas essas compilações específicas. 

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.

O utilitário make começa fazendo a leitura do Makefile, em seguida examina os arquivos necessários para a execução do programa, determina se reconstruções de alvos são necessárias, se necessárias se faz a execução de regras de construção correspondentes definidas no Makefile, atualiza os arquivos resultados da compilação e por fim conclui o processo. 


#### (c) Qual é a sintaxe utilizada para criar um novo **target**?

targets: prerequisites
          	recipe 


#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?

As dependências de target são definidas logo depois dos nome target, listando os pré-requisitos, que consistem em arquivos necessários para construir o alvo. Se algum dos pré-requisitos for mais recente do que o alvo, os comandos serão executados.  


#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
São instruções para como o programa deve ser compilado, as regras implicitas são as definidas pelo arquivo make e as explicitas são desenvolvidas pelo desenvolvedor. 

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?

O conjunto Thumb é um conjunto da arquitetura ARM mais compactada. Entre suas vantagens está a economia de espaço, onde utiliza-se apenas 16 bits, eficiência energética, por conta do menor número de instruções. O conjunto Thumb opera junto com o conjuto de intruções ARM por meio modo Thumb e o modo ARM. O modo Thumb s instruções são codificadas em 16 bits, sendo mais compactas que as instruções do modo ARM, que normalmente são codificadas em 32 bits e o modo ARM as instruções são codificadas em 32 bits, proporcionando uma maior variedade de operações, sendo assim nesse modo ignora-se as instruções Thumb. O processador ARM alterna entre os modos, obtendo as vantagens de ambos. 

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.



### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?

### (f) Qual a finalidade do **LR** (***Link Register***)?

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?

### (h) O que é a tabela de vetores de interrupção?

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
