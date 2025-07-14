	---
Com certeza! Aqui está o resumo de tudo o que conversamos sobre navegação no AstroNvim, formatado em um arquivo Markdown pronto para você salvar e consultar.

---

# Navegação Essencial no AstroNvim (Neovim)

Este guia cobre os principais comandos e dicas para navegar de forma eficiente vertical e horizontalmente no editor AstroNvim, que é construído sobre o Neovim.

---

## Navegação Vertical

Comandos para mover o cursor para cima e para baixo, e rolar a tela.

* **`j`**: Mover o cursor para **baixo** uma linha.
* **`k`**: Mover o cursor para **cima** uma linha.
* **`gj`**: Mover o cursor para **baixo** uma linha visual (útil para linhas longas que quebram).
* **`gk`**: Mover o cursor para **cima** uma linha visual.
* **`gg`**: Ir para o **início do arquivo**.
* **`G`**: Ir para o **final do arquivo**.
* **`<número>gg` ou `<número>G`**: Ir para a **linha especificada** pelo número (ex: `10gg` para ir para a linha 10).
* **`H`**: Mover o cursor para a **linha superior** da tela visível.
* **`M`**: Mover o cursor para a **linha do meio** da tela visível.
* **`L`**: Mover o cursor para a **linha inferior** da tela visível.
* **`Ctrl + f`**: Rolar a tela para **baixo uma página**.
* **`Ctrl + b`**: Rolar a tela para **cima uma página**.
* **`Ctrl + d`**: Rolar a tela para **baixo meia página**.
* **`Ctrl + u`**: Rolar a tela para **cima meia página**.
* **`{`**: Mover para o **início do parágrafo anterior** (ou bloco de código).
* **`}`**: Mover para o **início do próximo parágrafo**.

---

## Navegação Horizontal

Comandos para mover o cursor para a esquerda e para a direita dentro de uma linha.

* **`h`**: Mover o cursor para a **esquerda** um caractere.
* **`l`**: Mover o cursor para a **direita** um caractere.
* **`w`**: Mover para o **início da próxima palavra**.
* **`W`**: Mover para o **início da próxima palavra** (ignora pontuação como separador).
* **`b`**: Mover para o **início da palavra anterior**.
* **`B`**: Mover para o **início da palavra anterior** (ignora pontuação como separador).
* **`e`**: Mover para o **final da palavra atual**.
* **`E`**: Mover para o **final da palavra atual** (ignora pontuação como separador).
* **`0` (zero)**: Mover para o **início da linha** (primeiro caractere).
* **`^`**: Mover para o **primeiro caractere não em branco** da linha.
* **`$`**: Mover para o **final da linha**.
* **`f<char>`**: Procurar e ir para a **próxima ocorrência** de `<char>` na linha (ex: `fa`).
* **`F<char>`**: Procurar e ir para a **ocorrência anterior** de `<char>` na linha.
* **`t<char>`**: Mover **um caractere antes** da próxima ocorrência de `<char>` na linha.
* **`T<char>`**: Mover **um caractere depois** da ocorrência anterior de `<char>` na linha.
* **`;`**: **Repetir a última pesquisa** `f`, `F`, `t` ou `T` na mesma direção.
* **`,`**: **Repetir a última pesquisa** `f`, `F`, `t` ou `T` na direção oposta.

---

## Dicas de Navegação Úteis para Iniciantes

Estratégias avançadas e atalhos para otimizar seus movimentos.

### 1. Pesquisa Rápida

Use a pesquisa para saltar rapidamente para o conteúdo desejado.

* **`/` seguido de `palavra` + `Enter`**: Inicia uma **pesquisa para frente**.
* **`?` seguido de `palavra` + `Enter`**: Inicia uma **pesquisa para trás**.
* **`n`**: Ir para a **próxima ocorrência** da última pesquisa.
* **`N`**: Ir para a **ocorrência anterior** da última pesquisa.

### 2. Usando Marcadores (Marks)

Crie "pontos de save" no seu arquivo para retornar rapidamente.

* **`m<letra>`**: Define um **marcador local** (no arquivo atual) na posição do cursor (ex: `ma`).
* **`` `<letra> ``**: Retorna para a **posição exata** do marcador `<letra>` (ex: `` `a ``).
* **`` '<letra> ``**: Retorna para o **início da linha** onde o marcador `<letra>` foi definido (ex: `` 'a ``).
* **`` `. ``**: Retorna para a **última posição onde uma alteração** foi feita.
* **`` `' ``**: Retorna para o **início da linha da última alteração**.

### 3. Lista de Saltos (Jumplist)

Navegue pelo histórico de grandes movimentos dentro do editor.

* **`Ctrl + o`**: Mover para a **posição anterior** na lista de saltos.
* **`Ctrl + i`**: Mover para a **próxima posição** na lista de saltos.

### 4. Usando a Árvore de Arquivos (NvimTree)

Gerencie e navegue entre seus arquivos e diretórios.

* **`<leader> e` (padrão)** ou **`Ctrl + e`**: Alterna a visibilidade da **árvore de arquivos**.
    * Dentro da árvore de arquivos, use **`j`** e **`k`** para mover-se, e **`Enter`** para abrir arquivos ou expandir diretórios.

---

**Dica Final:** A prática constante é a chave para dominar a navegação no AstroNvim. Comece incorporando alguns comandos por dia até que se tornem um reflexo!

---

Espero que este arquivo Markdown seja muito útil para você! Há mais algum tópico do AstroNvim que você gostaria de detalhar ou explorar?
