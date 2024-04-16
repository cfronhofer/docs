# How can I customize the bulk Markdown Export?

One of the most powerful features of the Readwise to Markdown integration is the ability to [customize the formatting of exactly how you'd like your highlights/notes formatted individually](https://readwise.io/export/markdown/preferences). You can customize the formatting of your notes with the below options:

* Page Title
* Metadata (such as author, URL, category, title, image)
* Highlight header (parent of your new highlights added)
* Sync notification (file that summarizes which files were added/updated on every export).

You can customize your export by going to the [Markdown Export Preferences](https://readwise.io/export/markdown/preferences) page and toggling on "Use custom formatting."

Each section of the export has a "template." You can customize each template string to format exactly how you like using the [Jinja2 templating language](https://jinja.palletsprojects.com/en/2.11.x/).&#x20;

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/60873d653149d33a19c70bd6/file-13IPFLCcim.png)

The explanations below illustrate how customization works and give some useful examples.

***

## Page Title <a href="#title" id="title"></a>

By default, Readwise will append "(highlights)" to each page so you can differentiate a Readwise created page from your own. Here's the default template:

```django
{{ title }}{% raw %}
{% if not is_new_page %} (Updated {{ date }} at {{ time }}){% endif %}
{% endraw %}
```

Notice the `{{ title }}` variable. When a note is exported, that `{{ title }}` will be replaced with the book/article/tweet's actual title and `{{ date }}` with the current date.

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

From the [Markdown Export Preferences](http://readwise.io/export/markdown/preferences) page, you can also edit your page metadata, including the author, URL, category, title, image, and anything else you want to show up when each new book/article/tweet is imported.

Here's the default template:

```django
{% raw %}
{% if image_url -%}
![]({{image_url}})
{% endif -%}
### Metadata
- Author: {{author}}
- Full Title: {{full_title}}
- Category: #{{category}}
{% if url %}- URL: {{url}}{% endif %}
{% endraw %}
```

***

## Highlight Header <a href="#header" id="header"></a>

You can customize how the Header text above each set of synced highlights is formatted. By default, each time your highlights are synced they will be sub-bullets of this default header:

{% code overflow="wrap" %}
```django
{% raw %}
{% if is_new_page %} Highlights first synced by #Readwise [[{{date}}]] {% elif has_new_highlights %} New highlights added [[{{date}}]] at {{time}} {% endif %} 
<br>{% if is_new_page %}
Highlights
{% elif has_new_highlights %}
New highlights added {{date}} at {{time}}
{% endif %}
{% endraw %}
<br>
```
{% endcode %}

Note the `if` statement used above. By default, the header is formatted differently when the highlights are for a newly synced page versus new highlights on a previously synced page.

A common use case may be that you don't want the highlights backlinked to the date (the day they are synced). If that's the case, you can simply remove the \[\[]] wrapping the date, e.g:

```django
Highlights synced by #Readwise: {{date}} at {{time}}
```

***

## Sync Notification <a href="#notification" id="notification"></a>

Finally, every time you export your Markdown highlights, we can optionally generate a special markdown file which summarizes which files were added/updated.&#x20;

This setting is off by default, but it can be especially useful in note-taking apps that create a page for the date the highlights were exported and can be linked to that.
