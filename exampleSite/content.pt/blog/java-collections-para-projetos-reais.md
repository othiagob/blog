---
title: "Java Collections para Projetos Reais"
date: 2026-03-11
tags: ["java", "collections", "estrutura de dados", "backend"]
---

Dominar a Collections Framework em Java evita bugs e melhora desempenho.
Escolher entre List, Set e Map não é só sintaxe: é decisão de modelagem.

## 1. List: quando ordem importa

Use List quando você precisa manter a ordem e permitir elementos repetidos.

```java
import java.util.ArrayList;
import java.util.List;

List<String> tarefas = new ArrayList<>();
tarefas.add("Revisar PR");
tarefas.add("Publicar release");
tarefas.add("Revisar PR");
```

### Quando escolher

- Sequência de itens para exibição.
- Processamento por índice.
- Fila simples de execução.

## 2. Set: quando unicidade é requisito

Set não permite duplicados. Excelente para deduplicação.

```java
import java.util.HashSet;
import java.util.Set;

Set<String> tags = new HashSet<>();
tags.add("java");
tags.add("backend");
tags.add("java"); // ignorado
```

### Quando escolher

- Validar valores únicos (e-mail, slug, IDs externos).
- Normalizar dados antes de persistir.

## 3. Map: quando você precisa de chave -> valor

Map é ideal para indexação e acesso rápido por chave.

```java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> estoque = new HashMap<>();
estoque.put("teclado", 20);
estoque.put("mouse", 35);

int qtd = estoque.getOrDefault("monitor", 0);
```

## 4. Implementações e trade-offs

| Estrutura      | Melhor para                        | Observação |
|----------------|------------------------------------|------------|
| ArrayList      | Leitura por índice                 | Inserção no meio é mais custosa |
| LinkedList     | Inserções/remoções frequentes      | Acesso por índice é mais lento |
| HashSet        | Unicidade com boa performance      | Não mantém ordem |
| LinkedHashSet  | Unicidade + ordem de inserção      | Leve overhead de memória |
| HashMap        | Busca por chave                    | Não mantém ordem |
| TreeMap        | Chaves ordenadas                   | Custo maior por operação |

## 5. Imutabilidade para segurança

Sempre que possível, exponha coleções imutáveis para evitar alterações
acidentais.

```java
import java.util.List;

public class Projeto {
    private final List<String> membros;

    public Projeto(List<String> membros) {
        this.membros = List.copyOf(membros);
    }

    public List<String> getMembros() {
        return membros;
    }
}
```

## 6. Boas práticas rápidas

- Prefira interfaces na declaração: List, Set, Map.
- Escolha implementação com base em uso real, não por hábito.
- Evite null em coleções: retorne coleção vazia.
- Use streams com moderação, priorizando legibilidade.

Uma boa decisão de coleção hoje evita retrabalho de performance amanhã.
