# setting-up-husky-on-js-project

# About repository:

This is a basic repo to help with setting up husky on a node-js project;
The final outcome results in running a git pre-commit hook that prettifies all staged files.

* Step 1:

Install husky as a dev-dependency `npm install husky --save-dev`

* Step 2:

Install prettier and pretty-quick `npm install prettier pretty-quick --save-dev`

* Step 3:

Enable git hooks `npx husky install`

* Step 4:

Update package.json scripts to have git hooks enabled after package installations 

```
{
  "scripts": {
    ....
    "prepare": "husky install"
  }
}
``` 

* Step 5:

Add a script to run prettier on every staged file pre-commit.

```
{
  "scripts": {
    ...
    "format-files": "pretty-quick --staged"
  }
}
```

* Step 6:

Setup the prettier options. In the projects root directory create a .prettierrc file and add the following

```
{
    "bracketSpacing": true,
    "semi": false,
    "singleQuote": true,
    "trailingComma": "es5",
    "printWidth": 80
}
```

* Step 7:

Setup the pre-commit hook to run the prettier file formatting script
```
npx husky add .husky/pre-commit 'npm run format-files'
```
