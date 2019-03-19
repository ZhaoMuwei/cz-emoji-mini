# cz-emoji-mini

> Commitizen adapter formatting commit messages using emojis.

> This is a fork of [cz-emoji], with less emoji options.

[![Build Status](https://travis-ci.com/ZhaoMuwei/cz-emoji-mini.svg?branch=master)](https://travis-ci.com/ZhaoMuwei/cz-emoji-mini)
![npm](https://img.shields.io/npm/v/cz-emoji-mini.svg)

**cz-emoji-mini** allows you to easily use emojis in your commits using [commitizen].

```sh
? Select the type of change you are committing: (Use arrow keys)
❯ feature   🌟  A new feature
  fix       🐞  A bug fix
  docs      📚  Documentation change
  refactor  🎨  A code refactoring change
  chore     🔩  A chore change
```

## Install

```bash
npm install --global cz-emoji-mini

# set as default adapter for your projects
echo '{ "path": "cz-emoji-mini" }' > ~/.czrc
```

## Usage

```sh
$ git cz
```

## Customize

By default `cz-emoji-mini` comes preconfigured with the [Gitmoji](https://gitmoji.carloscuesta.me/) types.

But you can customize things on a project basis by adding a configuration section in your `package.json`:

```json
{
  "config": {
    "cz-emoji-mini": {}
  }
}
```

### Types

An [Inquirer.js] choices array:
```json
{
  "config": {
    "cz-emoji-mini": {
      "types": [
        {
          "emoji": "🌟",
          "code": ":star2:",
          "description": "A new feature",
          "name": "feature"
        }
      ]
    }
  }
}
```

The value `property` must be the emoji itself.

### Scopes

An [Inquirer.js] choices array:
```json
{
  "config": {
    "cz-emoji-mini": {
      "scopes": [
        "home",
        "accounts",
        "ci"
      ]
    }
  }
}
```

## Commitlint

Commitlint can be set to work with this package by leveraging the package https://github.com/arvinxx/commitlint-config-gitmoji.

```bash
npm install --save-dev commitlint-config-gitmoji
```

_commitlint.config.js_
```js
module.exports = {
  extends: [
    'gitmoji'
  ],
  parserPreset: {
    parserOpts: {
      headerPattern: /^(:\w*:)(?:\s)(?:\((.*?)\))?\s((?:.*(?=\())|.*)(?:\(#(\d*)\))?/,
      headerCorrespondence: [
        'type',
        'scope',
        'subject',
        'ticket'
      ],
    }
  }
};
```


## License

MIT © ZhaoMuwei <zhaomuwei@gmail.com>

MIT © [Nicolas Gryman](http://ngryman.sh)

[cz-emoji]: https://github.com/ngryman/cz-emoji
[commitizen]: https://github.com/commitizen/cz-cli
[Inquirer.js]: https://github.com/SBoudrias/Inquirer.js/
