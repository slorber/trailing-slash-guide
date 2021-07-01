
# Static site generators

Let's figure out how different static site generators output static files for route `/myPath`.

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

## NuxtJS

- Command: `nuxt generate`
- Default output: `/myPath`
- Configuration: [trailingSlash option](https://nuxtjs.org/docs/2.x/configuration-glossary/configuration-router#trailingslash)

## TODO: add other static site generators

TODO add all other static site generators

