# YES Script — VS Code Markup Highlighter
Download the [visual studio extension](https://marketplace.visualstudio.com/items?itemName=ProtoComplete.yes-script).

## About
Syntax highlighting for **YES** (**Y**our **E**xtensible **S**cript) files in Visual Studio Code.

YES is a meta-scriptlet standard whose elements, keys, and evaluation are user-defined.

See the available parsers to integrate with your own software:
- [rust](https://github.com/TheMaverickProgrammer/rust_yes_parser)
- [js](https://github.com/TheMaverickProgrammer/js_yes_parser)
- [dart](https://github.com/TheMaverickProgrammer/dart_yes_parser)
- [lua](https://github.com/TheMaverickProgrammer/lua_yes_parser)

> Read the [full spec](https://github.com/TheMaverickProgrammer/rust_yes_parser/tree/master/spec) to learn more.

---

## Features

| Token | Scope | Colour role |
|---|---|---|
| `#` comment lines | `comment.line.number-sign.yes` | comment |
| `!` global sigil | `keyword.control.global.sigil.yes` | keyword |
| Global name | `entity.name.function.global.yes` | function |
| `@` attribute sigil | `storage.modifier.attribute.sigil.yes` | storage |
| Attribute name | `entity.name.tag.attribute.yes` | tag |
| Standard element name | `entity.name.function.element.yes` | function |
| Key in `key=value` | `variable.other.key.yes` | variable |
| `=` operator | `keyword.operator.assignment.yes` | operator |
| `"..."` string literal | `string.quoted.double.yes` | string |
| `[...]` custom literal | `string.other.literal.bracket.yes` | string |
| Numeric values (`5f`, `1.0s`, `128`) | `constant.numeric.yes` | number |
| `true` / `false` | `constant.language.boolean.yes` | boolean |
| Unquoted raw values | `string.unquoted.yes` | string |
| `,` delimiter | `punctuation.separator.delimiter.yes` | punctuation |
| `\` line continuation | `punctuation.separator.continuation.yes` | punctuation |

---

## File Associations

These are the available supported file format extensions using YES script.

| Extension | Description |
|---|---|
| `.yes` | Generic YES Script file |
| `.cts` | Scene/cutscene script file |
| `.cart` | Configuration, Assembly, Resources, and Text file |
| `.ani` | Modern animation document format |
| `.anim` | Legacy animation document format |

---

## Installation

### From `.vsix` (recommended)

```
code --install-extension yes-script-1.0.0.vsix
```

### Manual (development)

1. Copy this folder into `~/.vscode/extensions/yes-script/`
2. Restart VS Code.

### Build the `.vsix` yourself

```bash
npm install
npx vsce package --allow-missing-repository
```

---

## Grammar Overview

Based on the formal production rules from the YES spec:

```
<ELEMENT>   → <SYMBOL> <NAME> <KEYVALUE>
<SYMBOL>    → ! | @ | # | ε
<KEYVALUE>  → <VALUE> | <KEY>=<VALUE> | <KEYVALUE> <DELIMITER> <KEYVALUE> | ε
<DELIMITER> → space | ,
<RAWTOKEN>  → <TOKEN> | "<TOKEN>" | ⌈<TOKEN>⌋
```

Reserved characters that cannot appear unquoted in element names: `!`, `#`, `@`, `,`

---

## License
The this vsix project is licensed GPLv2.

The parsers and their specification are protected by CDDL. See any of the upstream repositories for details.
