[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/zHqjFsRx)
# Diagnóstico de retomada - Teoria da Computação

Esta atividade serve para mapear o que você já domina sobre linguagens formais, autômatos, gramáticas e computabilidade.

Responda individualmente. Use suas palavras. Se usar IA depois da primeira tentativa, registre o uso na seção 7.

## 1. Mapa do que eu lembro

Marque cada tópico como: lembro bem, lembro parcialmente, não lembro, nunca vi ou não tenho certeza.

- alfabeto: lembro bem
- cadeia: lembro parcialmente
- linguagem: lembro parcialmente
- gramática: lembro parcialmente
- autômato finito: lembro bem
- linguagem regular: lembro parcialmente
- linguagem livre de contexto: lembro parcialmente
- linguagem sensível ao contexto: embro bem
- linguagem irrestrita: embro bem
- hierarquia de Chomsky: embro parcialmente
- computabilidade: lembro bem
- máquina de Turing: lembro bem

## 2. Definições com exemplo

Explique, com suas palavras e com um exemplo simples, usando o alfabeto `Sigma = {a, b}`.

1. O que é um alfabeto?
   Um alfabeto é um conjunto finito de símbolos que não seja vazio, o próprio alfabeto citado acima exemplifica isso: "Sigma = {a, b}" é um conjunto formado pelos caracteres "a" e "b".

2. O que é uma cadeia?
   Uma cadeia é uma sequência finita de símbolos de um alfabeto, são todas as potenciais "palavras" formadas a partir dos símbolos presentes no alfabeto, no caso do alfabeto "Sigma = {a, b}" teríamos cadeias como {a, b}, {ab, ba, aa, bb}, {aba, bab, aab, baa}... etc.
   
3. O que é uma linguagem?
   Uma linguagem é o conjunto de todas as cadeias pertencentes a um alfabeto. No caso do alfabeto "Sigma = {a, b}", seriam todas as combinações possíveis de "a" e "b", tendo todos os comprimentos possíveis.
   
5. O que é uma gramática?
   A gramática é o conjunto de regras que rege a geração finita de cadeias pertencentes a uma linguagem.

## 3. Linguagens

Considere as linguagens:

```text
L1 = { w em {0,1}* | w termina com 01 }
L2 = { a^n b^n | n >= 0 }
L3 = { a^n b^n c^n | n >= 0 }
```

Para cada linguagem:

1. escreva três palavras que pertencem à linguagem;
   L1: {1101, 101, 0001, ...} Qualquer combinação de zeros e uns que finalixe em "01"

   L2: {ab, aabb, aaabbb, ...} Quantidade n de "a" seguida por uma quantidade n de "b"

   L3: {abc, aabbcc, aaabbbccc, ...} Quantidade n de "a" seguida por uma quantidade n de "b" seguida de quantidade n de "c".

2. escreva duas palavras que não pertencem;
   L1: {0111, 011}
   L2: {abb, aaab}
   L3: {abbccc, aabcc}

4. diga, se souber, em qual classe ela provavelmente se encaixa;
   L1: Linguagem Regular
   L2: Linguagem Livre de Contexto.
   L3: Linguagem Sensível ao Contexto.

5. explique o motivo em linguagem simples.
   L1: (Linguagem Regular) Ele só precisa lembrar dos dois últimos símbolos que leu para saber se aceita ou rejeita a cadeia (que é exatamente o que um Autômato Finito consegue fazer).
   L2: (Linguagem Livre de Contexto.) Um autômato finito (sem memória) não consegue contar infinitamente. Para saber quantos b devem vir, a máquina precisa usar uma "Pilha" (memória) para empilhar os as e depois desempilhar quando ler os bs, garantindo que as quantidades sejam iguais.
   L3: (Linguagem Sensível ao Contexto.) Para resolver isso, é necessário uma Máquina de Turing, que pode "caminhar" pela fita para frente e para trás marcando as letras.
Não há problema em dizer "não sei". Nesse caso, escreva o que te deixou em dúvida.

## 4. Autômato finito

Considere o autômato abaixo, sobre o alfabeto `{0,1}`:

```text
Estados: q0, q1, q2
Estado inicial: q0
Estado final: q2

Transições:
q0 --0--> q1
q0 --1--> q0
q1 --0--> q1
q1 --1--> q2
q2 --0--> q1
q2 --1--> q0
```

Responda:

1. Qual linguagem esse autômato parece reconhecer?
Para chegar no estado de aceitação (q2), o último caminho obrigatório é sair de q1 lendo um 1 e para chegar em q1, ele obrigatoriamente teve que ler um 0.
Ou seja, não importa quantas voltas ele dê, para parar no q2 a sua cadeia precisa necessariamente terminar com a sequência 0 seguida de 1.

Esse autômato reconhece a linguagem L1 da questão anterior (Cadeias que terminam em 01).


2. Execute manualmente as cadeias abaixo e diga se aceita ou rejeita:
   - `01` Aceita
   - `101` Aceita
   - `100` Rejeita
   - `1101` Aceita
   - `111` Rejeita
3. Monte uma tabela curta mostrando o caminho dos estados para pelo menos duas cadeias.

q0 --1--> q0
q0 --0--> q1
q1 --1--> q2 (Aceita - Estado Final)

q0 --1--> q0
q0 --0--> q1
q1 --0--> q1 (Rejeita - Não é Estado Final)

## 5. Gramática

Considere a gramática:

```text
S -> aS
S -> b
```

Responda:

1. Gere cinco cadeias produzidas por essa gramática.
(b, ab, aab, aaab, aaaab...)

2. Descreva a linguagem em palavras.
É uma linguagem formada por cadeias que começam com qualquer quantidade de letras "a" (inclusive nenhuma) e terminam sempre com uma única letra "b".

3. Essa gramática parece regular, livre de contexto ou outra classe? Justifique de forma simples.
É uma Gramática Regular, como ela cresce somente para um lado, e sempre tem a adição de um elemento não terminal "a", seguido de um elemento terminal "b", um automato finito conseguiria processar uma linguagem rugular gerada a partir dessa gramatica. 

## 6. Ponto de dificuldade

Escolha um tópico da lista inicial e escreva:

Tópico escolhido: Autômatos Finitos e Gramáticas (aplicação prática).

1. O que você entende dele:
Entendo a teoria básica por trás dos conceitos, como a ideia de que um autômato tem estados e transições para ler cadeias, e que uma gramática possui regras de produção para gerar palavras.

2. Onde você se confunde:
A prática ainda me gera muita dificuldade. Tive bastante dificuldade para resolver as questões envolvendo a execução manual de cadeias no autômato (questão 4) e a geração de palavras a partir das regras da gramática (questão 5). Para conseguir acompanhar e responder, precisei dar um passo para trás, revisar conteúdos passados e rever algumas atividades antigas sobre esses tópicos.

3. que tipo de explicação ajudaria: desenho, exemplo, exercício guiado, analogia, prova passo a passo ou lista curta.
Exercícios guiados passo a passo ajudariam muito, além de listas curtas com um "passo a passo" mental de como começar a resolver as questões práticas sem me perder nas transições ou nas regras.

## 7. Uso de IA, se houver

Se você usou IA depois da primeira tentativa, registre:

```text
Pergunta feita: Pedi ajuda para entender a lógica por trás da execução das cadeias no autômato (questão 4) e das regras da gramática (questão 5), além de pedir uma sugestão para formatar as tabelas de transição em texto puro.
Resumo da resposta: A IA explicou o passo a passo de como testar as cadeias "caminhando" pelos estados do autômato e como aplicar as regras de produção da gramática. Também me forneceu um modelo visual usando setas (ex: q0 --0--> q1) para facilitar a digitação das respostas.
Como eu verifiquei: Fiz a maior parte da minha revisão conceitual lendo materiais e atividades antigas da disciplina. Quando a IA me deu o passo a passo prático, eu conferi manualmente se as transições batiam com o desenho do autômato fornecido no exercício.
O que eu alterei na minha resposta: Reescrevi as justificativas com as minhas próprias palavras, baseando-me no que entendi das explicações, e adotei a formatação de setinhas sugerida pela IA para organizar a resposta da questão 4.
O que ainda não entendi: A lógica passo a passo fez sentido, mas ainda sinto falta de intuição prática. Bater o olho em um autômato ou gramática e deduzir a linguagem direto, sem ter que testar várias cadeias manualmente, é algo que ainda não domino.
```

## Submissão no Moodle

Depois de finalizar, copie no Moodle:

```text
Repositório: https://github.com/frndchagas-org/diagn-stico-de-retomada-teoria-da-computa-o-Andloc-Loi
Commit final: Atividade_Revisao_Aloisio
Autoavaliação: nível basico, Terminologias e Conteitos e Logica de Altomatos. e tópico que precisa ser retomado: Logica de Altomatos
```
