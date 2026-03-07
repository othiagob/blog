# ᕦʕ •ᴥ•ʔᕤ Bear Cub

[![github pages](https://github.com/clente/hugo-bearcub/actions/workflows/gh-pages.yml/badge.svg)](https://github.com/clente/hugo-bearcub/actions/workflows/gh-pages.yml)
[![MIT license](https://img.shields.io/github/license/clente/hugo-bearcub)](https://github.com/clente/hugo-bearcub/blob/main/LICENSE)

## Visão Geral

🐻 Um tema leve para o [Hugo](https://gohugo.io/) baseado no [Bear
Blog](https://bearblog.dev) e no [Hugo Bear
Blog](https://github.com/janraasch/hugo-bearblog).

O **Bear Cub** cuida da velocidade e da otimização para que você possa se concentrar
em escrever bom conteúdo. É gratuito, multilíngue, otimizado para mecanismos de busca,
sem frescuras, responsivo, leve e rápido. Muito rápido.

## Instalação

Siga o [guia de início rápido](https://gohugo.io/getting-started/quick-start/) do Hugo para
criar um site vazio e, em seguida, clone o **Bear Cub** no diretório de temas como
um [submódulo Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules):

```sh
git submodule add https://github.com/clente/hugo-bearcub themes/hugo-bearcub
```

Para finalizar, adicione uma linha ao arquivo de configuração do site:

```sh
echo 'theme = "hugo-bearcub"' >> hugo.toml
```

## Funcionalidades

Assim como o [Bear Blog](https://bearblog.dev), este tema:
- É gratuito e de código aberto
- Tem boa aparência em qualquer dispositivo
- Gera páginas minúsculas (~5kb), otimizadas e incríveis
- Não possui rastreadores, anúncios ou scripts
- Gera automaticamente um feed RSS

Mas não é só isso! O **Bear Cub** também é...

### Acessível

O **Bear Cub** possui algumas melhorias de acessibilidade em comparação com seus predecessores.
A paleta de cores foi reformulada para garantir que tudo seja
[legível](https://web.dev/color-and-contrast-accessibility/) para usuários com baixa
visão ou deficiências de cor, e alguns elementos interativos foram
aumentados para facilitar o [clique](https://web.dev/accessible-tap-targets/)
para usuários com dificuldades motoras.

Essas pequenas mudanças fazem com que o **Bear Cub** passe no [teste PageSpeed
](https://pagespeed.web.dev/report?url=https%3A%2F%2Fclente.github.io%2Fhugo-bearcub%2F)
do Google com louvor.

![Pontuação PageSpeed](https://raw.githubusercontent.com/clente/hugo-bearcub/main/images/pagespeed.webp)

### Seguro

[A demonstração do **Bear Cub**](https://clente.github.io/hugo-bearcub/) está hospedada no GitHub
e, portanto, não tenho controle sobre sua [Política de Segurança de Conteúdo
](https://infosec.mozilla.org/guidelines/web_security#content-security-policy).
No entanto, o tema em si foi desenvolvido com segurança em mente: não há estilos
inline e não utiliza JavaScript algum.

Se você quiser melhorar ainda mais sua pontuação no [Mozilla
Observatory](https://observatory.mozilla.org/), basta adicionar alguns cabeçalhos
à configuração do seu serviço de hospedagem (por exemplo,
[Netlify](https://docs.netlify.com/routing/headers/) ou [Cloudflare
Pages](https://developers.cloudflare.com/pages/platform/headers/)) e nunca mais
precisar pensar nisso. Meu arquivo `_headers`, por exemplo, se parece com este:

```
/*
  X-Content-Type-Options: nosniff
  Strict-Transport-Security: "max-age=31536000; includeSubDomains; preload" env=HTTPS
  Cache-Control: max-age=31536000, public
  X-Frame-Options: deny
  Referrer-Policy: no-referrer
  Feature-Policy: microphone 'none'; payment 'none'; geolocation 'none'; midi 'none'; sync-xhr 'none'; camera 'none'; magnetometer 'none'; gyroscope 'none'
  Content-Security-Policy: default-src 'none'; manifest-src 'self'; font-src 'self'; img-src 'self'; style-src 'self'; form-action 'none'; frame-ancestors 'none'; base-uri 'none'
  X-XSS-Protection: 1; mode=block
```

### Multilíngue

Se você precisa escrever um blog com suporte a mais de um idioma, o **Bear Cub**
tem tudo o que você precisa! Confira o arquivo [`hugo.toml`
](https://github.com/clente/hugo-bearcub/blob/main/exampleSite/hugo.toml) da demonstração
para um exemplo de como configurar o suporte multilíngue.

Por padrão, o tema cria um botão de tradução que fica desativado quando a
página atual está disponível apenas em outro idioma. Você também pode optar por
ocultar esse botão (em vez de desativá-lo) definindo `hideUntranslated =
true`.

### Mais

De vez em quando, enquanto uso o **Bear Cub**, percebo que alguma funcionalidade
está faltando. Atualmente, estas são as "funcionalidades avançadas" que já implementei:

- Feed RSS com texto completo: um template de feed RSS aprimorado que inclui o conteúdo
  completo (devidamente codificado) dos seus posts no próprio feed.
- Conteúdo estático: você pode criar entradas de blog vazias que funcionam como links para
  arquivos estáticos incluindo `link: "{url}"` no [front
  matter](https://gohugo.io/content-management/front-matter/) de um post. Você também pode
  adicionar `render: false` às suas [opções de build
  ](https://gohugo.io/content-management/build-options/#readout) para evitar renderizar posts em branco.
- Link de pular conteúdo: um link "pular para o conteúdo principal" temporariamente invisível, mas
  que pode ser focado por pessoas que precisam de teclado para navegar na web (veja o [PR
  #5](https://github.com/clente/hugo-bearcub/pull/5) de
  [@2kool4idkwhat](https://github.com/2kool4idkwhat) para mais informações).
- Responder por e-mail: se você fornecer um endereço de e-mail, o tema cria um botão "Responder
  a este post por e-mail" no final de cada post (veja a [implementação original
  ](https://kevquirk.com/adding-the-post-title-to-my-reply-by-email-button) de Kev Quirk).
  Este botão pode ser suprimido individualmente definindo `hideReply: true`
  no [front matter](https://gohugo.io/content-management/front-matter/) de um post
  (veja o [PR #18](https://github.com/clente/hugo-bearcub/pull/18) de
  [@chrsmutti](https://github.com/chrsmutti)).
- Shortcode `absfigure`: um atalho para usar o shortcode `figure` que também
  converte URLs relativas em absolutas usando a função `absURL`.
- CSS de uso único (EXPERIMENTAL): você pode adicionar estilos a uma única página
  escrevendo o CSS necessário em `assets/{custom_css}.css` e incluindo
  `style: "{custom_css}.css"` no [front
  matter](https://gohugo.io/content-management/front-matter/) da página.
- CSS condicional (EXPERIMENTAL): como o **Bear Cub** faz destaque de sintaxe
  sem estilos inline (veja `hugo.toml` para mais informações), ele carrega seu
  `syntax.css` somente se um bloco de código estiver presente na página atual.
- Estilo alternativo "Herman" (EXPERIMENTAL): se quiser experimentar um estilo CSS mais
  moderno, você pode alterar o parâmetro `themeStyle` para `"herman"` para
  ativar a versão de [Herman Martinus](https://herman.bearblog.dev/) do tema
  [Blogster Minimal](https://blogster-minimal.netlify.app/) para
  [Astro](https://astro.build/).
- Geração dinâmica de cartão social (EXPERIMENTAL): se você não adicionar imagens de
  prévia a um post, este template gerará uma baseada no título. Veja um exemplo abaixo.

![Exemplo de cartão social](https://raw.githubusercontent.com/clente/hugo-bearcub/main/images/social_card.webp)

## Configuração

O **Bear Cub** pode ser personalizado com um arquivo `hugo.toml`. Confira a
[configuração](https://github.com/clente/hugo-bearcub/blob/main/exampleSite/hugo.toml)
da [demonstração](https://clente.github.io/hugo-bearcub/) para mais informações.

```toml
# Configuração básica
baseURL = "https://example.com"
theme = "hugo-bearcub"
copyright = "John Doe (CC BY 4.0)"
defaultContentLanguage = "en"

# Gera um robots.txt para SEO
enableRobotsTXT = true

# Configura destaque de sintaxe sem estilos inline. Para mais informações sobre
# por que evitar estilos inline, veja
# https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/style-src#unsafe_inline_styles
[markup]
  [markup.highlight]
    lineNos = true
    lineNumbersInTable = false
    # Permite que o Bear Cub use uma variação do Dracula mais acessível
    # para pessoas com visão reduzida. Para mais informações sobre contraste de cores
    # e acessibilidade, veja https://web.dev/color-and-contrast-accessibility/
    noClasses = false

# Configuração do modo multilíngue. Para mais informações sobre como configurar tradução,
# veja https://gohugo.io/content-management/multilingual/
[languages]
  [languages.en]
    title = "Bear Cub"
    languageName = "en-US 🇺🇸"
    LanguageCode = "en-US"
    contentDir = "content"
    [languages.en.params]
      madeWith = "Made with [Bear Cub](https://github.com/clente/hugo-bearcub)"
  [languages.pt]
    title = "Bear Cub"
    languageName = "pt-BR 🇧🇷"
    LanguageCode = "pt-BR"
    contentDir = "content.pt"
    [languages.pt.params]
      madeWith = "Feito com [Bear Cub](https://github.com/clente/hugo-bearcub)"

[params]
  # A descrição do seu site
  description = "Bear Cub Demo"

  # O caminho para o seu favicon
  favicon = "images/favicon.png"

  # Essas imagens aparecem quando serviços geram uma prévia de um link
  # para o seu site. Ignorado se `generateSocialCard = true`. Para mais informações
  # sobre prévias, veja https://gohugo.io/templates/internal#twitter-cards e
  # https://gohugo.io/templates/internal#open-graph
  images = ["images/share.webp"]

  # Este título é usado como site_name no template interno de dados estruturados
  # opengraph do Hugo
  title = "Bear Cub"

  # As datas são exibidas no formato abaixo. Para mais informações sobre
  # formatação, veja https://gohugo.io/functions/format/
  dateFormat = "2006-01-02"

  # Se o seu blog for multilíngue mas você não tiver traduzido uma página, este tema
  # criará um link desativado. Definindo `hideUntranslated` como true, você pode
  # fazer o tema simplesmente não mostrar nenhum link
  hideUntranslated = false

  # (EXPERIMENTAL) Este tema tem duas opções de estilo CSS: "original" e
  # "herman". O primeiro é o que você vê na demonstração do Bear Cub (uma versão
  # otimizada do Hugo Bear Blog), enquanto o segundo tem uma aparência mais moderna baseada
  # na versão de Herman Martinus do tema Blogster Minimal para Astro.
  themeStyle = "original"

  # (EXPERIMENTAL) Este tema é capaz de gerar dinamicamente cartões sociais
  # para posts que não têm `images` definido no front matter; Definindo
  # `generateSocialCard` como false, você pode desativar esse comportamento. Para mais
  # informações, veja layouts/partials/social_card.html
  generateSocialCard = true

  # Redes sociais. Remova qualquer item que não esteja usando para garantir que não apareça
  # nos metadados do seu site.
  [params.social]
    twitter = "example" # Usuário do Twitter (sem '@')
    facebook_admin = "0000000000" # ID do Administrador da Página do Facebook

  # Metadados do autor. Usado principalmente para o feed RSS do site, mas o
  # e-mail também é adicionado ao rodapé de cada post. Você pode ocultar o link
  # "responder para" usando o parâmetro `hideReply` no front matter.
  [params.author]
    name = "John Doe" # Seu nome exibido nos metadados do feed RSS
    email = "me@example.com" # Adicionado ao rodapé para que leitores possam responder aos posts
```

## Contribuindo

Se você encontrar algum problema ao usar o **Bear Cub**, pode abrir uma
[issue](https://github.com/clente/hugo-bearcub/issues) ou criar um [pull
request](https://github.com/clente/hugo-bearcub/pulls).
