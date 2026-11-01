# Query Boundary Audit

This is an independently published, **modified derivative of [Hono](https://github.com/honojs/hono)**, not an official Hono release or a new web framework. It preserves the original Git history, authorship, package names, and MIT license. Package installation and documentation links below refer to upstream Hono, not a published version of this modification.

This branch fixes [Hono issue #5596](https://github.com/honojs/hono/issues/5596): a requested query key containing literal `&` or `=` could match across raw query separators, returning the wrong value. The single-key fast path now handles only keys without those separators; encoded delimiter keys still resolve through the full parser. The regression checks the public request API against `URLSearchParams`, including both missing keys and later encoded matches.

To verify the change locally with the repository-pinned pnpm version:

```sh
corepack pnpm install --frozen-lockfile
corepack pnpm exec vp test --run src/request.test.ts src/utils/url.test.ts
```

Only read-only build and test automation remains in this derivative; upstream publish, issue-closing, and automated-write workflows are removed.

## Upstream Hono README

<div align="center">
  <a href="https://hono.dev">
    <img src="https://raw.githubusercontent.com/honojs/hono/main/docs/images/hono-title.png" width="500" height="auto" alt="Hono"/>
  </a>
</div>

<hr />

Hono - _**means flame🔥 in Japanese**_ - is a small, simple, and ultrafast web framework built on Web Standards. It works on any JavaScript runtime: Cloudflare Workers, Fastly Compute, Deno, Bun, Vercel, AWS Lambda, Lambda@Edge, and Node.js.

Fast, but not only fast.

```ts
import { Hono } from 'hono'
const app = new Hono()

app.get('/', (c) => c.text('Hono!'))

export default app
```

## Quick Start

```bash
npm create hono@latest
```

## Features

- **Ultrafast** 🚀 - The router `RegExpRouter` is really fast. Not using linear loops. Fast.
- **Lightweight** 🪶 - The `hono/tiny` preset is under 12kB. Hono has zero dependencies and uses only the Web Standard API.
- **Multi-runtime** 🌍 - Works on Cloudflare Workers, Fastly Compute, Deno, Bun, AWS Lambda, Lambda@Edge, or Node.js. The same code runs on all platforms.
- **Batteries Included** 🔋 - Hono has built-in middleware, custom middleware, and third-party middleware. Batteries included.
- **Delightful DX** 😃 - Super clean APIs. First-class TypeScript support. Now, we've got "Types".

## Documentation

The documentation is available on [hono.dev](https://hono.dev).

## Migration

The migration guide is available on [docs/MIGRATION.md](docs/MIGRATION.md).

## Communication

[X](https://x.com/honojs) and [Discord channel](https://discord.gg/KMh2eNSdxV) are available.

## Contributing

Contributions Welcome! You can contribute in the following ways.

- Create an Issue - Propose a new feature. Report a bug.
- Build middleware and libraries - Grow the Hono ecosystem.
- Share - Share your thoughts on the Blog, X, and others.
- Sponsor - Support the maintainers through GitHub Sponsors: [@yusukebe](https://github.com/sponsors/yusukebe) and [@usualoma](https://github.com/sponsors/usualoma).
- Make your application - Please try to use Hono.

For more details, see [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md).

## Contributors

Thanks to [all contributors](https://github.com/honojs/hono/graphs/contributors)!

## Authors

Yusuke Wada <https://github.com/yusukebe>

_RegExpRouter_, _SmartRouter_, _LinearRouter_, and _PatternRouter_ are created by Taku Amano <https://github.com/usualoma>

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.
