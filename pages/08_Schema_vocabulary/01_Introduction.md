:::sidecode
## Examples
```text
document.article
document.book@create
entity.user
device.light@turnOn
device.network.router+vendor.com.mikrotik
device.phone+vendor.com.samsung
```
:::

## Introduction

Purpose of schema vocuabulary is to define common objects and actions so MetaWeb resources can be easily understandable by machines and search engines.

Schema ID is written in format `[object]@[action]`

Action is applicable in `@action` meta property. If object is omitted then current resource schema is used.

Objects can be combined with plus (`+`) sign.