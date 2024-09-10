This is the [[Node js]] [[Method]] is used to export the [[function]]s which can be used by other files by importing it.

```js
const replaceStr = (str, char, replacer) => {
  const regex = new RegExp(char, "g")
  const replaced = str.replace(regex, replacer)
  return replaced
}

module.exports = { replaceStr }
```

