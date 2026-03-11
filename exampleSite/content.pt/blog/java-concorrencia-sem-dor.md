---
title: "Java e Concorrência Sem Dor"
date: 2026-03-11
tags: ["java", "concorrência", "threads", "desempenho"]
---

Concorrência em Java não precisa ser um bicho de sete cabeças. A ideia central
é simples: dividir trabalho de forma segura sem corromper estado.

## 1. O problema clássico: condição de corrida

Quando duas threads alteram o mesmo dado ao mesmo tempo, o resultado pode ficar
inconsistente.

```java
public class Contador {
    private int valor = 0;

    public void incrementar() {
        valor++; // não é operação atômica
    }

    public int getValor() {
        return valor;
    }
}
```

## 2. Solução inicial com AtomicInteger

Para contadores simples, prefira tipos atômicos.

```java
import java.util.concurrent.atomic.AtomicInteger;

public class ContadorSeguro {
    private final AtomicInteger valor = new AtomicInteger(0);

    public void incrementar() {
        valor.incrementAndGet();
    }

    public int getValor() {
        return valor.get();
    }
}
```

## 3. ExecutorService no lugar de Thread manual

Gerenciar threads manualmente costuma gerar código difícil de manter.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class Processador {
    public void executar() throws InterruptedException {
        ExecutorService pool = Executors.newFixedThreadPool(4);

        for (int i = 0; i < 20; i++) {
            int tarefa = i;
            pool.submit(() -> System.out.println("Processando tarefa " + tarefa));
        }

        pool.shutdown();
        pool.awaitTermination(10, TimeUnit.SECONDS);
    }
}
```

## 4. CompletableFuture para fluxos assíncronos

Quando há dependência entre tarefas assíncronas, CompletableFuture deixa o
fluxo mais legível.

```java
import java.util.concurrent.CompletableFuture;

public class RelatorioService {
    public CompletableFuture<String> gerarRelatorio() {
        return CompletableFuture.supplyAsync(this::buscarDados)
            .thenApply(this::processar)
            .thenApply(this::formatar);
    }

    private String buscarDados() { return "dados"; }
    private String processar(String entrada) { return entrada.toUpperCase(); }
    private String formatar(String entrada) { return "Relatório: " + entrada; }
}
```

## 5. Checklist para produção

- Limite o número de threads conforme CPU e perfil da aplicação.
- Evite estado mutável compartilhado.
- Prefira estruturas thread-safe quando necessário.
- Sempre faça shutdown de pools.
- Adicione logs e métricas para investigar gargalos.

Com essas práticas, você ganha performance sem abrir mão de previsibilidade.
