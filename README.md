# imooc-vite

When using Vue with vscode, ```@apply``` in ```.vue``` file will keep warning ```Unknown at rule @applycss(unknownAtRules)```. My idea is to disable ```vetur``` style validation in vscode and install `stylelint` instead.

## Stylelint installtion

```bash
yarn add stylelint stylelint-config-rational-order stylelint-config-recommended stylelint-order -D
```

And then we need to install `postcss` for avoding `postcss 8` error.

```bash
yarn add postcss -D
```

touch file ```stylelint.config.js```

```js
module.exports = {
  extends: ['stylelint-config-recommended'],
  plugins: ['stylelint-order', 'stylelint-config-rational-order/plugin'],
  rules: {
    'at-rule-no-unknown': [
      true,
      {
        ignoreAtRules: ['tailwind', 'apply', 'variants', 'responsive', 'screen'],
      },
    ],
    'declaration-block-trailing-semicolon': null,
    'no-descending-specificity': null,
    'order/properties-order': [],
    'plugin/rational-order': [
      true,
      {
        'border-in-box-model': false,
        'empty-line-between-groups': false,
      },
    ],
  },
};

```

In order to able ```format on save``` in vscode

```json
{
  "vetur.validation.style": false,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  }
}
```

