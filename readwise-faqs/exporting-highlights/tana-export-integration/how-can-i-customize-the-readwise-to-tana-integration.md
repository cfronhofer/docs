# How can I customize the Readwise to Tana integration?

One of the most powerful features of the Readwise to Tana integration is the ability to customize exactly how you would like the formatting of your notes to appear in Tana.

The customizable elements include:

* Note title
* Highlight formatting (links to original, tags, notes, etc)
* Metadata (such as author, URL, category)

You can customize your export by going to the [Tana export preferences page](https://readwise.io/export/tana/preferences) and turning on the "Use Custom Formatting" toggle.

Each component of the export customization has a "template" using the [Jinja2 templating language](https://jinja.palletsprojects.com/en/2.11.x/). You can customize each of these templates to achieve your desired format in Tana.

***

## Title <a href="#title" id="title"></a>

By default, Readwise will append "(highlights)" to each node so you can differentiate a Readwise created node from your own. Here's the default template:

```django
{{title}} (highlights) #{{category}}
```

Notice the `{{ title }}` variable. When a note comes into Tana, that `{{ title }}` will be replaced with the document's actual title.

The `#{{category}}` variable is also included here so that Tana will recognize the document categories (books, articles, etc.) as tags. This will allow you to view your notes by category and to add or edit the Supertag properties for them.

Note: All documents exported from Readwise will also be appended with the #Readwise tag. This is not a customizable part of the template because it is part of the integration's core functionality and shouldn't be removed.

You also have some other variables available to you. For example, here's how you can prepend each title with the name of the author:

```django
{{author}} - {{title}} #{{category}}
```

Of course, you can customize the title significantly further, using [inline-if statements](https://stackoverflow.com/a/14215034/1522443), [Jinja2 filters](https://jinja.palletsprojects.com/en/2.11.x/templates/#filters), and [much more](https://jinja.palletsprojects.com/en/2.11.x/templates/). The templating language is quite powerful!

***

## Highlight <a href="#highlight" id="highlight"></a>

This section is a little more complex, but can support some powerful workflows. Here's the default template:

```django
{{ highlight_text }} #highlight
{% raw %}
{% if highlight_location_url %}
    Readwise Location:: {{highlight_location_url}}
{% endif %}
{% if highlight_tags %}
    Topics:: {% for t in highlight_tags %} {{t}}{% endfor %}
{% endif %}
{% if highlight_note %}
    Notes:: {{ highlight_note }}
{% endif %}
{% endraw %}
```

Note the indentation above. The highlight text is shown at the top level, with the default #highlight tag inline with it. Nested under the highlight text are the location information (e.g. page number, link back to article/tweet, etc.) and any notes or tags attached to that highlight, if they exist.

Why might you want to customize the highlight text? For one, if you'd just prefer to change the default formatting, for example by putting notes inline or at the parent level.

Here's an example of how you might add the highlight date as a new field:

```django
{{ highlight_text }} #highlight
{% raw %}
{% if highlight_location_url %}
    Readwise Location:: {{highlight_location_url}}
{% endif %}
{% if highlight_tags %}
    Topics:: {% for t in highlight_tags %} {{t}}{% endfor %}
{% endif %}
{% if highlight_note %}
    Notes:: {{ highlight_note }}
{% endif %}
{% if highlight_date %}
    Date Highlighted:: {{ highlight_date }}
{% endif %}
{% endraw %}
```

There is, of course, much more you can do with this by using the [Jinja2 templating language](https://jinja.palletsprojects.com/en/2.11.x/).

***

## Metadata

Below the highlights template, you'll find a series of toggles that allow you to enable/disable and rename the fields that Readwise will create for each document node. (Note that these are the _document_-level properties, not the _highlight_-level properties.)

The default settings look like this:

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/64d40d00dd84587802e5d71d/file-W5Yf1wcgQI.png)

You can enable or disable any of these fields simply by clicking the corresponding toggle on or off. In the fields to the right, you can customize what the titles of the fields will be when exported to Tana. For example, if you already have a field called "Title" that you use as a different part of your Tana workflow, you could change "Title" here to be "Document Title" instead.
