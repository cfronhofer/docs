# How do I import highlights from Scribd/Everand?

Scribd doesn't currently offer a native option to export highlights, but here's a workaround that allows you to export highlights from a single book at a time to import into Readwise.

Note: This method requires the Google Chrome web browser and may result in some highlights being truncated. This is a limitation of how the Scribd reading interface is formatted.

1. Go to [Scribd](https://www.scribd.com/) or [Everand](https://www.everand.com/) and open the book that you'd like to get the highlights from.
2. Click the **kebab icon (3 vertical dots)** in the right-hand corner, then click into **Notes & Bookmarks**:

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/617af0030332cb5b9e9b8bd7/file-wkqx0fMZ8G.png)

3. With the pop-up open, select **View** > **Developer** > **Developer Tools**:&#x20;

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/617af15f9ccf62287e5f0dcd/file-eL9uj8o4m1.png)

4. Select **Console** from the developer view and input the following script next to the `>` symbol, then press **Enter**. (You may need to type "allow paste" before it will allow you to paste the script in.)

{% code overflow="wrap" %}
```javascript
var annotations = document.querySelector('.annotations');

var notesParagraphs = Array.from(annotations.querySelectorAll('p'));

var notesText = notesParagraphs.map((paragraph) => `<p>${paragraph.innerHTML}</p>`).join('');var win = window.open("", "Title", "toolbar=no,location=no,directories=no,status=no,menubar=no,scrollbars=yes,resizable=yes,width=780,height=200,top="+(screen.height-400)+",left="+(screen.width-840));

win.document.body.innerHTML = `<div>${notesText}</div>`;
```
{% endcode %}

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/617af2710332cb5b9e9b8bf1/file-e1VKontNRJ.png)

5. A new window will open that contains all the highlights as plain text, and you can copy/paste the highlights to import them into Readwise with any of the following tools:

* [CSV Import](https://readwise.io/import\_bulk)
* [Freeform Input](https://readwise.io/import\_freeform)
* [PDF Import](https://help.readwise.io/article/41-can-i-import-highlights-from-pdfs)
