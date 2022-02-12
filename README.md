# Tree Shake Test

This repository was a quick test: I wanted to see if `import * as something from './file'` would affect tree-shaking, compared to specifying exactly which imports are necessary.

The good news: it doesn't matter! If you don't try to access an exported function, it will be trimmed out of the final bundle, no matter how you import it.

To reproduce the experiment:

1. Clone this repo
2. Install dependencies (`npm install`)
3. Build the codebase (`npm run build`)
4. Inspect the compiled code, in `build/static/js/main.6edac0cf.js`

In the compiled code, you should be able to command-F / control-F and find the text `console.log("Function`.

If the tree shaking works, you should be able to find function 1:1 and function 2:1, since those functions are actually called. But you should _not_ be able to find 1:2 and 2:2.

You can see how the code is imported in `index.js`.
