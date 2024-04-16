# Why can't I permanently delete highlights?

The reason that Readwise only uses a soft _Discard_ rather than a hard _Delete_ might seem odd at first, but it's fairly intuitive once you understand the rationale:

Readwise synchronizes your highlights from a variety of sources. For instance, if you hard-deleted a Kindle highlight in Readwise but not in the original Kindle source, then the next time Readwise is synced with Kindle, Readwise would see the deleted highlight as new. The previously deleted highlight would then be re-imported to Readwise, causing it to return from the dead like a frustrating zombie highlight.

We could always just delete the highlight from the frontend in Readwise and save a copy in the backend to compare against future syncs, but that would be misleading and frustrate users who want to recover an accidentally deleted highlight.

If permanently annihilating a highlight is important to you, then we advise you to do so in the original source. Then refresh those highlights within Readwise via the following steps:

1\. Select the **down arrow** next to the book/article to open the document options

2\. Select **Refresh Highlights**

3\. Re-sync highlights from source here: [readwise.io/welcome/sync?refresh=true](http://readwise.io/welcome/sync?refresh=true)

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/60b54ae54dda6972e0930ee3/file-Z6VcEiCeMg.png)

{% hint style="warning" %}
The above directions don't apply to manually entered highlights or to those taken with the Readwise web clipper. Your options are to delete the book/article and re-enter all your highlights while leaving out the ones you want to delete permanently or just discarding.&#x20;
{% endhint %}
