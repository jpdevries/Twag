# Twag

HTML tags in Twig.

Twag is a collection of Twig imports each of which represent an HTML tag and its associated&nbsp;attributes.

## Usage
Twag templates work the same as any other Twig template. Include the Twag template for the tag you'd like to use and pass in any optional&nbsp;attributes.
```twig
{% include 'twag/img.twig' with {
  'alt': 'A picture of a cat',
  'src': 'cat.jpg'
  } only %}
```

```html
<img alt="A picture of a cat" src="cat.jpg">
```

Tags that represent non&ndash;void elements can be included with the [Twig embed syntax](http://twig.sensiolabs.org/doc/tags/embed.html) and accept an `innerHTML`&nbsp;block.

```twig
{% embed "twag/label.twig" with {
  'for': 'cat'
} only %}
  {% block innerHTML %}
    A cool cat
  {% endblock %}
{% endembed %}
```

```html
<label for="cat">A cool cat</label>
```

What about miscellaneous attributes like `ARIA` and `data-attributes`? Pass a [Key Value](https://mijingo.com/blog/key-value-arrays-in-twig) array as a `misc` property to append those attributes as&nbsp;well.

```twig
{% include 'twag/img.twig' with {
  'alt': 'A picture of a cat',
  'src': 'cat.jpg',
  'misc': {
    'aria-hidden': 'false',
    'data-meow': 'true'
  }
} only %}
```

```html
<img alt="A picture of a cat" src="cat.jpg" aria-hidden="false" data-meow="true">
```

Miscellaneous attributes such as `hidden` that have no value are supported as&nbsp;well.

```twig
{% include 'twag/img.twig' with {
  'alt': 'A picture of a hidden cat',
  'src': 'cat.jpg',
  'misc': {
    'aria-hidden': 'true',
    'hidden': ''
  }
} only %}
```

```html
<img alt="A picture of a hidden cat" src="cat.jpg" aria-hidden="true" hidden>
```

## To Do
 - [Package with Composer?](https://github.com/jpdevries/Twag/issues/1)
 - Port Build to PHP?

## Contributing
Contributions are welcome. In the `_build` folder you'll find a `build.js` script and an accompanying `attributes` directory. There is a JSON file representing each HTML tag in the `attributes` folder that contains the attributes available for that&nbsp;tag.

To add a new tag, add the corresponding JSON file to the attributes folder. To update the attributes for a tag update the existing JSON file. Lastly, run the `build`&nbsp;script.

```bash
cd twag
npm install # if you haven't already
npm run build
```
