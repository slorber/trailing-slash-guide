
# Static site generators

Let's figure out how different static site generators output static files for route `/myPath`.

## Jekyll

- Command: `jekyll build`
- Default output: `/myPath.html`
- Configuration: no options available

## Gatsby

- Command: `gatsby build`
- Default output: `/myPath/index.html` 
- Configuration: no, but various plugins exist

## Next.js

- Command: `next export`
- Default output: `/myPath.html`
- Configuration: [trailingSlash option](https://nextjs.org/docs/api-reference/next.config.js/trailing-slash) (different from Vercel [trailingSlash option](https://vercel.com/docs/configuration#project/trailing-slash))

## Docusaurus

- Default output: `/myPath/index.html`
- Configuration: [trailingSlash option](https://docusaurus.io/docs/docusaurus.config.js#trailing-slash)

## Nuxt

- Command: `nuxt generate`
- Default output: `/myPath/index.html`
- Configuration (Nuxt v2): [trailingSlash option](https://nuxtjs.org/docs/2.x/configuration-glossary/configuration-router#trailingslash)

## Hugo

- Command: `hugo`
- Default output: `/myPath/index.html`
- Configuration: no options available

## Angular Prerendering

- Default output: `/myPath/index.html`
- Configuration: no options available
- Docs: [Angular Prerendering (SSG)](https://angular.dev/guide/prerendering)

## TODO: add other static site generators

TODO add all other static site generators

