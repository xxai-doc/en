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

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

The markdown template, with the suffix `.mdt` , can refer to external files with a syntax similar to `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

Markdown translation will not translate codes and links, and will cache translated sentences. If the translation is modified but the original text is not modified, executing it again will not overwrite the modification of the translation.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Language files for translating `yaml` generated websites.
