# DigiAdders

Biblioteca de somadores digitais para o [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution). O arquivo `somadores.circ` reúne, em um único projeto, sete arquiteturas de somadores, do Half Adder ao Kogge-Stone, para estudar na prática como cada uma lida com a propagação do carry.

Desenvolvido como parte de um projeto de extensão (NERD) da Universidade Federal do Paraná (UFPR), sob orientação do Prof. Dr. Daniel Afonso Gonçalves de Oliveira.

## Somadores incluídos

| Circuito | Largura | Ideia principal |
|---|---|---|
| Half Adder | 1 bit | Soma de dois bits com uma porta XOR e uma AND |
| Full Adder | 1 bit | Dois Half Adders e uma porta OR, com carry de entrada |
| Ripple Carry Adder (RCA) | 4 bits | Full Adders em cascata, com o carry propagado de estágio em estágio |
| Carry Lookahead Adder (CLA) | 4 bits | Todos os carries calculados em paralelo a partir dos sinais de geração (G) e propagação (P) |
| Carry Select Adder | 8 bits | Dois blocos RCA em paralelo (Cin = 0 e Cin = 1) e multiplexadores para escolher o resultado |
| Carry Save Adder (CSA) | 4 bits | Soma de três operandos, com os carries salvos em vez de propagados |
| Kogge-Stone Adder | 8 bits | Árvore de prefixos em três níveis, com todos os carries calculados em paralelo |

## Organização

Cada somador é um subcircuito dentro de `somadores.circ`, construído de forma incremental e reutilizando os anteriores:

- `HalfAdder` é a base do `FullAdder`.
- `FullAdder` é a base do `RippleCarryAdder`.
- `RippleCarryAdder` é reutilizado no Carry Select Adder e como somador final do Carry Save Adder.
- `prefix_operator` é o nó da árvore do Kogge-Stone e combina dois pares (G, P) em um.

Como são subcircuitos, qualquer um deles pode ser instanciado em outro projeto do Logisim, por exemplo dentro de uma ULA.

## Como usar

1. Instale o [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution/releases).
2. Abra o arquivo `somadores.circ`.
3. Escolha um dos circuitos no painel de exploração, à esquerda.
4. Use a ferramenta de interação (dedo) para alterar as entradas e observe as saídas e o caminho do carry.

Para usar os somadores em outro projeto, importe a biblioteca pelo menu *Projeto > Carregar biblioteca > Biblioteca do Logisim* e selecione o `somadores.circ`.

## Relatório

O relatório que acompanha o projeto (`somadores.pdf`) descreve a teoria de cada arquitetura, as decisões de projeto e a comparação entre elas.

## Autor

Bruno Yuuki Hayashi, estudante de Ciência da Computação, UFPR.
