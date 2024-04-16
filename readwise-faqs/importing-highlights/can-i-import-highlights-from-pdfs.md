# Can I import highlights from PDFs?

{% embed url="https://www.youtube.com/watch?v=oAVRt-YAuPE" %}

{% hint style="warning" %}
Please note that **support for PDF highlights is in perpetual beta** so you may discover a new bug from time to time. If you do, let us know and we'll do our best to fix it promptly!
{% endhint %}

To import highlights from a PDF, simply email the highlighted PDF file as an attachment to **add@readwise.io** (from an email address associated with your Readwise account).

That's it.

You can also upload PDFs by selecting the [PDF Import](https://readwise.io/import/pdf) option from Add Highlights.

## What PDFs work best?

PDF is a fickle file format, so some PDFs highlight better than others:

* **Digital PDFs.** Highlights extract much cleaner from digital PDFs than scanned PDFs with OCR applied.
* **Single Column PDFs.** Text in a single column extracts _much_ more accurately than two or three column PDFs. You can still extract highlights from multi-column PDFs: just be prepared for things to sometimes fall out of order. The absolute worst are PDF presentations with text all over the page.&#x20;
* **Left-to-Right PDFs.**

## What happens if a highlight spans two pages?

Due to limitations of the PDF file format, the highlight will be broken into two separate highlights. Fortunately, we have a workaround. Use the concatenation feature described here: [How to Combine Highlights On-the-Fly with Readwise](https://blog.readwise.io/combine-highlights-on-the-fly/).

## What PDF reader apps work with Readwise?

Thus far, we've had positive results with the following apps (provided you are working with a clean PDF to begin with):

* Preview (on Mac)
* Adobe Acrobat
* PDF Expert
* LiquidText (note: there is a LiquidText glitch where you must do all of your highlighting in a single session)
* Foxit
* iAnnotate
* DEVONthink
* PDFPenPro

If you could let us know what PDF app you're using when you email **add@readwise.io** PDFs, it would really help us!

## Which PDF reader apps do not work with Readwise?

Believe it or not, there are some PDF reading apps that do not take normal highlights per the PDF annotation spec, so our parser cannot extract them. These apps include:

* MarginNote
* GoodNotes
* Notability
* Adobe Acrobat on iPad and Android tablets (we're looking into this)

If extracting highlights from PDFs is important to you, we recommend switching to one of the reader apps listed in the section above!

## Can I send multiple PDFs in a single email?

Yes, but the size of the attachments must be below 30 megabytes in total.

## How do title and author work?

Readwise extracts the document title and author name from the PDF metadata. Not every PDF reader application enables editing of these properties. If your preferred app does allow metadata editing, we encourage you to make it a habit to clean these up, as some PDFs have strange metadata for reasons unknown to us.

If the PDF has no metadata, Readwise will use filename as book title and leave the author blank.

{% hint style="warning" %}
Note: If a PDF does import with incorrect metadata, you can edit the title and author in Readwise.
{% endhint %}

## I've imported PDF highlights but I can't find them in Readwise?

If you didn't receive an error email from Readwise, you likely can't find the PDF highlights in Readwise because the file had strange metadata. In other words, it's named something non-obvious. Open the PDF, find a highlight, and search Readwise for a fragment of the highlight text.

## Why does my PDF keep coming back with an error?

As a bit of background, PDF is an incredibly fickle file format originally created in 1993 for the purpose of printing digital documents to analog paper. Technology has come such a long way in the past 30 years that, if we had our druthers, we'd move people off PDF entirely and into something meant for the digital-first world (e.g. an ebook standard such as EPUB or MOBI).

Of course, network effects are strong and that's not going to happen for a long time, if ever.

Until then, we're gradually discovering edge cases and improving our parsing through a lot of manual hard-coding. In nearly all cases, we don't deliberately choose not to support a particular PDF reader. Instead, the PDF reader decides—for whatever reason—not to use the official PDF annotation spec but rather to, for example, draw yellow rectangles with transparency on top of the document. Other times, the PDF may look like ordinary text to the user, but It's really either a scanned image or series of tiny letter-shaped images (encoded entirely differently from text) which can't be picked up by ordinary software.
