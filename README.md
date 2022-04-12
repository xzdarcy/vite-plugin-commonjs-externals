# [vite-plugin-commonjs-externals](https://github.com/xiaoxiangmoe/vite-plugin-commonjs-externals)

Provides commonjs externals support for Vite.

- Add vite optimize esbuild plugin. Allow to use cjs package in node_modules. [issue#2511](https://github.com/vitejs/vite/issues/2511) & [issue#2652](https://github.com/vitejs/vite/issues/2652)

For example:

```typescript
import { defineConfig } from 'vite';
import {
  commonjsExternals,
  esbuildCommonjsExternals,
} from '@xzdarcy/vite-plugin-commonjs-externals';

const commonjsPackages = [
  'electron',
  'electron/main',
  'electron/common',
  'electron/renderer',
];

export default defineConfig({
  optimizeDeps: {
    // working for libs in node_modules when developing.
    exclude: commonjsPackages,
    esbuildOptions: {
      plugins: [
        esbuildCommonjsExternals({
          externals: commonjsPackages,
        }),
      ],
    },
  },
});
```
