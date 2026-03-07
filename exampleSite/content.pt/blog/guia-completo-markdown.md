---
title: "Guia Completo de Markdown"
date: 2024-03-01
tags: ["markdown", "guia", "escrita"]
---

Markdown é uma linguagem de marcação leve que permite formatar texto de forma
simples usando caracteres especiais. Neste guia você vai ver **tudo** que é
possível fazer.

---

## Títulos

Use `#` para criar títulos de diferentes níveis:

# Título H1
## Título H2
### Título H3
#### Título H4
##### Título H5
###### Título H6

---

## Ênfase no Texto

Você pode usar **negrito**, *itálico* ou ***negrito e itálico*** ao mesmo tempo.
Também é possível usar ~~tachado~~ para indicar algo removido.

---

## Listas

### Lista não ordenada

- Primeiro item
- Segundo item
  - Sub-item aninhado
  - Outro sub-item
- Terceiro item

### Lista ordenada

1. Primeiro passo
2. Segundo passo
3. Terceiro passo
   1. Sub-passo A
   2. Sub-passo B

### Lista de tarefas

- [x] Aprender Markdown
- [x] Criar um blog
- [ ] Publicar o primeiro post
- [ ] Compartilhar com amigos

---

## Links e Imagens

Um [link simples](https://gohugo.io) para o site do Hugo.

Um link com [título ao passar o mouse](https://gohugo.io "Site do Hugo").

Uma imagem:

![Logo do Hugo](https://gohugo.io/images/hugo-logo-wide.svg)

---

## Citações (Blockquotes)

> "Programar é como escrever um livro, exceto que se você esquecer um ponto
> e vírgula, o livro explode." — Anônimo

Citações aninhadas:

> Nível 1
>> Nível 2
>>> Nível 3

---

## Código

Código inline: use `backticks` para destacar `comandos` ou `variáveis`.

Bloco de código sem linguagem:

```
function hello() {
    console.log("Olá, mundo!");
}
```

Bloco de código com sintaxe destacada:

```python
def saudacao(nome: str) -> str:
    """Retorna uma saudação personalizada."""
    return f"Olá, {nome}! Bem-vindo ao blog."

if __name__ == "__main__":
    print(saudacao("othiagob"))
```

```bash
# Comandos úteis no terminal
git clone https://github.com/othiagob/blog.git
cd blog
hugo server --buildDrafts
```

---

## Tabelas

| Linguagem  | Paradigma    | Criada em | Popular para       |
|------------|-------------|----------:|--------------------|
| Python     | Multiparadigma | 1991   | IA, Data Science   |
| JavaScript | Multiparadigma | 1995   | Web Front-end      |
| Go         | Imperativa  | 2009      | Backend, DevOps    |
| Rust       | Sistemas    | 2010      | Sistemas, WASM     |
| TypeScript | Multiparadigma | 2012   | Web Full-stack     |

---

## Linha Horizontal

Três hífens criam uma linha divisória:

---

## HTML Inline

Você pode usar HTML quando o Markdown não for suficiente:

<details>
<summary>Clique para expandir</summary>

Este conteúdo fica escondido até você clicar!

</details>

---

## Escape de Caracteres

Para mostrar caracteres especiais sem formatação, use `\`:

\*não é itálico\* e \*\*não é negrito\*\*

---

É isso! Agora você conhece os principais recursos do Markdown. Use com
criatividade ✍️
