# Astro Template

![Astro](https://img.shields.io/badge/Astro-7.x-BC52EE?logo=astro&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-6.x-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.x-06B6D4?logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-22C55E)

Template de landing page em **Astro** com **TypeScript**, **Tailwind CSS v4** e **SEO centralizado**. Todos os dados institucionais, de contato e de localização ficam em um único arquivo (`src/data/site.ts`), que alimenta automaticamente as meta tags, o Open Graph e o JSON-LD (Schema.org) do site.

Ideal para quem quer sair do zero com uma base limpa, tipada, performática e pronta para ranquear — sem repetir configuração de SEO em cada página.

---

## Recursos principais

- **SEO a partir de uma única fonte de verdade** — nome, descrição, contatos, endereço e redes sociais vivem em `src/data/site.ts`.
- **Open Graph completo** — `og:title`, `og:description`, `og:image`, `og:url`, `og:locale`, `og:site_name` e `og:image:alt` gerados automaticamente.
- **Canonical e URLs absolutas** — resolvidas com `Astro.site`, evitando links relativos em compartilhamentos.
- **Schema.org (JSON-LD)** — marcação `LocalBusiness` com endereço, telefone, e-mail, áreas atendidas e `sameAs`.
- **Geo SEO** — meta `geo.region` e `geo.placename` derivadas da primeira cidade atendida e do estado.
- **Controle de indexação** — prop `noindex` (já aplicada na página 404).
- **Componentes reutilizáveis** — Header, Footer, SEO/SchemaOrg e uma coleção de componentes de interface (`src/components/gs/`).
- **Tailwind CSS v4** integrado via plugin Vite, com tema e fontes definidos em `src/styles/global.css`.
- **Fontes self-hosted** — Inter e Poppins via `@fontsource` (sem requisições a terceiros).
- **View Transitions** — navegação com `ClientRouter` habilitado no layout base.
- **Sitemap automático** via `@astrojs/sitemap`.
- **Tipagem estrita** — `astro/tsconfigs/strict` e alias `@/*` para `src/*`.
- **Zero JavaScript de framework** — apenas Astro, com ilhas de script quando necessário.

---

## Stack

| Camada | Tecnologia |
| :-- | :-- |
| Framework | [Astro](https://astro.build) 7 |
| Linguagem | TypeScript 6 (strict) |
| Estilos | Tailwind CSS 4 (`@tailwindcss/vite`) |
| Tipografia | `@fontsource/inter` e `@fontsource/poppins` |
| Ícones | `@lucide/astro` |
| SEO | Componentes próprios + `@astrojs/sitemap` |
| Runtime | Node.js `>=22.22.0` |

---

## Estrutura do projeto

```text
.
├── astro.config.mjs          # Integrações (sitemap), Tailwind, `site` e Vite
├── package.json
├── tsconfig.json             # Strict + alias `@/*` → `src/*`
├── src/
│   ├── components/
│   │   ├── Header.astro      # Cabeçalho global
│   │   ├── Footer.astro      # Rodapé global
│   │   ├── seo/
│   │   │   ├── SEO.astro     # Meta tags, Open Graph, canonical e geo
│   │   │   └── SchemaOrg.astro# JSON-LD LocalBusiness
│   │   └── gs/               # Componentes de interface reutilizáveis
│   │       ├── Bubbles.astro
│   │       ├── Fab.astro
│   │       ├── FabMenu.astro
│   │       ├── GlowBg.astro
│   │       ├── Reels.astro
│   │       ├── Reveal.astro
│   │       ├── Terminal.astro
│   │       └── WordLoader.astro
│   ├── data/
│   │   └── site.ts           # ⭐ Configuração central do site e SEO
│   ├── layouts/
│   │   └── Base.astro        # <html>, SEO, Header, Footer e slot
│   ├── pages/
│   │   ├── index.astro       # Rota `/`
│   │   └── 404.astro         # Rota `/404` (noindex)
│   └── styles/
│       └── global.css        # Tailwind, fontes e tokens do tema
└── public/                   # Assets estáticos (favicon, og-image, etc.)
```

> Rotas são criadas a partir de `src/pages/`. Cada arquivo `.astro` vira uma URL correspondente ao seu caminho.

### Componentes de interface (`src/components/gs/`)

| Componente | Descrição |
| :-- | :-- |
| `Header.astro` / `Footer.astro` | Estrutura global já plugada no `Base.astro` (prontos para receber seu conteúdo). |
| `Fab.astro` | Botões flutuantes de contato (WhatsApp, e-mail, telefone) no canto da tela. |
| `FabMenu.astro` | Menu flutuante expansível com rótulos acessíveis e suporte a ícones do Astro. |
| `Reels.astro` | Player de vídeos verticais estilo Reels, com navegação por `data-goto`. |
| `Reveal.astro` | Animação de fade/slide ao entrar no viewport usando um único `IntersectionObserver`. |
| `Terminal.astro` | Simulador de terminal com digitação animada e saída de comandos. |
| `WordLoader.astro` | Alternância animada de palavras (efeito de texto rotativo). |
| `GlowBg.astro` | Fundo decorativo com esferas de luz animadas (aurora orbs). |
| `Bubbles.astro` | Bolhas decorativas de fundo, somente CSS. |

A documentação de uso de cada componente está em [`src/components/gs/.README.md`](./src/components/gs/.README.md).

---

## Quick start

### 1. Use este template

```bash
# Clone o repositório
git clone https://github.com/Ogustavone/astro-template.git meu-projeto
cd meu-projeto

# Remova o histórico do template (opcional)
rm -rf .git && git init
```

Alternativamente, use o botão **Use this template** no GitHub.

### 2. Instale as dependências

O projeto usa **npm** (há um `package-lock.json`), mas funciona com qualquer gerenciador:

```bash
npm install
# ou
pnpm install
# ou
bun install
```

> Requer **Node.js 22.22.0 ou superior**.

### 3. Suba o servidor de desenvolvimento

```bash
npm run dev
```

A aplicação estará disponível em `http://localhost:4321` (o script já expõe o host em `0.0.0.0`).

### 4. Configure o seu site

Edite **`src/data/site.ts`** — é o único lugar que você precisa tocar para atualizar identidade, contato, dados legais e SEO:

```ts
// src/data/site.ts
export const site = {
  info: {
    name: "GS",
    fullName: "GS Soluções Digitais Ltda",
    slogan: "Inovação sob medida para o seu negócio",
    description: "Desenvolvimento de softwares sob medida e consultoria em tecnologia.",
    url: "https://www.gs.com",
  },

  contact: {
    phone: "+5555988887777",
    phoneDisplay: "(55) 98888-7777",
    email: "gs@gmail.com",
  },

  data: {
    cnpj: "12345678000199",
    cnpjDisplay: "12.345.678/0001-99",
    legalName: "GS Soluções Digitais Ltda",
    addressLocality: "Santa Maria",
    addressRegion: "RS",
    areaServed: "Santa Maria, Rio Grande do Sul",
  },

  cities: [
    { name: "Santa Maria", description: "Atendimento completo para toda a região central." },
  ],

  socials: {
    username: "@gs",
    instagram: "https://www.instagram.com/gs/",
    github: "https://github.com/gs",
    linkedin: "https://www.linkedin.com/company/gs/",
  },
} as const;
```

Em seguida, ajuste a URL de produção no `astro.config.mjs`:

```js
// astro.config.mjs
export default defineConfig({
  site: "https://seu-dominio.com", // usado para canonical, OG e sitemap
  // ...
});
```

Por fim, adicione os assets referenciados pelo SEO em `public/`:

```text
public/
├── favicon.svg
└── og-image.png   # 1200×630 recomendado
```

### 5. Comandos disponíveis

| Comando | Ação |
| :-- | :-- |
| `npm run dev` | Inicia o servidor de desenvolvimento em `localhost:4321` (host `0.0.0.0`). |
| `npm run build` | Executa `astro check` e gera o build de produção em `./dist/`. |
| `npm run check` | Roda a verificação de tipos e diagnóstico do Astro. |
| `npm run preview` | Serve o build de produção localmente. |

---

## Configuração de SEO

O fluxo é simples: **`site.ts` → `SEO.astro` → `Base.astro` → página**.

```
src/data/site.ts
      │
      ├──► SEO.astro ──────► <title>, description, canonical, OG, geo
      │        └──► SchemaOrg.astro ──► JSON-LD LocalBusiness
      │
      └──► Base.astro ─────► <head> + Header + slot + Footer
```

### Como usar o layout

`Base.astro` aceita `title`, `description`, `image` e `noindex`. O restante do SEO é herdado da configuração central:

```astro
---
import Base from "@/layouts/Base.astro";
import { site } from "@/data/site";
---

<Base
  title={`Serviços | ${site.info.name}`}
  description="Conheça nossas soluções de software sob medida."
  image="/og/servicos.png"
>
  <main>
    <h1>Nossos serviços</h1>
  </main>
</Base>
```

### O que é gerado automaticamente

| Recurso | Origem |
| :-- | :-- |
| `<title>` e `<meta name="description">` | Props do layout, com fallback para `site.info` |
| `<link rel="canonical">` | `Astro.url.pathname` resolvido contra `Astro.site` |
| Open Graph (`og:*`) | Título, descrição, imagem e `site.info.name` |
| `geo.region` / `geo.placename` | `site.data.addressRegion` e primeira cidade de `site.cities` |
| JSON-LD `LocalBusiness` | `site.info`, `site.contact`, `site.data`, `site.cities` e `site.socials` |
| `robots: noindex, nofollow` | Quando `noindex={true}` (padrão na 404) |
| `sitemap-index.xml` | `@astrojs/sitemap`, com base em `site` do `astro.config.mjs` |

### Imagem de compartilhamento

O padrão é `/og-image.png`. Para social cards por página, basta informar a prop `image`:

```astro
<Base title="Contato" description="Fale com a gente." image="/og/contato.png">
```

> Use imagens absolutas a partir de `public/` e prefira a proporção **1200×630**.

---

## Deploy

O build é totalmente estático e pode ser publicado em qualquer host (Vercel, Netlify, Cloudflare Pages, GitHub Pages, etc.). Configure o comando `npm run build` e o diretório de saída `dist/`.

Antes de publicar, revise:

- `site` em `astro.config.mjs` apontando para o domínio final;
- `src/data/site.ts` com dados reais de contato e endereço;
- `public/favicon.svg` e `public/og-image.png` presentes;
- `vite.server.allowedHosts` em `astro.config.mjs` (há um `TODO` para remover em produção).

---

## Licença

Distribuído sob a licença **MIT**. Você pode usar, modificar e redistribuir este template livremente, mantendo o aviso de copyright.
