# 08 Refactoring

> ## Paths

```tsx
// tsconfig.json
"paths": {
  "@libs/*": ["libs/*"],
  "@components/*": ["components/*"]
}

// pages/index.tsx
import FloatingButton from '@components/floating-button';
import Item from '@components/item';
import Layout from '@components/layout';
import useUser from '@libs/client/useUser';
import client from '@libs/server/client';
```
