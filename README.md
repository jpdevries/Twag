# Twag

HTML tags in Twig.

Twag is a collection of Twig imports each of which represent an HTML element and its associated&nbsp;attributes.

## Usage
Twag templates work the same as any other Twig template. Include the Twag template for the tag you'd like to use and pass in any optional&nbsp;attributes.
```twig
{% include 'twag/img.twig' with {
  'alt': 'A picture of a cat',
  'src': 'cat.jpg'
  } only %}
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

## Contributing
Contributions are welcome. In the `_build` folder you'll find a `build.js` script and an accompanying `attributes` directory. There is a JSON file representing each HTML tag in the `attributes` folder that contains the attributes available for that&nbsp;tag.

To add a new tag, add the corresponding JSON file to the attributes folder. To update the attributes for a tag update the existing JSON file. Lastly, run the `build`&nbsp;script.

```bash
cd twag
npm install # if you haven't already
npm run build
```
