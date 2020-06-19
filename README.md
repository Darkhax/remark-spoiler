# remark-spoiler
A [remark](https://github.com/remarkjs/remark) plugin that adds support for spoiler text. By default spoiler text is defined by wrapping text with `||`.

![A video showing spoiler text. The text is obscured until the cursor of the user is above the text.](https://i.imgur.com/ByJYfFu.gif "Spoiler Text Demo")
## Installation

```
npm install remark-spoiler
```

For best results you should use [remark-html](https://www.npmjs.com/package/remark-html) or similar.

## Usage

Import the plugin and then pass it into remark or your unified processor chain.

```js
import remark from 'remark';
import html from 'remark-html';
import spoiler from 'remark-spoiler';

remark.use(html).use(spoiler).process("||hello world||");
```

With this plugin the resulting HTML will be 

```html
<span class="spoiler">hello world</span>
```

**Note:** HTML does not have native support for "spoiler" text. This plugin applies a class name which allows CSS to apply custom formatting, however the plugin does not provide this CSS for you. There are many ways to style your spoilers, here is one example.

```css
.spoiler { 
    color: black; 
    background-color:black;
}
  
.spoiler:hover{
    background-color:white; 
}
```

## Options
You may supply an optional options object to configure the plugin. These are the options currently supported.

- `marker` - The token used to identify spoiler text. By default this is `||`.
- `nodeType` - The name of the node to create. By default this is `spoiler`.
- `tagType` - The name of the HTML tag to wrap the text in. The default is 'span'.
- `classNames` - An array of class names to use for the HTML tag. By default this is just 'spoiler'. Passing an empty array will disable this.

**Example**
```js
const spoilerOptions = {
    marker: '!!',
    classNames: ['thing1', 'thing2']
}

remark().use(html).use(spoiler, spoilerOptions).process("!!I Am Secret!!");
```

## License

[MIT](https://github.com/Darkhax/remark-spoiler/blob/main/LICENSE) © [Darkhax](https://github.com/Darkhax)