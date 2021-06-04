# Trailing Slash Guide

Have trailing slash problems after deploying a static website in production?

This repo is for you, and aims to cover an exhaustive combination of static site generators and hosting providers.

**Help wanted**: please help complete the data, making it exhaustive, factual and up-to-date.

**Common problems**:

- SEO/perf issues: when browsing `/myPath`, your host redirects to `/myPath/`
- 404 issues: relative link such as `<a href="otherPath">` are resolved differently (`/otherPath` or `/myPath/otherPath` depending on the presence/absence of a trailing slash
- UX issues: your host adds a trailing slash, and later your single-page-application frontend router removes it, leading to a confusing experience and flickering url

**Causes**:

- static site generators can emit different files for the same path `/myPath`: `/myPath.html` or `/myPath/index.html` (the later can lead to an additional trailing slash)
- host providers can serve the same static files differently

## Static site generators

Let's figure out how different static site generators output static files.

### Gatsby

- Gatsby outputs `/myPath/index.html` for `/myPath`: it can lead host providers to add a trailing slash
- Gatsby's SPA router (Reach-Router) can route both `/myPath` and `/myPath/` after React hydration

### Next.js

- Next.js outputs by default `/myPath.html` for `/myPath`. This output generally works fine and host providers do not add any extra trailing slash.
- Next.js has a [{trailingSlash: true}](https://nextjs.org/docs/api-reference/next.config.js/trailing-slash) config setting to output `/myPath/index.html`.

### Docusaurus

- Docusaurus outputs `/myPath/index.html` for `/myPath`: it can lead host providers to add a trailing slash
- Docusaurus's SPA router (React-Router) can route both `/myPath` and `/myPath/` after React hydration

### TODO

TODO Add comments for all other static site generators

## Hosting providers

Let's deploy the same [static](/static) folder to multiple hosting providers, and see how each file is served.

This folder is a representative sample of the output of static site generators

```sh 
static
│
├── file.html
│
├── folder
│   └── index.html
│
├── both.html
└── both
    └── index.html
```

Let's see the behavior of each host provider for the following urls:

- `/file`
- `/file/`
- `/folder`
- `/folder/`
- `/both`
- `/both/`

### Netlify

Netlify has a setting `Post Processing > Asset Optimization > Pretty Urls` that affects the way a static site is served. Disabling the `Pretty Urls` setting can help prevent Netlify to add an unwanted trailing slash.

#### Default settings (`Disable asset optimization` checked)

**Important**: the global checkbox `Disable asset optimization` is confusing and does not really disable the `Pretty Urls` settings in practice: make sure to uncheck all the `Asset optimization` independently.

**Deployment**: [trailing-slash-guide-default.netlify.app](https://trailing-slash-guide-default.netlify.app)

| Url      | Redirect Url |
| -------- | ------------ |
| /file    | ✅            |
| /file/   | ➡️ /file     |
| /folder  | ➡️ /folder/  |
| /folder/ | ✅            |
| /both    | ✅            |
| /both/   | ➡️ /both     |

#### Pretty Urls enabled

**Deployment**: [trailing-slash-guide-pretty-url-enabled.netlify.app](https://trailing-slash-guide-pretty-url-enabled.netlify.app)

| Url      | Redirect Url |
| -------- | ------------ |
| /file    | ✅            |
| /file/   | ➡️ /file     |
| /folder  | ➡️ /folder/  |
| /folder/ | ✅            |
| /both    | ✅            |
| /both/   | ➡️ /both     |

#### Pretty Urls disabled

**Important**: make sure the `Pretty Urls` checkbox is **really** unchecked (ie, don't use the broken `Disable asset optimization` global checkbox)

**Deployment**: [trailing-slash-guide-pretty-url-disabled.netlify.app](https://trailing-slash-guide-pretty-url-disabled.netlify.app)

| Url      | Redirect Url |
| -------- | ------------ |
| /file    | ✅            |
| /file/   | ✅            |
| /folder  | ✅            |
| /folder/ | ✅            |
| /both    | ✅            |
| /both/   | ✅            |

### Vercel

**Deployment**: [trailing-slash-guide.vercel.app](https://trailing-slash-guide.vercel.app)

| Url      | Redirect Url |
| -------- | ------------ |
| /file    | ✅            |
| /file/   | ✅            |
| /folder  | ✅            |
| /folder/ | ✅            |
| /both    | ✅            |
| /both/   | ✅            |
