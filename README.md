# D.Lucca Dedetizadora e Desentupidora — site

Site one-page da D.Lucca (Florianópolis e região, SC). Objetivo: gerar cliques no WhatsApp e presença no Google.

HTML e CSS puros, sem build, sem dependências. Publicado com GitHub Pages.

## Estrutura

```
index.html              página única (textos, links, SEO, schema)
404.html                página de erro com botão de WhatsApp
assets/css/style.css    todo o visual (cores no topo, em :root)
assets/img/             fotos (WebP), logo, emblema, ícones, og-image
assets/fonts/           Sora e Inter (self-hosted, licença SIL OFL)
favicon.ico, favicon-32x32.png, apple-touch-icon.png, site.webmanifest
robots.txt, sitemap.xml
.nojekyll               faz o GitHub Pages servir os arquivos como estão
```

## Como editar

**Textos:** direto no `index.html`. Cada seção é uma `<section>` com comentário/`id` (`servicos`, `como-funciona`, `galeria`, `contato`). Mantenha um único `<h1>`.

**Número / mensagem do WhatsApp:** todos os botões usam
`https://wa.me/554896136561?text=...` (mensagem codificada em URL, ex.: espaço = `%20`, `á` = `%C3%A1`).
Para trocar o número, busque e substitua `554896136561` no `index.html` e no `404.html`, e o telefone exibido `(48) 9613-6561` no rodapé e no schema (`"telephone"`).

**Instagram:** no rodapé, procure `data-todo="[INSTAGRAM]"` e troque o `href` pelo perfil (ex.: `https://www.instagram.com/dlucca.dedetizadora/`). Depois, adicione o mesmo link no schema JSON-LD do `<head>`:
`"sameAs": ["https://www.instagram.com/..."]`.

**Depoimentos:** procure `[Depoimentos reais do Google serão inseridos aqui]` e substitua por depoimentos reais (nunca inventados).

**Fotos:** coloque a nova foto em `assets/img/` (WebP, até ~1000px no lado maior, qualidade ~72) e troque o `src`, `width`, `height` e o `alt` descritivo no `index.html`. Exemplo de conversão:
`cwebp -q 72 -resize 0 1000 foto.jpg -o assets/img/nova-foto.webp`

**Cores:** variáveis no topo de `assets/css/style.css` (`--purple`, `--lilac`, `--wa`...). O verde `--wa` é exclusivo dos botões de WhatsApp.

## Domínio próprio (quando houver)

1. Crie o arquivo `CNAME` na raiz com o domínio (ex.: `dlucca.com.br`).
2. No DNS do domínio, aponte conforme a documentação do GitHub Pages (registros A para os IPs do GitHub e `www` como CNAME para `<usuario>.github.io`).
3. Em **Settings → Pages**, informe o domínio e marque **Enforce HTTPS**.
4. Substitua a URL antiga pela nova em: `index.html` (canonical, og:url, og:image, JSON-LD), `404.html`, `robots.txt` e `sitemap.xml`.
5. Cadastre o domínio no Google Search Console e envie o `sitemap.xml`. Crie/atualize o Perfil da Empresa no Google com o link do site.

## Checklist antes de divulgar

- [ ] Testar um botão de WhatsApp no celular (o número abre a conversa certa?)
- [ ] Link do Instagram
- [ ] Depoimentos reais (ou remover o bloco placeholder)
- [ ] Domínio próprio + Search Console
