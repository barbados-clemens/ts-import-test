# Missing edge for Workspace nodes

When an import isn't able to resolve to a project the edge is removed between projects. Even though there is a valid package.json workspaces dependencies definition.Even
i.e. `demo` imports `lib-one`
but imports from the root, `import { something } from '@org/lib-one';`
`lib-one` only exports something like

```json
{
  "exports": {
    "./package.json": "./package.json"
  }
}
```

> Note see how there is a missing `.` root level export

This will prevent the edge from being shown between two projects

Even if you have `"@org/lib-one": "worksapces:*"` in the `demo` project `package.json`. It's almost as if when there is an "invalid" import between project all previous metadata is remove or all processing of files stops. Meaning the package.json def should still create the edge.
