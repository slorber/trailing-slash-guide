# Trailing Slash Guide

Have trailing slash problems after deploying a static website in production?

This repo explains factually the behavior of:
- [Static Site generators](docs/Static-Site-Generators.md) 
- [Hosting Providers](docs/Hosting-Providers.md)

We also suggest some [possible solutions](docs/Solutios.md)

## Intro

Let's get more familiar with trailing slash issues.

**Common problems**:

- SEO/perf issues: when browsing `/myPath`, your host redirects to `/myPath/`
- 404 issues: relative link such as `<a href="otherPath">` are resolved differently (`/otherPath` or `/myPath/otherPath` depending on the presence/absence of a trailing slash
- UX issues: your host adds a trailing slash, and later your single-page-application frontend router removes it, leading to a confusing experience and flickering url

**Causes**:

- static site generators can emit different files for the same path `/myPath`: `/myPath.html` or `/myPath/index.html` (the later can lead to an additional trailing slash)
- host providers all have a different behavior when serving static files, there is no standard

## Summary

Considering this [static site](static):

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

Behavior of various static hosting providers:

| Host                  | Settings        | Url                                                                  | /file  | /file/   | /file.html | /folder                          | /folder/ | /folder/index.html | /both  | /both/   | /both.html | /both/index.html |
| --------------------- | --------------- | -------------------------------------------------------------------- | ------ | -------- | ---------- | -------------------------------- | -------- | ------------------ | ------ | -------- | ---------- | ---------------- |
| GitHub Pages          |                 | [link](https://slorber.github.io/trailing-slash-guide)               | ✅      | 💢 404   | ✅          | ➡️ /folder/ | ✅        | ✅                  | ✅      | ✅        | ✅          | ✅                |
| Netlify               | Default         | [link](https://trailing-slash-guide-default.netlify.app)             | ✅      | ➡️ /file | ✅          | ➡️ /folder/                      | ✅        | ✅                  | ✅      | ➡️ /both | ✅          | ✅                |
| Netlify               | Pretty Urls on  | [link](https://trailing-slash-guide-pretty-url-enabled.netlify.app)  | ✅      | ➡️ /file | ✅          | ➡️ /folder/                      | ✅        | ✅                  | ✅      | ➡️ /both | ✅          | ✅                |
| Netlify               | Pretty Urls off | [link](https://trailing-slash-guide-pretty-url-disabled.netlify.app) | ✅      | ✅        | ✅          | ✅                                | ✅        | ✅                  | ✅      | ✅        | ✅          | ✅                |
| Vercel                |                 | [link](https://trailing-slash-guide.vercel.app)                      | 💢 404 | 💢 404   | ✅          | ✅                                | ✅        | ✅                  | ✅      | ✅        | ✅          | ✅                |
| Cloudflare Pages      |                 | [link](https://trailing-slash-guide.pages.dev)                       | ✅      | ➡️ /file | ➡️ /file   | ➡️ /folder/                      | ✅        | ➡️ /folder/        | ✅      | ✅        | ➡️ /both   | ➡️ /both/        |
| Render                |                 | [link](https://trailing-slash-guide.onrender.com)                    | ✅ | ✅   | ✅     | ✅                           | ✅   | ✅             | ✅ | ✅   | ✅     | ✅           |
| Azure Static Web Apps |                 | [link](https://polite-bay-08a23e210.azurestaticapps.net/)            | ✅      | 💢 404   | ✅          | ✅                                | ✅        | ✅                  | ✅      | ✅        | ✅          | ✅                |

## Help Wanted

Let's keep this resource up-to-date, and make it exhaustive together.
