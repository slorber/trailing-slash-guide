# Trailing Slash Guide

Have trailing slash problems after deploying a static website in production?

This repo is for you, and aims to cover an exhaustive combination of static site generators and hosting providers.

**Common problems:**

- SEO/perf issues: when browsing `/myPath`, your host redirects to `/myPath/`
- 404 issues: relative link such as `<a href="otherPath">` are resolved differently (`/otherPath` or `/myPath/otherPath` depending on the presence/absence of a trailing slash
- UX issues: your host adds a trailing slash, and later the frontend router removes it, leading to a confusing experience and flickering url

**Causes:**

- static site generators can emit different files for the same path `/myPath`: `/myPath.html` or `/myPath/index.html`
- host providers can serve the same static files differently

## Static site generators


## Hosting providers

Let's deploy the same [static](/static) folder present in this repo to multiple hosting providers, and see how each file is served.

This folder is a representative sample of what a static website could look like:

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

**Deployment**: [trailing-slash-guide-default.netlify.app](trailing-slash-guide-default.netlify.app)

#### 
