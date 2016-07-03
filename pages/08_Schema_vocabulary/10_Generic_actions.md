:::sidecode
## Examples
```text
document@create
entity.user@update
document.article@archive
document.article.news@create
entity.person.customer@trash
```
:::

## Generic actions

| Schema ID | Description |
| --------- | ----------- |
| [object]@create | Expresses that new object will be created. |
| [object]@update | Expresses that current object will be updated. |
| [object]@delete | Expresses that current object will be deleted. |
| [object]@trash  | Expresses that current object will be deleted but can be restored in future. |
| [object]@restore | Expresses that current object will be restored from archived or trashed state. |
| [object]@archive | Expresses that current object will be archived. |