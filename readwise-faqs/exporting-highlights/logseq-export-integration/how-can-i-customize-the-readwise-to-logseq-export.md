# How can I customize the Readwise to Logseq Export?

One of the most powerful features of the Readwise to Logseq plugin is the ability to [customize the formatting of how your highlight data is imported into Logseq](https://readwise.io/export/logseq/preferences). You can customize a variety of elements including:

* Page title
* Metadata (such as author, URL, category, title, cover image)
* Highlight header (inserted whenever new highlights are added)
* Highlights themselves (e.g. inclusion of links to original, tags, notes, etc.)
* Sync notifications (a new entry in Logseq each time the Readwise plugin runs)

To begin customizing your export, head to the [Logseq Export](https://readwise.io/export/logseq/preferences) page from your Readwise Dashboard.&#x20;

Each component of the export has a "template" using the [Jinja2 templating language](https://jinja.palletsprojects.com/en/2.11.x/). The explanations below should illustrate how customization works and give some useful examples.

***

## Page Title

By default, Readwise will insert the title of each document as an H1 (# in Markdown) in the default template:&#x20;

```django
# {{title}} 
```

Notice the `{{title}}` variable. As your highlights are exported to Logseq, Readwise will replace the `{{title}}` variable with the document's actual title.

Let's say you wanted the first line of your export to be the document's title _plus_ the word "Highlights" in parentheses. All you would have to do is append the text " (Highlights)" to the template as follows:

```django
# {{title}} (Highlights) 
```

You can customize this much more using [inline-if statements](https://stackoverflow.com/a/14215034/1522443), [Jinja2 filters](https://jinja.palletsprojects.com/en/2.11.x/templates/#filters), and [much more](https://jinja.palletsprojects.com/en/2.11.x/templates/). The templating language is quite powerful!

***

## Metadata

One of the nicest aspects of the Readwise plugin is that each document can be enhanced with additional metadata such as author name, document URL, document tags, category, full title, cover image, and more.

In the special metadata first block of Logseq, the default template below will insert the author name with double brackets, full title with double brackets, document category (e.g. Book, Article, or Tweet) with a hashtag, URL (if there is one), and document tags in Readwise (if any) with double brackets. In the second block, the template will insert the cover image, if there is one.

{% code overflow="wrap" %}
```django
author:: [[{{author}}]]\
full-title:: {{full_title}}\
category:: #{{category}}\
{% raw %}
{% if url %}url:: {{url}}{% endif %}\
{% if document_tags %}tags:: {% for tag in document_tags %}#[[{{tag}}]] {% endfor %} {% endif %}
{% if image_url %}![]({{image_url}}){% endif %}
{% endraw %} 
```
{% endcode %}

Below is an example of how you'd modify the category line if you wanted to append an emoji to each category tag:

{% code overflow="wrap" %}
```django
Category: #{{category}}{{ " 📚" if category == "books"}}{{" 📰" if category == "articles"}}{{" 🐦" if category == "tweets"}}{{" 🎙" if category == "podcasts"}} 
```
{% endcode %}

Again, this templating language is quite powerful! You go much deeper with the customization using inline-if statements, Jinja2 filters, and more.

***

## Highlight Header

Another component of the template is the header text that appears above each set of synced highlights. The first time a document is exported to Logseq, the Highlight section will be delineated by a header reading "Highlights first synced by \[\[Readwise]] \[\[date]]". Any new highlights taken in this document will be appended beneath with a new header.

{% code overflow="wrap" %}
```django
{% raw %}
{% if is_new_page %}
Highlights first synced by [[Readwise]] [[{{date}}]]
{% elif has_new_highlights %}
New highlights added [[{{date}}]] at {{time}}
{% endif %}
{% endraw %} 
```
{% endcode %}

A common use case in tools for thought such as Roam Research and Obsidian is to backlink the date in this header to your Daily Notes page. To make this work for yourself, you'll need to format the `{{date}}` variable to match your Daily Notes formatting. For example, if your Daily Note uses the format of YYYY-MM-DD, you could match that format by adding a date filter to the variable like so: `{{date|date('Y-m-d')}}`

***

## Highlights

Of course, you can also format the export of the highlights themselves. By default, each highlight is inserted as a bullet (using a dash), followed by a hyperlink to the original highlight and then sub-bullets for any tags and notes attached to the highlight.

{% code overflow="wrap" %}
```django
{{ highlight_text }}{% raw %}
{% if highlight_location and highlight_location_url %} ([{{highlight_location}}]({{highlight_location_url}})){% elif highlight_location %} ({{highlight_location}}){% endif %}
    {% if highlight_tags %}
    **Tags**: {% for tag in highlight_tags %}#[[{{tag}}]] {% endfor %}
    {% endif %}
    {% if highlight_note %}
    **Note**: {{ highlight_note }}
    {% endif %}
{% endraw %}
```
{% endcode %}

As mentioned above, there is much more you can do using [inline-if statements](https://stackoverflow.com/a/14215034/1522443), [Jinja2 filters](https://jinja.palletsprojects.com/en/2.11.x/templates/#filters), and so on.

***

## Sync Notifications

Finally, you can configure the Readwise plugin to append an entry to your Daily Note each time the sync runs. This notification is particularly useful in tools such as Roam Research where the backlink appears more front and center in the Daily Note.
