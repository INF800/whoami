---
title: Link local npm package with react app
updated: 2021-08-24 04:37
tags: npm, js
category: 
- Misc
---

### Link local npm package with react app

If you want to see changes in the dependant react app while making changes in the local source code of the npm package or library, use the following steps:

#### Step 1

Goto the npm package main dir and run

```
npm link
```

#### Step 2

Goto the dependant react app main dir and run 
```
npm link <package-name>
```

> That's it 🤯

Read more at https://docs.npmjs.com/cli/v7/commands/npm-link
