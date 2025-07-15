---
layout: post
title: "Vetores em C: 5 Exemplos Essenciais para Iniciantes"
date: 2025-07-14 11:00:00 -0300
categories: [programação, c]
tags: [c, vetores, arrays, programação, iniciantes]
---

# Vetores em C: 5 Exemplos Essenciais para Iniciantes

Este post apresenta 5 exemplos práticos de vetores na linguagem C, explicados de forma simples e direta. Cada exemplo inclui código comentado, explicação detalhada e a saída esperada.

## O que são vetores?

**Vetores** (também chamados de arrays) são estruturas de dados que armazenam múltiplos elementos do mesmo tipo em posições consecutivas na memória. Cada elemento é acessado através de um índice numérico, começando do 0.

---

## Exemplo 1: Criando e exibindo um vetor

```c
#include <stdio.h>

int main() {
    // Criando um vetor com 5 números inteiros
    int numeros[5] = {10, 20, 30, 40, 50};
    
    // Exibindo todos os elementos
    printf("Elementos do vetor:\n");
    for (int i = 0; i < 5; i++) {
        printf("numeros[%d] = %d\n", i, numeros[i]);
    }
    
    return 0;
}
```

**Explicação:**
- `int numeros[5]`: declara um vetor de 5 inteiros
- `{10, 20, 30, 40, 50}`: inicializa os valores
- `for (int i = 0; i < 5; i++)`: percorre todos os elementos
- `numeros[i]`: acessa o elemento na posição i

**Saída:**
```
Elementos do vetor:
numeros[0] = 10
numeros[1] = 20
numeros[2] = 30
numeros[3] = 40
numeros[4] = 50
```

---

## Exemplo 2: Lendo valores do usuário

```c
#include <stdio.h>

int main() {
    int notas[3];
    
    // Lendo as notas do usuário
    printf("Digite 3 notas:\n");
    for (int i = 0; i < 3; i++) {
        printf("Nota %d: ", i + 1);
        scanf("%d", &notas[i]);
    }
    
    // Exibindo as notas
    printf("\nNotas digitadas:\n");
    for (int i = 0; i < 3; i++) {
        printf("Nota %d: %d\n", i + 1, notas[i]);
    }
    
    return 0;
}
```

**Explicação:**
- `int notas[3]`: declara um vetor vazio de 3 inteiros
- `scanf("%d", &notas[i])`: lê um valor e armazena na posição i
- `&notas[i]`: endereço da posição i do vetor

**Saída (exemplo):**
```
Digite 3 notas:
Nota 1: 85
Nota 2: 92
Nota 3: 78

Notas digitadas:
Nota 1: 85
Nota 2: 92
Nota 3: 78
```

---

## Exemplo 3: Calculando a média

```c
#include <stdio.h>

int main() {
    int valores[4] = {15, 25, 35, 45};
    int soma = 0;
    float media;
    
    // Calculando a soma
    for (int i = 0; i < 4; i++) {
        soma += valores[i];
    }
    
    // Calculando a média
    media = (float)soma / 4;
    
    printf("Valores: ");
    for (int i = 0; i < 4; i++) {
        printf("%d ", valores[i]);
    }
    
    printf("\nSoma: %d\n", soma);
    printf("Média: %.2f\n", media);
    
    return 0;
}
```

**Explicação:**
- `soma += valores[i]`: adiciona cada elemento à soma total
- `(float)soma / 4`: converte para float para obter média decimal
- `%.2f`: formata a saída com 2 casas decimais

**Saída:**
```
Valores: 15 25 35 45 
Soma: 120
Média: 30.00
```

---

## Exemplo 4: Encontrando o maior elemento

```c
#include <stdio.h>

int main() {
    int numeros[6] = {12, 45, 7, 23, 67, 34};
    int maior = numeros[0];
    int posicao = 0;
    
    // Procurando o maior elemento
    for (int i = 1; i < 6; i++) {
        if (numeros[i] > maior) {
            maior = numeros[i];
            posicao = i;
        }
    }
    
    printf("Vetor: ");
    for (int i = 0; i < 6; i++) {
        printf("%d ", numeros[i]);
    }
    
    printf("\nMaior elemento: %d\n", maior);
    printf("Posição: %d\n", posicao);
    
    return 0;
}
```

**Explicação:**
- `int maior = numeros[0]`: assume que o primeiro elemento é o maior
- `if (numeros[i] > maior)`: compara cada elemento com o maior atual
- `posicao = i`: guarda a posição do maior elemento

**Saída:**
```
Vetor: 12 45 7 23 67 34 
Maior elemento: 67
Posição: 4
```

---

## Exemplo 5: Contando elementos específicos

```c
#include <stdio.h>

int main() {
    int numeros[8] = {2, 7, 4, 9, 6, 3, 8, 5};
    int pares = 0;
    int impares = 0;
    
    // Contando pares e ímpares
    for (int i = 0; i < 8; i++) {
        if (numeros[i] % 2 == 0) {
            pares++;
        } else {
            impares++;
        }
    }
    
    printf("Números: ");
    for (int i = 0; i < 8; i++) {
        printf("%d ", numeros[i]);
    }
    
    printf("\nNúmeros pares: %d\n", pares);
    printf("Números ímpares: %d\n", impares);
    
    return 0;
}
```

**Explicação:**
- `numeros[i] % 2 == 0`: verifica se o número é par (resto da divisão por 2 é 0)
- `pares++`: incrementa o contador de números pares
- `impares++`: incrementa o contador de números ímpares

**Saída:**
```
Números: 2 7 4 9 6 3 8 5 
Números pares: 4
Números ímpares: 4
```

---

## Dicas importantes

1. **Índices começam em 0**: O primeiro elemento está na posição 0, não 1
2. **Tamanho fixo**: O tamanho do vetor deve ser definido na declaração
3. **Mesmo tipo**: Todos os elementos devem ser do mesmo tipo de dados
4. **Cuidado com os limites**: Acessar posições inexistentes causa erros
5. **Inicialização**: Vetores podem ser inicializados na declaração

## Próximos passos

Agora que você entende os conceitos básicos de vetores, pode praticar criando seus próprios exemplos e experimentar com diferentes tipos de dados (float, char, etc.).

---

*Gostou do conteúdo? Compartilhe e continue praticando!*
