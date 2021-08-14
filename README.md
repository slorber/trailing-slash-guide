# Trailing Slash Guide

Have trailing slash problems after deploying a static website in production?

This repo explains factually the behavior of:
- [Static Site generators](docs/Static-Site-Generators.md) 
- [Hosting Providers](docs/Hosting-Providers.md)
- [Self-hosted HTTP servers](docs/Self-Host.md)

We also suggest some [possible solutions](docs/Solutions.md)

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

| Host                  | Settings                                | Url                                                                       | /file                                                                            | /file/                                                                            | /file.html                                                                         | /folder                                                                            | /folder/                                                                            | /folder/index.html                                                                           | /both                                                                          | /both/                                                                          | /both.html                                                                         | /both/index.html                                                                         |
| --------------------- | --------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| GitHub Pages          |                                         | [link](https://slorber.github.io/trailing-slash-guide)                    | [✅](https://slorber.github.io/trailing-slash-guide/file)                         | [💢 404](https://slorber.github.io/trailing-slash-guide/file/)                    | [✅](https://slorber.github.io/trailing-slash-guide/file.html)                      | [➡️ /folder/](https://slorber.github.io/trailing-slash-guide/folder)               | [✅](https://slorber.github.io/trailing-slash-guide/folder/)                         | [✅](https://slorber.github.io/trailing-slash-guide/folder/index.html)                        | [✅](https://slorber.github.io/trailing-slash-guide/both)                       | [✅](https://slorber.github.io/trailing-slash-guide/both/)                       | [✅](https://slorber.github.io/trailing-slash-guide/both.html)                      | [✅](https://slorber.github.io/trailing-slash-guide/both/index.html)                      |
| Netlify               | Default                                 | [link](https://trailing-slash-guide-default.netlify.app)                  | [✅](https://trailing-slash-guide-default.netlify.app/file)                       | [➡️ /file](https://trailing-slash-guide-default.netlify.app/file/)                | [✅](https://trailing-slash-guide-default.netlify.app/file.html)                    | [➡️ /folder/](https://trailing-slash-guide-default.netlify.app/folder)             | [✅](https://trailing-slash-guide-default.netlify.app/folder/)                       | [✅](https://trailing-slash-guide-default.netlify.app/folder/index.html)                      | [✅](https://trailing-slash-guide-default.netlify.app/both)                     | [➡️ /both](https://trailing-slash-guide-default.netlify.app/both/)              | [✅](https://trailing-slash-guide-default.netlify.app/both.html)                    | [✅](https://trailing-slash-guide-default.netlify.app/both/index.html)                    |
| Netlify               | Pretty Urls on                          | [link](https://trailing-slash-guide-pretty-url-enabled.netlify.app)       | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file)            | [➡️ /file](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file/)     | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file.html)         | [➡️ /folder/](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder)  | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder/)            | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder/index.html)           | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both)          | [➡️ /both](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both/)   | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both.html)         | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both/index.html)         |
| Netlify               | Pretty Urls off                         | [link](https://trailing-slash-guide-pretty-url-disabled.netlify.app)      | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file/)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file.html)        | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder/)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder/index.html)          | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both)         | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both/)         | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both.html)        | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both/index.html)        |
| Vercel                | Default                                 | [link](https://vercel-default-eight.vercel.app)                           | [💢 404](https://vercel-default-eight.vercel.app/file)                           | [💢 404](https://vercel-default-eight.vercel.app/file/)                           | [✅](https://vercel-default-eight.vercel.app/file.html)                             | [✅](https://vercel-default-eight.vercel.app/folder)                                | [✅](https://vercel-default-eight.vercel.app/folder/)                                | [✅](https://vercel-default-eight.vercel.app/folder/index.html)                               | [✅](https://vercel-default-eight.vercel.app/both)                              | [✅](https://vercel-default-eight.vercel.app/both/)                              | [✅](https://vercel-default-eight.vercel.app/both.html)                             | [✅](https://vercel-default-eight.vercel.app/both/index.html)                             |
| Vercel                | cleanUrls=false trailingSlash=undefined | [link](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app) | [💢 404](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file) | [💢 404](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file/) | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file.html)   | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder)      | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder/)      | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder/index.html)     | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both)    | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both/)    | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both.html)   | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both/index.html)   |
| Vercel                | cleanUrls=false trailingSlash=false     | [link](https://vercel-cleanurls-false-trailingslash-false.vercel.app)     | [💢 404](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file)     | [💢 404](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file/)     | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file.html)       | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder)          | [➡️ /folder](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder/) | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder/index.html)         | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both)        | [➡️ /both](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both/) | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both.html)       | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both/index.html)       |
| Vercel                | cleanUrls=false trailingSlash=true      | [link](https://vercel-cleanurls-false-trailingslash-true.vercel.app)      | [💢 404](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file)      | [💢 404](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file/)      | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file.html)        | [➡️ /folder/](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder) | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder/)           | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder/index.html)          | [➡️ /both/](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both) | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both/)         | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both.html)        | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both/index.html)        |
| Vercel                | cleanUrls=true trailingSlash=undefined  | [link](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app)  | [💢 404](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file)  | [💢 404](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file/)  | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file.html)    | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder)       | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder/)       | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder/index.html)      | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both)     | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both/)     | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both.html)    | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both/index.html)    |
| Vercel                | cleanUrls=true trailingSlash=false      | [link](https://vercel-cleanurls-true-trailingslash-false.vercel.app)      | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file)           | [➡️ /file](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file/)    | [➡️ /file](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file.html) | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder)           | [➡️ /folder](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder/)  | [➡️ /folder](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder/index.html) | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both)         | [➡️ /both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both/)  | [➡️ /both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both.html) | [➡️ /both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both/index.html) |
| Vercel                | cleanUrls=true trailingSlash=true       | [link](https://vercel-cleanurls-true-trailingslash-true.vercel.app)       | [➡️ /file/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file)    | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file/)            | [➡️ /file/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file.html) | [➡️ /folder/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder)  | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder/)            | [➡️ /folder/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder/index.html) | [➡️ /both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both)  | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both/)          | [➡️ /both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both.html) | [➡️ /both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both/index.html) |
| Cloudflare Pages      |                                         | [link](https://trailing-slash-guide.pages.dev)                            | [✅](https://trailing-slash-guide.pages.dev/file)                                 | [➡️ /file](https://trailing-slash-guide.pages.dev/file/)                          | [➡️ /file](https://trailing-slash-guide.pages.dev/file.html)                       | [➡️ /folder/](https://trailing-slash-guide.pages.dev/folder)                       | [✅](https://trailing-slash-guide.pages.dev/folder/)                                 | [➡️ /folder/](https://trailing-slash-guide.pages.dev/folder/index.html)                      | [✅](https://trailing-slash-guide.pages.dev/both)                               | [✅](https://trailing-slash-guide.pages.dev/both/)                               | [➡️ /both](https://trailing-slash-guide.pages.dev/both.html)                       | [➡️ /both/](https://trailing-slash-guide.pages.dev/both/index.html)                      |
| Render                |                                         | [link](https://trailing-slash-guide.onrender.com)                         | [✅](https://trailing-slash-guide.onrender.com/file)                              | [✅](https://trailing-slash-guide.onrender.com/file/)                              | [✅](https://trailing-slash-guide.onrender.com/file.html)                           | [✅](https://trailing-slash-guide.onrender.com/folder)                              | [✅](https://trailing-slash-guide.onrender.com/folder/)                              | [✅](https://trailing-slash-guide.onrender.com/folder/index.html)                             | [✅](https://trailing-slash-guide.onrender.com/both)                            | [✅](https://trailing-slash-guide.onrender.com/both/)                            | [✅](https://trailing-slash-guide.onrender.com/both.html)                           | [✅](https://trailing-slash-guide.onrender.com/both/index.html)                           |
| Azure Static Web Apps |                                         | [link](https://polite-bay-08a23e210.azurestaticapps.net)                  | [✅](https://polite-bay-08a23e210.azurestaticapps.net/file)                       | [💢 404](https://polite-bay-08a23e210.azurestaticapps.net/file/)                  | [✅](https://polite-bay-08a23e210.azurestaticapps.net/file.html)                    | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder)                       | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder/)                       | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder/index.html)                      | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both)                     | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both/)                     | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both.html)                    | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both/index.html)                    |

## Help Wanted

Let's keep this resource up-to-date, and make it exhaustive together.