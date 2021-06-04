# Trailing Slash Guide

Have trailing slash problems after deploying a static website in production?

This repo aims to cover an exhaustive combination of [static site generators](#static-site-generators) and [hosting providers](#hosting-providers), and suggest some [possible solutions](#possible-solutions).

Solution are proposed at the very end.

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

- Gatsby outputs `/myPath/index.html` for `/myPath`: it can lead host providers to add a trailing slash.
- Gatsby's SPA router (Reach-Router) can route both `/myPath` and `/myPath/` after React hydration.

### Next.js

- Next.js outputs by default `/myPath.html` for `/myPath` on `next export`: static host providers generally don't add any extra trailing slash.
- Next.js has a [{trailingSlash: true}](https://nextjs.org/docs/api-reference/next.config.js/trailing-slash) config setting to output `/myPath/index.html`.

### Docusaurus

- Docusaurus outputs `/myPath/index.html` for `/myPath`: it can lead host providers to add a trailing slash.
- Docusaurus's SPA router (React-Router) can route both `/myPath` and `/myPath/` after React hydration.

### TODO: add other static site generators

TODO add all other static site generators

## Hosting providers

Let's deploy the same [static](/static) folder to multiple hosting providers, and see how each file is served.

This folder is a representative sample of the output of static site generators:

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
- `/file.html`
- `/folder`
- `/folder/`
- `/folder/index.html`
- `/both`
- `/both/`
- `/both.html`
- `/both/index.html`

### GitHub Pages

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

### Netlify

Netlify has a setting `Post Processing > Asset Optimization > Pretty Urls` that affects the way a static site is served. Disabling the `Pretty Urls` setting can help prevent Netlify to add an unwanted trailing slash.

#### Default settings (`Disable asset optimization` checked)

**Important**: the global checkbox `Disable asset optimization` is confusing and does not really disable the `Pretty Urls` settings in practice: make sure to uncheck all the `Asset optimization` independently.

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

#### Pretty Urls enabled

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

#### Pretty Urls disabled

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

### Vercel

**Important**: surprisingly, `next export` creates by default `/myPath.html` (when `trailingSlash: false`) but this pattern is not well supported by Vercel.

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

### Cloudflare Pages

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

### Render

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

### TODO: add other hosting providers

TODO add all other static hosting providers: S3/CloudFront, Amplify, Azure, Heroku, Surge, Firebase... and self-hosting tools (Apache, Nginx...)

## Possible solutions

Here's a non-exhaustive list of possible solutions to try.

### Change settings of your static site generator

Some static site generators have settings to change how static files are outputted.

### Change your host provider

Use a host provider that supports better the static files created by your static site generator. Eventually look into your current host provider options to fine-tune how files are served.

### Post-process your static site generator output before deployment

It is possible to change from one static file pattern `/myPath.html` to another `/myPath/index.html`.

Notice that most host providers don't create redirect if both files are present, so you could also use both patterns at the same time.

A simple Node.js script can be used to process your static site before deployment, for example:

```js
const glob = require('glob-promise');
const path = require('path');
const fs = require('fs-extra');

// /myPath/index.html => /myPath.html
async function generateSimpleHtmlFiles(outDir) {

  const pattern = path.join(outDir, '/**/index.html');
  const filePaths = (await glob(pattern)).filter(filePath => {
    return filePath !== path.join(outDir, '/index.html');
  });


  await Promise.all(
    filePaths.map(async filePath => {
      if ((await fs.stat(filePath)).isDirectory()) {
        return;
      }
      const filePathCopy = `${path.dirname(filePath)}.html`;
      if (await fs.pathExists(filePathCopy)) {
      } else {
        await fs.copyFile(filePath, filePathCopy);
      }
    })
  );
}

generateSimpleHtmlFiles("/public"); // Your static site output folder
```
