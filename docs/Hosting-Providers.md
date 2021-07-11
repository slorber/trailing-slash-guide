
# Hosting providers

Let's deploy the same [static](../static) folder to multiple hosting providers, and see how requests are served.

## Summary

| Host                  | Settings                                | Url                                                                       | /file                                                                            | /file/                                                                            | /file.html                                                                        | /folder                                                                           | /folder/                                                                           | /folder/index.html                                                                          | /both                                                                         | /both/                                                                         | /both.html                                                                        | /both/index.html                                                                        |
| --------------------- | --------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| GitHub Pages          |                                         | [link](https://slorber.github.io/trailing-slash-guide)                    | [✅](https://slorber.github.io/trailing-slash-guide/file)                         | [💢 404](https://slorber.github.io/trailing-slash-guide/file/)                    | [✅](https://slorber.github.io/trailing-slash-guide/file.html)                     | [➡️ /folder/](https://slorber.github.io/trailing-slash-guide/folder)              | [✅](https://slorber.github.io/trailing-slash-guide/folder/)                        | [✅](https://slorber.github.io/trailing-slash-guide/folder/index.html)                       | [✅](https://slorber.github.io/trailing-slash-guide/both)                      | [✅](https://slorber.github.io/trailing-slash-guide/both/)                      | [✅](https://slorber.github.io/trailing-slash-guide/both.html)                     | [✅](https://slorber.github.io/trailing-slash-guide/both/index.html)                     |
| Netlify               | Default                                 | [link](https://trailing-slash-guide-default.netlify.app)                  | [✅](https://trailing-slash-guide-default.netlify.app/file)                       | [➡️ file](https://trailing-slash-guide-default.netlify.app/file/)                 | [✅](https://trailing-slash-guide-default.netlify.app/file.html)                   | [➡️ folder/](https://trailing-slash-guide-default.netlify.app/folder)             | [✅](https://trailing-slash-guide-default.netlify.app/folder/)                      | [✅](https://trailing-slash-guide-default.netlify.app/folder/index.html)                     | [✅](https://trailing-slash-guide-default.netlify.app/both)                    | [➡️ both](https://trailing-slash-guide-default.netlify.app/both/)              | [✅](https://trailing-slash-guide-default.netlify.app/both.html)                   | [✅](https://trailing-slash-guide-default.netlify.app/both/index.html)                   |
| Netlify               | Pretty Urls on                          | [link](https://trailing-slash-guide-pretty-url-enabled.netlify.app)       | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file)            | [➡️ file](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file/)      | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/file.html)        | [➡️ folder/](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder)  | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder/)           | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/folder/index.html)          | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both)         | [➡️ both](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both/)   | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both.html)        | [✅](https://trailing-slash-guide-pretty-url-enabled.netlify.app/both/index.html)        |
| Netlify               | Pretty Urls off                         | [link](https://trailing-slash-guide-pretty-url-disabled.netlify.app)      | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file/)           | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/file.html)       | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder)          | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder/)          | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/folder/index.html)         | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both)        | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both/)        | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both.html)       | [✅](https://trailing-slash-guide-pretty-url-disabled.netlify.app/both/index.html)       |
| Vercel                | Default                                 | [link](https://vercel-default-eight.vercel.app)                           | [💢 404](https://vercel-default-eight.vercel.app/file)                           | [💢 404](https://vercel-default-eight.vercel.app/file/)                           | [✅](https://vercel-default-eight.vercel.app/file.html)                            | [✅](https://vercel-default-eight.vercel.app/folder)                               | [✅](https://vercel-default-eight.vercel.app/folder/)                               | [✅](https://vercel-default-eight.vercel.app/folder/index.html)                              | [✅](https://vercel-default-eight.vercel.app/both)                             | [✅](https://vercel-default-eight.vercel.app/both/)                             | [✅](https://vercel-default-eight.vercel.app/both.html)                            | [✅](https://vercel-default-eight.vercel.app/both/index.html)                            |
| Vercel                | cleanUrls=false trailingSlash=undefined | [link](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app) | [💢 404](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file) | [💢 404](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file/) | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/file.html)  | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder)     | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder/)     | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/folder/index.html)    | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both)   | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both/)   | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both.html)  | [✅](https://vercel-cleanurls-false-trailingslash-undefined.vercel.app/both/index.html)  |
| Vercel                | cleanUrls=false trailingSlash=false     | [link](https://vercel-cleanurls-false-trailingslash-false.vercel.app)     | [💢 404](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file)     | [💢 404](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file/)     | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/file.html)      | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder)         | [➡️ folder](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder/) | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/folder/index.html)        | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both)       | [➡️ both](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both/) | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both.html)      | [✅](https://vercel-cleanurls-false-trailingslash-false.vercel.app/both/index.html)      |
| Vercel                | cleanUrls=false trailingSlash=true      | [link](https://vercel-cleanurls-false-trailingslash-true.vercel.app)      | [💢 404](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file)      | [💢 404](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file/)      | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/file.html)       | [➡️ folder/](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder) | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder/)          | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/folder/index.html)         | [➡️ both/](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both) | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both/)        | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both.html)       | [✅](https://vercel-cleanurls-false-trailingslash-true.vercel.app/both/index.html)       |
| Vercel                | cleanUrls=true trailingSlash=undefined  | [link](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app)  | [💢 404](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file)  | [💢 404](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file/)  | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/file.html)   | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder)      | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder/)      | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/folder/index.html)     | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both)    | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both/)    | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both.html)   | [✅](https://vercel-cleanurls-true-trailingslash-undefined.vercel.app/both/index.html)   |
| Vercel                | cleanUrls=true trailingSlash=false      | [link](https://vercel-cleanurls-true-trailingslash-false.vercel.app)      | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file)           | [➡️ file](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file/)     | [➡️ file](https://vercel-cleanurls-true-trailingslash-false.vercel.app/file.html) | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder)          | [➡️ folder](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder/)  | [➡️ folder](https://vercel-cleanurls-true-trailingslash-false.vercel.app/folder/index.html) | [✅](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both)        | [➡️ both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both/)  | [➡️ both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both.html) | [➡️ both](https://vercel-cleanurls-true-trailingslash-false.vercel.app/both/index.html) |
| Vercel                | cleanUrls=true trailingSlash=true       | [link](https://vercel-cleanurls-true-trailingslash-true.vercel.app)       | [➡️ file/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file)     | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file/)            | [➡️ file/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/file.html) | [➡️ folder/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder)  | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder/)           | [➡️ folder/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/folder/index.html) | [➡️ both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both)  | [✅](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both/)         | [➡️ both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both.html) | [➡️ both/](https://vercel-cleanurls-true-trailingslash-true.vercel.app/both/index.html) |
| Cloudflare Pages      |                                         | [link](https://trailing-slash-guide.pages.dev)                            | [✅](https://trailing-slash-guide.pages.dev/file)                                 | [➡️ file](https://trailing-slash-guide.pages.dev/file/)                           | [➡️ file](https://trailing-slash-guide.pages.dev/file.html)                       | [➡️ folder/](https://trailing-slash-guide.pages.dev/folder)                       | [✅](https://trailing-slash-guide.pages.dev/folder/)                                | [➡️ folder/](https://trailing-slash-guide.pages.dev/folder/index.html)                      | [✅](https://trailing-slash-guide.pages.dev/both)                              | [✅](https://trailing-slash-guide.pages.dev/both/)                              | [➡️ both](https://trailing-slash-guide.pages.dev/both.html)                       | [➡️ both/](https://trailing-slash-guide.pages.dev/both/index.html)                      |
| Render                |                                         | [link](https://trailing-slash-guide.onrender.com)                         | [✅](https://trailing-slash-guide.onrender.com/file)                              | [✅](https://trailing-slash-guide.onrender.com/file/)                              | [✅](https://trailing-slash-guide.onrender.com/file.html)                          | [✅](https://trailing-slash-guide.onrender.com/folder)                             | [✅](https://trailing-slash-guide.onrender.com/folder/)                             | [✅](https://trailing-slash-guide.onrender.com/folder/index.html)                            | [✅](https://trailing-slash-guide.onrender.com/both)                           | [✅](https://trailing-slash-guide.onrender.com/both/)                           | [✅](https://trailing-slash-guide.onrender.com/both.html)                          | [✅](https://trailing-slash-guide.onrender.com/both/index.html)                          |
| Azure Static Web Apps |                                         | [link](https://polite-bay-08a23e210.azurestaticapps.net)                  | [✅](https://polite-bay-08a23e210.azurestaticapps.net/file)                       | [💢 404](https://polite-bay-08a23e210.azurestaticapps.net/file/)                  | [✅](https://polite-bay-08a23e210.azurestaticapps.net/file.html)                   | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder)                      | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder/)                      | [✅](https://polite-bay-08a23e210.azurestaticapps.net/folder/index.html)                     | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both)                    | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both/)                    | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both.html)                   | [✅](https://polite-bay-08a23e210.azurestaticapps.net/both/index.html)                   |

## GitHub Pages

**Important**: GitHub Pages is historically one of the most popular and free option to host a static website. In 2021, there are better free alternatives, offering more features.

**Deployment**: [slorber.github.io/trailing-slash-guide](https://slorber.github.io/trailing-slash-guide)

| Url                | Result      |
| ------------------ | ----------- |
| /file              | ✅           |
| /file/             | 💢 404      |
| /file.html         | ✅           |
| /folder            | ➡️ /folder/ |
| /folder/           | ✅           |
| /folder/index.html | ✅           |
| /both              | ✅           |
| /both/             | ✅           |
| /both.html         | ✅           |
| /both/index.html   | ✅           |

## Netlify

Netlify has a setting `Post Processing > Asset Optimization > Pretty Urls` that affects the way a static site is served. Disabling the `Pretty Urls` setting can help prevent Netlify to add an unwanted trailing slash.

**VERY IMPORTANT**: the global checkbox `Disable asset optimization` is confusing and does not really disable the `Pretty Urls` settings in practice: make sure to uncheck all the `Asset optimization` independently.

### Default settings (`Disable asset optimization` checked)

**Deployment**: [trailing-slash-guide-default.netlify.app](https://trailing-slash-guide-default.netlify.app)

| Url                | Result      |
| ------------------ | ----------- |
| /file              | ✅           |
| /file/             | ➡️ /file    |
| /file.html         | ✅           |
| /folder            | ➡️ /folder/ |
| /folder/           | ✅           |
| /folder/index.html | ✅           |
| /both              | ✅           |
| /both/             | ➡️ /both    |
| /both.html         | ✅           |
| /both/index.html   | ✅           |

### Pretty Urls enabled

**Deployment**: [trailing-slash-guide-pretty-url-enabled.netlify.app](https://trailing-slash-guide-pretty-url-enabled.netlify.app)

| Url                | Result      |
| ------------------ | ----------- |
| /file              | ✅           |
| /file/             | ➡️ /file    |
| /file.html         | ✅           |
| /folder            | ➡️ /folder/ |
| /folder/           | ✅           |
| /folder/index.html | ✅           |
| /both              | ✅           |
| /both/             | ➡️ /both    |
| /both.html         | ✅           |
| /both/index.html   | ✅           |

### Pretty Urls disabled

**Important**: make sure the `Pretty Urls` checkbox is **really** unchecked (ie, don't use the broken `Disable asset optimization` global checkbox).

**Deployment**: [trailing-slash-guide-pretty-url-disabled.netlify.app](https://trailing-slash-guide-pretty-url-disabled.netlify.app)

| Url                | Result |
| ------------------ | ------ |
| /file              | ✅      |
| /file/             | ✅      |
| /file.html         | ✅      |
| /folder            | ✅      |
| /folder/           | ✅      |
| /folder/index.html | ✅      |
| /both              | ✅      |
| /both/             | ✅      |
| /both.html         | ✅      |
| /both/index.html   | ✅      |

## Vercel

Vercel has 2 options affecting how files are served with 6 possible combinations:
- [`cleanUrls`](https://vercel.com/docs/configuration#project/clean-urls)
- [`trailingSlash`](https://vercel.com/docs/configuration#project/trailing-slash)

**Important**: Next.js also has a distinct [`trailingSlash` option](https://nextjs.org/docs/api-reference/next.config.js/trailing-slash)

**Important**: surprisingly, by default `next export` creates `/myPath.html` but this filename is not well-supported by Vercel by default (unless you use `cleanUrls: true`)

### Default settings (no config file)

**Deployment**: [trailing-slash-guide.vercel.app](https://trailing-slash-guide.vercel.app)

| Url                | Result |
| ------------------ | ------ |
| /file              | 💢 404 |
| /file/             | 💢 404 |
| /file.html         | ✅      |
| /folder            | ✅      |
| /folder/           | ✅      |
| /folder/index.html | ✅      |
| /both              | ✅      |
| /both/             | ✅      |
| /both.html         | ✅      |
| /both/index.html   | ✅      |

## Cloudflare Pages

**Deployment**: [trailing-slash-guide.pages.dev](https://trailing-slash-guide.pages.dev)

| Url                | Result      |
| ------------------ | ----------- |
| /file              | ✅           |
| /file/             | ➡️ /file    |
| /file.html         | ➡️ /file    |
| /folder            | ➡️ /folder/ |
| /folder/           | ✅           |
| /folder/index.html | ➡️ /folder/ |
| /both              | ✅           |
| /both/             | ✅           |
| /both.html         | ➡️ /both    |
| /both/index.html   | ➡️ /both/   |

## Render

**Deployment**: [trailing-slash-guide.onrender.com](https://trailing-slash-guide.onrender.com)

| Url                | Result |
| ------------------ | ------ |
| /file              | ✅      |
| /file/             | ✅      |
| /file.html         | ✅      |
| /folder            | ✅      |
| /folder/           | ✅      |
| /folder/index.html | ✅      |
| /both              | ✅      |
| /both/             | ✅      |
| /both.html         | ✅      |
| /both/index.html   | ✅      |

## Azure Static Web Apps

**Deployment**: [polite-bay-08a23e210.azurestaticapps.net](https://polite-bay-08a23e210.azurestaticapps.net/)

| Url                | Result   |
| ------------------ | -------- |
| /file              | ✅      |
| /file/             | 💢 404 |
| /file.html         | ✅      |
| /folder            | ✅      |
| /folder/           | ✅      |
| /folder/index.html | ✅      |
| /both              | ✅      |
| /both/             | ✅      |
| /both.html         | ✅      |
| /both/index.html   | ✅      |

## TODO: add other hosting providers

TODO add all other static hosting providers: S3/CloudFront, Amplify, Azure, Heroku, Surge, Firebase, Gatsby Cloud ... and self-hosting tools (Apache, Nginx...)
