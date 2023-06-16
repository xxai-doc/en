<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Part of the website code is open source, welcome to help optimize the translation.

## front-end code

* [front-end code](https://github.com/xxai-art/web)
* [Language packs for the site as a whole](https://github.com/xxai-art/web/tree/main/i18n)
* [Language packs for login modules](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Website Multilingual Documentation](https://github.com/xxai-doc)

The front-end programming language is [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , which adds some features based on the coffeescript syntax, see [./coffee_plus.md](./coffee_plus.md) .

## Internationalization of websites and documents

Build on the following 3 projects

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  The suffix is `.mdt` , you can use the syntax similar to `<+ ./coffee_plus/import.js>` to refer to external files, and generate markdown with the suffix `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown translation will not translate codes and links, and will cache translated sentences. If the translation is modified but the original text is not modified, executing it again will not overwrite the modification of the translation.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Language files for translating `yaml` generated websites.

### Document Translation Automation Instructions

See repository [xxai-art/doc](https://github.com/xxai-art/doc)

It is recommended to install nodejs, [direnv](https://direnv.net) and [bun](https://github.com/oven-sh/bun) first, and then run `direnv allow` after entering the directory.

In order to avoid overly large warehouses translated into hundreds of languages, I created a separate code warehouse for each language and created an organization to store this warehouse

Setting the environment variable `GITHUB_ACCESS_TOKEN` and then running [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) will automatically create the warehouse.

Of course, you can also put it in a warehouse.

Translation script reference [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

The script code is interpreted as follows:

[bunx](https://bun.sh/docs/cli/bunx) is a replacement for npx, which is faster. Of course, if you don't have bun installed, you can use `npx` instead.

`bunx mdt zh` renders `.mdt` in the zh directory as `.md` , see the 2 linked files below

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` is the core code for translation (if you only have `nodejs` installed, but `bun` and `direnv` are not installed, you can also run `npx i18n` to translate).

It will parse [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , the configuration of `i18n.yml` in this document is as follows:

```
en:
zh: ja ko en
```

The meaning is: Chinese translation to Japanese, Korean, English, English translation to all other languages. If you only want to support Chinese and English, you can just write `zh: en` .

The last is [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , which extracts the content between the main title and the first subtitle of each language's `README.md` to generate an entry `README.md` . The code is very simple, you can look at it yourself.

Google API is used for free translation. If you cannot access Google, please configure and set a proxy, such as:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

The translation script will generate a translation cache in `.i18n` directory, please check it with `git status` and add it to the code repository to avoid repeated translations.
