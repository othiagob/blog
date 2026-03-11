---
title: "Java na Prática: POO Sem Mistério"
date: 2026-03-11
tags: ["java", "poo", "orientação a objetos", "iniciante"]
---

Programação orientada a objetos em Java parece complexa no início, mas fica
simples quando você enxerga cada conceito como uma ferramenta para organizar
melhor o código.

Neste post, vamos construir uma pequena API de pedidos para consolidar os
4 pilares da POO: encapsulamento, herança, abstração e polimorfismo.

## 1. Encapsulamento: proteja o estado

Encapsular é esconder detalhes internos da classe e expor apenas o que é
necessário para uso.

```java
public class Conta {
    private final String titular;
    private double saldo;

    public Conta(String titular, double saldoInicial) {
        if (saldoInicial < 0) {
            throw new IllegalArgumentException("Saldo inicial não pode ser negativo");
        }
        this.titular = titular;
        this.saldo = saldoInicial;
    }

    public String getTitular() {
        return titular;
    }

    public double getSaldo() {
        return saldo;
    }

    public void depositar(double valor) {
        if (valor <= 0) {
            throw new IllegalArgumentException("Valor de depósito inválido");
        }
        saldo += valor;
    }

    public void sacar(double valor) {
        if (valor <= 0 || valor > saldo) {
            throw new IllegalArgumentException("Saque inválido");
        }
        saldo -= valor;
    }
}
```

## 2. Abstração: modele o que importa

Abstração é representar regras de negócio sem trazer complexidade
desnecessária para a interface pública.

```java
public interface Frete {
    double calcular(double pesoEmKg, String cepDestino);
}
```

A regra interna pode mudar, mas quem usa a interface continua chamando do
mesmo jeito.

## 3. Herança: reuse com critério

Herança funciona bem quando existe uma relação clara de "é um".

```java
public abstract class Funcionario {
    protected final String nome;

    protected Funcionario(String nome) {
        this.nome = nome;
    }

    public abstract double calcularBonus(double salarioBase);
}

public class Desenvolvedor extends Funcionario {
    public Desenvolvedor(String nome) {
        super(nome);
    }

    @Override
    public double calcularBonus(double salarioBase) {
        return salarioBase * 0.15;
    }
}
```

## 4. Polimorfismo: uma interface, múltiplos comportamentos

Com polimorfismo, você trata objetos diferentes por um contrato comum.

```java
import java.util.List;

public class FolhaPagamento {
    public double totalBonificacao(List<Funcionario> funcionarios, double salarioBase) {
        return funcionarios.stream()
            .mapToDouble(f -> f.calcularBonus(salarioBase))
            .sum();
    }
}
```

## Erros comuns em POO com Java

- Criar classes gigantes com muitas responsabilidades.
- Expor atributos públicos sem validação.
- Usar herança quando composição seria melhor.
- Misturar regra de negócio com I/O (console, banco, HTTP) na mesma classe.

## Dica prática

Antes de criar uma classe, responda:

- Qual responsabilidade única ela terá?
- Quais invariantes ela precisa proteger?
- Ela depende de abstração (interface) para facilitar testes?

Se essas respostas estiverem claras, seu código tende a escalar melhor.
