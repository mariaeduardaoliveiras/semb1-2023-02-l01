# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.

A compilação cruzada, também conhecida como "cross-compilation" em inglês, é o processo de compilação de código-fonte em um ambiente de desenvolvimento para que possa ser executado em uma plataforma ou arquitetura diferente daquela em que foi construída. Isso significa que a fonte do código é composta em uma máquina diferente que será executada. Esta compilação é utilizada no desenvolvimento de software para sistemas embarcados, dispositivos móveis e outras plataformas onde a arquitetura de hardware pode ser diferente daquela dos computadores tradicionais de desenvolvimento.
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?

Um código de inicialização é um conjunto de instruções de baixo nível que é executado assim que um sistema embarcado ou um programa de computador é inicializado. Sua finalidade é preparar o ambiente de execução para a execução do programa principal. Um exemplo é a Inicialização de Bibliotecas: em muitos sistemas, o código de inicialização é responsável por iniciar bibliotecas padrão e outras dependências permitidas para a execução do programa.
## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.

O arquivo Makefile é um arquivo de configuração, seu objetivo é a automatização nos processos de conformidade de projetos de desenvolvimento de software, ele especifica as regras e os comandos que o sistema de compilação deve seguir para criar os possíveis itens finais a partir do código-fonte e de outros arquivos associados ao projeto. Ele atua confirmando as alterações que foram feitas no arquivo de código-fonte e com isso regular quais partes do código precisam ser recompiladas e realizar apenas essas compilações específicas.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.

O importante faz começa fazendo a leitura do Makefile, em seguida examina os arquivos necessários para a execução do programa, determina se as reconstruções de alvos são fáceis, se permite se faz a execução de regras de construção correspondentes definidas no Makefile, atualiza os arquivos resultados da compilação e por fim conclui o processo.

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

NA arquitetura ARM Load/Store as instruções de acesso a memória só podem ser realizadas usando registradores de propósito geral, utilizando as intruções de load e store para acessar a memória. Já na Register/Register essas instruções podem ser acessadas diretamente, as operações aritmeticas também são realizadas de forma direta, enquanto na arquitetura ARM precisam ser realizadas apenas em registradores. 

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.

O processador ARM Cortex-M possui dois níveis de acesso, o privilegiado(Privileged) e o não privilegiado(Unprivileged), no nível privilegiado o processador possui acesso total as instruções do processador, acesso a todas as instruções e permissões para modificar registros de configuração, interrupções e outros aspectos do sistema, já no Unprivileged Mode, o software tem acesso limitado aos recursos do sistema, acesso restrito a certas instruções e não pode executar certas instruções privilegiadas. Sovre os modos de operações, a ARM Cortex-M possui três modos, o Handler Mode, Thread Mode e Privileged Mode. O primeiro sendo o modo quando ocorre interrupções e/ou excessões, possuindo acesso total aos recursos. O segundo, sendo o modo padrão e que possui acesso limitado aos recursos. Por fim, o Privileged Mode, que possui aceeso privelegiado a recursos do sistema independentemente do nível de acesso de execução de código. 

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.

Quando uma exceção ocorre, o processador interrompe a execução normal do programa e transfere o controle para um tratador de exceções, que é responsável por lidar com o evento e, possivelmente, tomar medidas corretivas. O mesmo ocorre quando acontece uma interrupção, salva o estado do processador (contexto), e transfere o controle para um tratador de interrupção associado àquela interrupção específica. 
Entre os diferentes tipos de excessão estão reset, IRQ,FIQ e SVC e possuem prioridades próprias. Sobre as interrupções, são criados grupos com as interrupções onde tem seus niveis de prioridade, e dentro de cada conjunto são colocadas prioridades globais, onde esses grupos são o Group priority, ou seja, prioridades mais altas. E as prioridades adicionais são as sub-priority, as interrupções podem ter uma subprioridade adicional. Isso permite que as interrupções dentro do mesmo grupo sejam priorizadas de acordo com sua subprioridade, caso duas ou mais interrupções ocorram simultaneamente.

 
### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?

O CPSR armazena informações sobre o estado atual da execução do programa, contém bits que indicam o modo de execução atual, informações de flag. Já SPSR armazena temporariamente, para que o estado do CPSR seja salvo antes que ocele seja alterado por uma execução ou interrupção. 

### (f) Qual a finalidade do **LR** (***Link Register***)?

A finalidade do Link Register é armazenar o endereço de retorno (ou link) de uma sub-rotina (função ou procedimento) após sua execução. Assim, permite que o programa volte a instrução de chamada quando concluir a sub-rotina ou função.
 
### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?

O propósito do PSR é armazenar informações sobre o estado atual do programa, além de gerenciar e controlar a execução do programa. 

### (h) O que é a tabela de vetores de interrupção?

A tabela de vetores é estrutura de dados responsável por mapear os endereços de memória de tradores de interrupções. Ou seja, quano ocorre uma interrupção, a tabela fornece a informação para o processsador saber para onde devera redirecionar, associando cada tipo de interrupção para um endereço específico. 


### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

O NVIC tem a finalidade de gerenciar as interrupções com eficiência, é utilizado em apliações em tempo real por meio de temporização de tarefas críticas, permite que tarefas seja temporizadas afim de resolver eventos externos de maior importância, priorização de tarefas, essas são resolvidades por meio de suas importâncias e urgências, oq garante que tarefas mais importantes sejam executadas primeiro e por fim, sincronização de periféricos externos com a execução do programa principal. 

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

Esse mecanismo serve para indentificar o contexto da interrupção e realizar o melhor retorno de interrupçãp, esse valor é determinado pelo hardware e codifica várias informações importantes sobre o estado anterior da execução do programa, incluindo o modo de exceção atual e se as pilhas foram trocadas. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 

A diferença no salvamento de contexto entre o Cortex-M3 e Cortez M4F está relacionanda ao (FPU - Floating Point Unit), no Cortex-M3 por náo ter FPU o salvamento envolve apenas os registradores de prósito geral, já o M4F que possui um ponte de FPU, o salvamento contém também os registradores de ponto flutuante. Ou seja, no M3 quando ocorre uma interrupção o salvamento ocorre automaticamente na pilha principal, enquanto no M4F pode ser usada uma pilha de contexto separada para os registradores de ponto flutuante. Lazy stack é uma tecnica de economia de tempo e espaço na pilha para o tratamento de interrupções, usando o lazy stack é possivel adiar o salvamento dos registradores de ponto flutuante até que eles sejam usados em uma interrupção, ele é configurado por meio do 'LSPACT' e esse bit pode ser configurado durante a inicialização do sistema para ativar ou desativar o lazy stack.


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
