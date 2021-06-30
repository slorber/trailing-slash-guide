
# Solutions

Here's a non-exhaustive list of possible solutions to try.

## Change settings of your static site generator

Some static site generators have settings to change how static files are outputted.

## Change your host provider

Use a host provider that supports better the static files created by your static site generator. 

Look into your current host provider options to fine-tune how files are served.

## Post-process your static site generator output before deployment

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
