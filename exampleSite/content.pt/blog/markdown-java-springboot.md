---
title: "Markdown na prática para Java e Spring Boot"
date: 2026-05-20
tags: ["markdown", "java", "spring boot", "documentacao"]
---

Markdown é uma forma simples de escrever textos técnicos sem perder clareza.
Ele funciona muito bem para blogs, READMEs, anotações de estudo, documentação
de APIs e registros de decisões em projetos Java e Spring Boot.

Neste post eu reuni vários recursos úteis para formatar publicações e mostrar
como cada um pode aparecer em um artigo técnico.

## Títulos e hierarquia

Use títulos para organizar a leitura. Um artigo técnico normalmente fica mais
fácil de acompanhar quando cada ideia tem uma seção própria.

```md
# Título principal
## Seção
### Subseção
#### Detalhe
```

No blog, o título principal já vem do front matter do post. Dentro do conteúdo,
comece geralmente em `##`.

## Ênfase no texto

Você pode destacar ideias com **negrito**, _itálico_ e `código inline`.

```md
**Spring Boot** simplifica a criação de aplicações Java.
_Convenção sobre configuração_ ajuda a acelerar o desenvolvimento.
Use `@RestController` para criar endpoints HTTP.
```

Também é possível combinar estilos quando fizer sentido: **Java moderno com
_Spring Boot_**.

## Listas

Listas são ótimas para passos, recursos e comparações rápidas.

### Lista não ordenada

- Java é uma linguagem orientada a objetos.
- Spring Boot facilita configuração, empacotamento e execução.
- Maven e Gradle ajudam a gerenciar dependências.

### Lista ordenada

1. Criar o projeto.
2. Adicionar dependências.
3. Implementar controllers, services e repositories.
4. Rodar testes.
5. Publicar a aplicação.

## Links

Links ajudam a conectar o conteúdo com documentação oficial, repositórios e
referências.

```md
[Documentação do Spring Boot](https://spring.io/projects/spring-boot)
[Documentação do Java](https://docs.oracle.com/en/java/)
```

Exemplo em texto: o [Spring Boot](https://spring.io/projects/spring-boot) é uma
das formas mais populares de construir aplicações Java para web e APIs.

## Citações

Use citações para destacar uma ideia importante.

> Código bom não é apenas código que funciona. É código que outras pessoas
> conseguem ler, testar e manter.

Em projetos Java, isso significa escrever classes com responsabilidades claras,
nomes consistentes e testes que expliquem o comportamento esperado.

## Blocos de código

Blocos de código são essenciais em posts técnicos. Indique a linguagem para o
Hugo aplicar destaque de sintaxe.

```java
package dev.othiagob.blog;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HealthController {

    @GetMapping("/health")
    public String health() {
        return "Aplicação Spring Boot online";
    }
}
```

## Código de configuração

Markdown também funciona bem para arquivos de configuração.

```yaml
spring:
  application:
    name: blog-api
  datasource:
    url: jdbc:postgresql://localhost:5432/blog
    username: blog
    password: secret
```

E para Maven:

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

## Tabelas

Tabelas ajudam quando você precisa comparar conceitos.

| Conceito | Em Java | No Spring Boot |
|----------|---------|----------------|
| Classe | Define estrutura e comportamento | Pode representar controller, service, entity ou config |
| Interface | Define contratos | Facilita desacoplamento e testes |
| Anotação | Metadado no código | Configura componentes como `@Service` e `@Repository` |
| Injeção de dependência | Pode ser feita manualmente | É gerenciada pelo container do Spring |

## Separadores

Use uma linha horizontal para dividir partes grandes do conteúdo.

---

Depois do separador, você pode iniciar outra etapa do artigo, como uma conclusão
ou um exemplo completo.

## Imagens e figuras

Quando houver imagens na pasta `static`, você pode referenciá-las no Markdown.

```md
![Descrição da imagem](/images/favicon.png)
```

Exemplo:

![Favicon do blog](/images/favicon.png)

Sempre escreva uma descrição útil no texto alternativo. Isso melhora
acessibilidade e ajuda quem usa leitores de tela.

## Checklists

Checklists são bons para guias práticos.

- [x] Criar endpoint REST
- [x] Separar regra de negócio em service
- [ ] Adicionar testes automatizados
- [ ] Configurar banco de dados de produção

## Exemplo de estrutura de projeto

```text
src/main/java/dev/othiagob/blog
├── controller
├── service
├── repository
├── model
└── BlogApplication.java
```

Uma estrutura simples já ajuda bastante:

- `controller`: recebe chamadas HTTP.
- `service`: concentra regras de negócio.
- `repository`: conversa com o banco de dados.
- `model`: representa entidades e objetos do domínio.

## Dicas para escrever bons posts técnicos

1. Explique o problema antes do código.
2. Mostre um exemplo pequeno funcionando.
3. Evite pular etapas importantes.
4. Use tabelas para comparar decisões.
5. Termine com próximos passos ou melhorias possíveis.

## Exemplo completo em Spring Boot

```java
package dev.othiagob.blog;

import java.util.List;
import org.springframework.stereotype.Service;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

record Artigo(String titulo, String categoria) {}

@Service
class ArtigoService {

    List<Artigo> listar() {
        return List.of(
            new Artigo("Collections em Java", "java"),
            new Artigo("APIs REST com Spring Boot", "spring boot")
        );
    }
}

@RestController
@RequestMapping("/artigos")
class ArtigoController {

    private final ArtigoService service;

    ArtigoController(ArtigoService service) {
        this.service = service;
    }

    @GetMapping
    List<Artigo> listar() {
        return service.listar();
    }
}
```

Esse exemplo mostra vários pontos importantes:

- `record` reduz código repetitivo para objetos simples.
- `@Service` marca uma classe de regra de negócio.
- `@RestController` expõe endpoints HTTP.
- Injeção por construtor deixa dependências explícitas.
- `List.of` cria uma lista imutável para o exemplo.

## Conclusão

Markdown é simples, mas poderoso. Com títulos, listas, tabelas, links, citações,
imagens, checklists e blocos de código, dá para criar publicações técnicas bem
organizadas sobre Java, Spring Boot e qualquer outro tema de desenvolvimento.

Para estudar e documentar projetos, ele é uma ferramenta excelente: rápido de
escrever, fácil de versionar no Git e perfeito para publicar em um blog estático
com Hugo.
