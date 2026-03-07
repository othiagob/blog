---
title: "Código Limpo: Princípios que Todo Dev Deveria Conhecer"
date: 2024-03-15
tags: ["programação", "boas práticas", "código"]
---

Escrever código que funciona é uma coisa. Escrever código que outras pessoas
(e você mesmo no futuro) consigam entender é outra completamente diferente.

> "Qualquer tolo pode escrever código que um computador entende. Bons
> programadores escrevem código que humanos entendem." — Martin Fowler

---

## 1. Nomes que Comunicam Intenção

Evite abreviações enigmáticas. O nome de uma variável, função ou classe deve
revelar **por que existe** e **o que faz**.

**Ruim:**
```python
d = 86400  # o que é isso?
def calc(x, y):
    return x * y
```

**Bom:**
```python
SEGUNDOS_POR_DIA = 86400

def calcular_area_retangulo(largura: float, altura: float) -> float:
    return largura * altura
```

---

## 2. Funções Pequenas e com Uma Responsabilidade

Uma função deve fazer **uma coisa** e fazer bem feita. Se você precisar escrever
"e" ao descrever o que ela faz, é sinal de que pode ser dividida.

```go
// Ruim: uma função faz muita coisa
func processarPedido(pedido Pedido) {
    validarPedido(pedido)
    calcularTotal(pedido)
    aplicarDesconto(pedido)
    salvarNoBanco(pedido)
    enviarEmailConfirmacao(pedido)
    atualizarEstoque(pedido)
}

// Bom: responsabilidades separadas
func processarPedido(pedido Pedido) error {
    if err := validarPedido(pedido); err != nil {
        return fmt.Errorf("pedido inválido: %w", err)
    }
    return finalizarCompra(pedido)
}
```

---

## 3. Comentários: Menos é Mais

O melhor comentário é o código que se explica sozinho. Comente o **porquê**,
não o **o quê**.

```javascript
// Ruim: comentário óbvio
// incrementa i em 1
i++;

// Bom: explica uma decisão não óbvia
// Usando 33ms (30fps) em vez de 16ms (60fps) para economizar bateria em mobile
const INTERVALO_ANIMACAO = 33;
```

---

## 4. Tratamento de Erros

Nunca ignore erros silenciosamente. Seja explícito:

```python
# Ruim
try:
    resultado = dividir(a, b)
except:
    pass  # swallowing the error 😱

# Bom
try:
    resultado = dividir(a, b)
except ZeroDivisionError:
    logger.error("Tentativa de divisão por zero: a=%s, b=%s", a, b)
    raise ValueError("O divisor não pode ser zero") from None
```

---

## 5. Princípio DRY — Don't Repeat Yourself

Se você está copiando e colando código, é sinal de que precisa de uma abstração:

```typescript
// Ruim: lógica repetida
function validarEmail(email: string): boolean {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return regex.test(email);
}

function validarEmailAdmin(email: string): boolean {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/; // mesma regex!
  return regex.test(email) && email.endsWith("@empresa.com");
}

// Bom: reutiliza a lógica
const EMAIL_REGEX = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

function isEmailValido(email: string): boolean {
  return EMAIL_REGEX.test(email);
}

function isEmailAdmin(email: string): boolean {
  return isEmailValido(email) && email.endsWith("@empresa.com");
}
```

---

## Checklist Rápido

Antes de fazer commit, pergunte-se:

| Critério                              | ✅ / ❌ |
|---------------------------------------|--------|
| Os nomes estão claros e descritivos?  |        |
| As funções fazem apenas uma coisa?    |        |
| Não há código duplicado?              |        |
| Os erros são tratados corretamente?   |        |
| O código passa nos testes?            |        |
| Um colega conseguiria entender?       |        |

---

Código limpo não é luxo — é **respeito** pelos seus colegas e pelo seu eu do
futuro. 🚀
