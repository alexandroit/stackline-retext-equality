# @stackline/retext-equality

> retext plugin to warn about possible insensitive, inconsiderate language.

[![npm version](https://img.shields.io/npm/v/@stackline/retext-equality.svg?style=flat-square)](https://www.npmjs.com/package/@stackline/retext-equality)
[![license](https://img.shields.io/npm/l/@stackline/retext-equality.svg?style=flat-square)](https://github.com/alexandroit/stackline-retext-equality)
[![GitHub repository](https://img.shields.io/badge/GitHub-repository-181717?style=flat-square&logo=github)](https://github.com/alexandroit/stackline-retext-equality)
[![Docs](https://img.shields.io/badge/docs-alexandro.net-0f766e?style=flat-square)](https://alexandro.net/docs/vanilla/retext-equality/)
[![Reddit community](https://img.shields.io/badge/community-r%2FStackline-ff4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/r/Stackline/)

**[Documentation](https://alexandro.net/docs/vanilla/retext-equality/)** | **[npm](https://www.npmjs.com/package/@stackline/retext-equality)** | **[Issues](https://github.com/alexandroit/stackline-retext-equality/issues)** | **[Repository](https://github.com/alexandroit/stackline-retext-equality)**

**Current package version:** `1.0.2`

---

## Why this package?

`@stackline/retext-equality` is the Stackline-maintained distribution of `retext-equality@6.6.0`. It is an independent continuation of [retext-equality](https://github.com/retextjs/retext-equality); original authors and licenses remain credited below.

## Compatibility

| Item | Value |
| :--- | :--- |
| Package | `@stackline/retext-equality@1.0.2` |
| API target | `retext-equality@6.6.0` |
| Supported Node.js | `See supported framework requirements` |
| License | `MIT` |
| Module type | `module` |
| Main entry | `index.js` |
| Types | `index.d.ts` |
| Runtime dependencies | `vfile, unified, quotation, @types/nlcst, @types/unist, nlcst-search, unist-util-is, nlcst-normalize, nlcst-to-string, unist-util-visit` |

## Installation

```bash
npm install @stackline/retext-equality
```

Preserve existing imports and plugin resolution with an npm alias:

```bash
npm install retext-equality@npm:@stackline/retext-equality
```

## Usage and API reference

### retext-equality


[**retext**][retext] plugin to check for possible insensitive, inconsiderate
language.

## Install

This package is [ESM only](https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c):
Node 12+ is needed to use it and it must be `import`ed instead of `require`d.

[npm][]:

```sh
npm install @stackline/retext-equality
```

## Use

Say we have the following file, `example.txt`:

```txt
He’s pretty set on beating your butt for sheriff.
```

…and our script, `example.js`, looks like this:

```js
import {readSync} from 'to-vfile'
import {reporter} from 'vfile-reporter'
import {unified} from 'unified'
import retextEnglish from 'retext-english'
import retextEquality from '@stackline/retext-equality'
import retextStringify from 'retext-stringify'

const file = readSync('example.txt')

unified()
  .use(retextEnglish)
  .use(retextEquality)
  .use(retextStringify)
  .process(file)
  .then((file) => {
    console.error(reporter(file))
  })
```

Now, running `node example` yields:

```txt
example.txt
  1:1-1:5  warning  `He’s` may be insensitive, use `They`, `It` instead  he-she  retext-equality

⚠ 1 warning
```

## API

This package exports no identifiers.
The default export is `retextEquality`.

### `unified().use(retextEquality[, options])`

Check for possible insensitive, inconsiderate language.

###### `options.ignore`

List of phrases *not* to warn about (`Array.<string>`).

###### `options.noBinary`

Do not allow binary references (`boolean`, default: `false`).
By default `he` is warned about unless it’s followed by something like `or she`
or `and she`.
When `noBinary` is `true`, both cases would be warned about.

### Messages

See [`rules.md`][rules] for a list of rules and how rules work.

Each message is emitted as a [`VFileMessage`][message] on `file`, with the
following fields:

###### `message.source`

Name of this plugin (`'@stackline/retext-equality'`).

###### `message.ruleId`

See `id` in [`rules.md`][rules].

###### `message.actual`

Current not ok phrase (`string`).

###### `message.expected`

Suggest ok phrase (`Array.<string>`).

###### `message.note`

Extra information, when available (`string?`).

## Related

*   [`alex`](https://github.com/get-alex/alex)
    — Catch insensitive, inconsiderate writing
*   [`retext-passive`](https://github.com/retextjs/retext-passive)
    — Check passive voice
*   [`retext-profanities`](https://github.com/retextjs/retext-profanities)
    — Check for profane and vulgar wording
*   [`retext-simplify`](https://github.com/retextjs/retext-simplify)
    — Check phrases for simpler alternatives

## Contributing

See [`contributing.md`][contributing] in [`retextjs/.github`][health] for ways
to get started.
See [`support.md`][support] for ways to get help.

To create new patterns, add them in the YAML files in the [`data/`][script]
directory, and run `npm install` and then `npm test` to build everything.
Please see the current patterns for inspiration.
New English rules will be automatically added to `rules.md`.

Once you are happy with the new rule, add a test for it in [`test.js`][test] and
open a pull request.

This project has a [code of conduct][coc].
By interacting with this repository, organization, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]



[build-badge]: https://github.com/retextjs/retext-equality/workflows/main/badge.svg

[build]: https://github.com/retextjs/retext-equality/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/retextjs/retext-equality.svg

[coverage]: https://codecov.io/github/retextjs/retext-equality

[downloads-badge]: https://img.shields.io/npm/dm/retext-equality.svg

[downloads]: https://www.npmjs.com/package/retext-equality

[size-badge]: https://img.shields.io/bundlephobia/minzip/retext-equality.svg

[size]: https://bundlephobia.com/result?p=retext-equality

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/retextjs/retext/discussions

[npm]: https://docs.npmjs.com/cli/install

[health]: https://github.com/retextjs/.github

[contributing]: https://github.com/retextjs/.github/blob/HEAD/contributing.md

[support]: https://github.com/retextjs/.github/blob/HEAD/support.md

[coc]: https://github.com/retextjs/.github/blob/HEAD/code-of-conduct.md

[license]: license

[author]: https://wooorm.com

[retext]: https://github.com/retextjs/retext

[message]: https://github.com/vfile/vfile-message

[script]: script

[test]: test.js

[rules]: rules.md

## Credits and original authors

- Original project: [retext-equality](https://github.com/retextjs/retext-equality).
- Titus Wormer.
- Shinnosuke Watanabe.
- Elliott Hauser.
- Ryan Tucker.
- David Simons.
- rugk.
- Eli Feasley.
- Eli Sadoff.
- Flip Stewart.
- Catherine Etter.
- Conlin Durbin.
- Jen Weber.
- Matsuko.
- Saksham Gupta.
- Aaron Miller.
- Alicia Gansley.
- Anna K.
- Bryce Kahle.
- Ben Hall.
- Copyright (c) 2015 Titus Wormer <tituswormer@gmail.com>.
- Stackline maintenance: [Alexandro Paixao Marques](https://www.linkedin.com/in/aleinfo/) and [Stackline contributors](https://github.com/alexandroit).

Original copyright, license notices and contributor acknowledgements remain part of this distribution. Stackline maintenance does not replace authorship of the original work.

## Community and Links

- [Stackline website](https://alexandro.net/)
- [GitHub projects](https://github.com/alexandroit)
- [npm packages](https://www.npmjs.com/~alex360qc)
- [Reddit community — r/Stackline](https://www.reddit.com/r/Stackline/)
- [Maintainer LinkedIn](https://www.linkedin.com/in/aleinfo/)

Use this repository's issue tracker for reproducible bugs and feature requests. Join r/Stackline for examples, usage questions and release discussions.
