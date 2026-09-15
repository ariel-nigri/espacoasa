# pri.vê — Landing page da Formação em Terapia do Esquema

Landing page estática (HTML/CSS puro, sem build, sem dependências de framework).

## Estrutura

```
index.html
assets/
  hero-photo.jpg
  icon-mark.png
  branch-green.png / branch-plum.png / branch-green-thin.png / branch-gold-thin.png
  sprig-green.png / sprig-plum.png / sprig-gold.png
  divider-ornament.png
  methodology-icons.png
```

Basta subir a pasta inteira (index.html + assets/) para qualquer hospedagem estática — Netlify, Vercel, GitHub Pages, ou o servidor próprio da pri.vê.

Única dependência externa: as fontes do Google Fonts (Cormorant Garamond + Montserrat), carregadas via `<link>` no `<head>`. Se precisar rodar 100% offline, é só baixar os arquivos de fonte e trocar o `<link>` por `@font-face` local.

## Pontos de integração

### 1. Login do aluno (seção `#login`)
O formulário atual é **só visual** — não autentica ninguém. Está em:

```html
<form class="login-card" onsubmit="return false;">
  <input type="email" id="email" ...>
  <input type="password" id="senha" ...>
  <button class="btn-enter" type="submit">Entrar</button>
```

Para integrar autenticação real:
- Trocar `onsubmit="return false;"` pela chamada real (fetch para API, redirect para sistema de login existente, etc.)
- Os campos já têm `id="email"` e `id="senha"` para facilitar
- Os links "Esqueci minha senha" e "Primeiro acesso" apontam para `#login` (âncora fake) — trocar pelos destinos reais

### 2. Aulas e datas (seção `#aulas`)
As três aulas já estruturadas têm data marcada como **"Data a confirmar"** (classe `.tl-date`). Substituir pelo texto da data real assim que definida. A seção foi pensada para crescer — dá pra copiar o bloco `.tl-item` para adicionar novos módulos.

### 3. Navegação
O menu do topo (`nav.mainnav`) usa âncoras internas (`#curso`, `#aulas`, `#facilitadoras`, `#login`) — já funcionam sem ajuste, contanto que os IDs das seções não sejam renomeados.

## Cores e tipografia (marca pri.vê)

```css
--sage:  #73826A
--plum:  #6B495B
--gold:  #B89A67
--bg:    #FDFCF8   /* fundo base, tom quase-branco da marca */
```

Tipografia: **Cormorant Garamond** (títulos/serifa) + **Montserrat** (corpo/sans).

## Responsivo
Breakpoints em `760px` (mobile) e `820px` (esconde o menu horizontal). Testado em viewport mobile (390px) e desktop (1280px).
