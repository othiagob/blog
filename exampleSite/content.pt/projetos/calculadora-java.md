---
title: "Calculadora em Java — Projeto de Console"
date: 2024-03-20
tags: ["java", "console", "iniciante"]
---

Primeiro projeto Java documentado no blog: uma calculadora de linha de
comando com suporte a múltiplas operações e tratamento de erros.

---

## Sobre o projeto

Uma calculadora simples rodando no terminal, desenvolvida para praticar
conceitos fundamentais de Java como:

- Leitura de entrada do usuário com `Scanner`
- Estruturas condicionais e switch
- Tratamento de exceções
- Organização em classes e métodos

## Código

```java
import java.util.Scanner;

public class Calculadora {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Primeiro número: ");
        double a = scanner.nextDouble();

        System.out.print("Operação (+, -, *, /): ");
        char op = scanner.next().charAt(0);

        System.out.print("Segundo número: ");
        double b = scanner.nextDouble();

        double resultado = calcular(a, op, b);
        System.out.printf("Resultado: %.2f%n", resultado);

        scanner.close();
    }

    public static double calcular(double a, char op, double b) {
        return switch (op) {
            case '+' -> a + b;
            case '-' -> a - b;
            case '*' -> a * b;
            case '/' -> {
                if (b == 0) throw new ArithmeticException("Divisão por zero");
                yield a / b;
            }
            default -> throw new IllegalArgumentException("Operação inválida: " + op);
        };
    }
}
```

## Como executar

```bash
javac Calculadora.java
java Calculadora
```

## O que aprendi

| Conceito              | Aplicado em                        |
|-----------------------|------------------------------------|
| `Scanner`             | Leitura de dados do console        |
| `switch` com arrow    | Seleção da operação (Java 14+)     |
| `yield`               | Retorno de valor dentro do switch  |
| Exceções              | Divisão por zero e op. inválida    |
| `printf` / formatação | Exibição com 2 casas decimais      |

Código disponível em breve no GitHub.
