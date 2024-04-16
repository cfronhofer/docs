# How can I customize the Readwise to Roam Export?

One of the most powerful features of the Readwise to Roam integration is the ability to [customize the formatting of exactly how you'd like your data imported into Roam](https://readwise.io/magicaltrashpanda).

You can customize the formatting of your notes:

* Page title
* Metadata (such as author, URL, category, title, cover image)
* Highlight header (parent of any new highlights added)
* Highlights themselves (links to original, tags, notes, etc.)
* Sync notification (shows up in the #Readwise page, letting you know of new highlights from your daily)

You can customize your export by going to the [Roam Export Preferences](http://readwise.io/export/roam/preferences) page and toggling on "Use custom formatting."

At a high level, each component of the export customization has a "template" that uses the [Jinja2 templating language](https://jinja.palletsprojects.com/en/2.11.x/). You can customize each of these templates to achieve your desired formats in Roam. As you tweak the templates in Readwise, you'll be able to see a live preview of what your notes will look like in Roam.&#x20;

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

The explanations below should illustrate how customization works, and give some useful examples. And if you're looking for more metadata examples and explanations, [check out this great guide :)](https://roamstack.com/feed-roam-using-readwise/)

***

## Page Title <a href="#title" id="title"></a>

By default, Readwise will append "(highlights)" to each page so you can differentiate a Readwise created page from your own. Here's the default template:

```django
{{ title }} (highlights)
```

Notice the `{{ title }}` variable. When a note comes into Roam, that `{{ title }}` will be replaced with the book/article/tweet's actual title.

You also have some other variables available to you. For example, here's how you can prepend each title with the category (i.e. is this a book, article, or tweet?)

```django
{{category}}/{{title}}
```

This would result in something like Book/Atomic Habits.

If you want all of your Readwise highlights to just show up in one page (though we don't recommend this), you could set the template to a non-variable string such as this:

```django
{{"All Highlights"}}
```

Of course, you can customize the title significantly further, using [inline-if statements](https://stackoverflow.com/a/14215034/1522443), [Jinja2 filters](https://jinja.palletsprojects.com/en/2.11.x/templates/#filters), and [much more](https://jinja.palletsprojects.com/en/2.11.x/templates/). The templating language is quite powerful!

***

## Page Metadata <a href="#metadata" id="metadata"></a>

From the [Roam Preferences](http://readwise.io/magicaltrashpanda) page, you can also edit your Roam page metadata, including the author, URL, category, title, image, and anything else you want to show up when each new book/article/tweet is imported.

Here's the default template:

{% code overflow="wrap" %}
```django
Author:: [[{{author}}]]
Full Title:: {{full_title}}
Category:: #{{category}}
{% raw %}
{% if document_tags %}Document Tags:: {% for tag in document_tags %}#{{tag}} {% endfor %} {% endif %}
{% if url %}URL:: {{url}}{% endif %}
{% if image_url %}![]({{image_url}}){% endif %}
{% endraw %}
```
{% endcode %}

Here's an example of some modifications you can make to, e.g. create a TODO for each new highlight, add custom backlinks, and customize formatting based on the category of book/article/tweet.

{% code overflow="wrap" %}
```django
{% raw %}
{% if category == "tweets" %}
#twitter 🐦
{% elif category == "books" %}
{{"{{"}}[[TODO]]{{"}}"}} #toprocess process & summarize the highlights from this book
{% else %}
This is a podcast/article
{% endif %}

Author:: [[{{author}}]]
Full Title:: {{full_title}}
Category:: #{{category}}{{ " 📚" if category == "books"}}{{" 📰" if category == "articles"}}{{" 🐦" if category == "tweets"}}{{" 🎙" if category == "podcasts"}}
{% if document_tags %}Document Tags:: {% for tag in document_tags %}#{{tag}} {% endfor %} {% endif %}
{% if url %}URL:: {{url}}{% endif %} 
{% if image_url %}![]({{image_url}}){% endif %}
{% endraw %}
```
{% endcode %}

***

## Highlight Header <a href="#header" id="header"></a>

You can customize how the Header text above each set of synced highlights is formatted. By default, each time your highlights are synced they will be sub-bullets of this default header:

{% code overflow="wrap" %}
```django
{% raw %}
{% if is_new_page %}
Highlights first synced by #Readwise [[{{date}}]]
{% elif has_new_highlights %}
New highlights added [[{{date}}]] at {{time}}
{% endif %}
{% endraw %}
```
{% endcode %}

Note the `if` statement used above. By default, the header is formatted differently when the highlights are for a newly synced page versus new highlights on a previously synced page.

A common use case may be that you don't want the highlights backlinked to the date (the day they are synced). If that's the case, you can simply remove the \[\[]] wrapping the date, e.g:

```django
Highlights synced by #Readwise: {{date}} at {{time}}
```

***

## Highlight Content <a href="#highlight" id="highlight"></a>

Customizing the highlight itself is a little more complex, but can support some insane workflows. Here's the default template:

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

Note the indentation above. The highlight text is shown at the top level, with the location information (e.g. page number, link back to article/tweet, etc.) inline with it. Nested under the highlight text are any notes and tags attached to that highlight, if they exist.

Why might you want to customize the highlight text? For one, maybe you'd just like to tweak the default formatting, e.g. putting notes inline or at the parent level.

Here's an example of how you can embed saved tweets directly into Roam, rather than having just their text sync:

{% code overflow="wrap" %}
```django
{% raw %}
{% if category == "tweets" %}{{ highlight_location_url }}{% else %}{{ highlight_text }}{% if highlight_location and highlight_location_url %} ([{{highlight_location}}]({{highlight_location_url}})){% elif highlight_location %} ({{highlight_location}}){% endif %}{% endif%}
    {% if highlight_tags %}
    **Tags**: {% for tag in highlight_tags %}#[[{{tag}}]] {% endfor %}
    {% endif %}
    {% if highlight_note %}
    **Note**: {{ highlight_note }}
    {% endif %}
{% endraw %}
```
{% endcode %}

You might also want to enable a more complex workflow, like having all of your highlights synced to the same page, regardless of books. Here's how you might do that:

{% code overflow="wrap" %}
```django
{{ highlight_text }}{% raw %}
{% if highlight_location and highlight_location_url %} ([{{highlight_location}}]({{highlight_location_url}})){% elif highlight_location %} ({{highlight_location}}){% endif %}
    Category: [[{{ category }}]]
    Title: [[{{title}}]]
    Author: [[{{author}}]]
    {% if highlight_tags %}
    **Tags**: {% for tag in highlight_tags %}#[[{{tag}}]] {% endfor %}
    {% endif %}
    {% if highlight_note %}
    **Note**: {{ highlight_note }}
    {% endif %}
{% endraw %}
```
{% endcode %}

In this case, you would also change the Page Title template to something like:

```django
{{ "Readwise Highlights" }}
```

(Note that because this example uses no variables, all highlights will have the same page title and thus write to the same page.)

There is, of course, much more you can do with this.

***

## Sync Notification <a href="#notification" id="notification"></a>

Finally, every time Readwise syncs new highlights you've made into your Roam account, it appends a message into your #Readwise page in Roam to notify you of the updates. This links to your daily note as well, so you can see all the highlights you made in one day. Here's the default template:

{% code overflow="wrap" %}
```django
On [[{{date}}]] at {{time}} Readwise synced {{num_highlights}} highlight{{num_highlights|pluralize}} from {{num_books}} book{{num_books|pluralize}}.
```
{% endcode %}

Note the use of the pluralize filter from Jinja2, which makes the note read more naturally. In the case that you **don't** want these notifications in your daily note, you can simply unlink the date reference like so:

{% code overflow="wrap" %}
```django
On {{date}} at {{time}} Readwise synced {{num_highlights}} highlight{{num_highlights|pluralize}} from {{num_books}} book{{num_books|pluralize}}.
```
{% endcode %}

If you don't want these sync notifications _at all_, you can delete the entire template for sync notifications.
