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

