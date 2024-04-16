# How does the Readwise to Tana export integration work?

Before you can export your Readwise highlights to Tana, you'll need to create an [API token](https://help.tana.inc/tana-input-api.html) for your Tana workspace:

1. In the Settings panel of Tana (represented by a gear icon), click API Tokens.
2. Select the Workspace you want your Readwise exports to appear in.
3. Click the + Create button.
4. Once the token is created, click Copy to save it to your clipboard.
5. In your Readwise account, go to the [Tana setup page](https://readwise.io/export/tana/token) and paste the token into the API field.
6. Click Save.

You'll then be directed to the integration options page.

The export has a variety of customization options (outlined in [this help article](https://help.readwise.io/article/157-how-can-i-customize-the-readwise-to-tana-integration)), but the default format will create a node for each document and tag it with the Supertag #Readwise. The highlights from the document will be nested underneath the document node and tagged with #highlights.

Note: If you plan to customize your formatting, we recommend doing a test export by enabling the "Select Items to Be Exported" option and choosing a few documents with a variety of metadata, to ensure that the export works as you expect. Once you've tweaked the options to your liking, you can re-export those few documents using the "refresh" icon on the far right of the document.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5eb8cc86042863474d1a75fd/images/64d2d74b9d8cf153a015db83/file-gdmHFmr3PN.png)

This interactive tutorial will guide you through the process of generating your API key and configuring the Readwise integration:

## What happens when I take new highlights? Will those automatically sync with Tana?

Yes! You can configure the Readwise Tana integration to automatically sync any new highlights that come into Readwise. If the highlight is from a _new_ book, article, or Twitter account, a new node will be created in your Tana account. If the highlight is from an _existing_ book, article, or Twitter account, the highlight will be _appended_ to below the existing node. Because the Readwise integration is append-only, nothing in Tana will ever be overwritten.

{% hint style="warning" %}
Certain services such as Amazon Kindle, Instapaper, and Pocket only synchronize with Readwise a few times a day. For this reason, the highlight may not immediately appear in either Readwise or Tana. If you need to sync sooner, you should first force a manual re-sync in Readwise (from the [Add Highlights](http://readwise.io/sync) section of the [Readwise Dashboard](http://readwise.io/dashboard)).
{% endhint %}

## How do I trigger a new sync to Tana?

By default, the Tana integration will export any new highlights as soon as they appear in Readwise. (Note that it may still take a few minutes for them to appear in your Tana account.) If you've disabled that option or simply want to force a fresh sync, you can click the "Start export to Tana" button on the [Tana Export settings page](https://readwise.io/export/tana/preferences).

## Can I edit the text of a book, article, or Twitter page in Tana?

Yes! You can edit the text of a highlight as you wish and the Readwise integration will not overwrite any changes you make. New highlights will be appended as a new node.

## What happens when I update highlights in Readwise? Will those changes automatically sync with Tana? (Or vice versa?)

Currently, no. New updates to existing highlights will not be reflected in already synced highlights. We want to make sure we don't overwrite any manual edits you might have made in your Tana workspace.

## Where does the Location link after each Kindle highlight take me?

If you have the Kindle app installed on your desktop, clicking the Location link will launch the Kindle app and jump you to the highlight in the book. More on those links here:  [Can I jump to a highlight directly in the Kindle app?](https://help.readwise.io/article/40-can-i-jump-to-a-highlight-directly-in-the-kindle-app)

## Can I customize how my notes appear in Tana?

Absolutely! See [this help article](https://help.readwise.io/article/157-how-can-i-customize-the-readwise-to-tana-integration) for more information on how you can customize the title, metadata, and more.

## Can I add new properties to my tags in Tana?

Yes! You can add as many new properties to the tags within Tana as you'd like and Readwise won't overwrite them in any subsequent syncs.

Do note that if you make any changes to the properties that Readwise creates (e.g. author, title, etc.), Readwise may not recognize it as the same schema on the next sync and may create a duplicate. If that happens, you can [merge the tags](https://help.tana.inc/how-do-i-merge-nodes-fields-or-tags.html) as needed.

## How do I reset the integration so I can start over fresh?

You can reset the integration by creating a new API token in your Tana workspace and replacing the previous one in your Readwise account. (You can access the token setup page from the link at the bottom of the [export options page](https://readwise.io/export/tana/preferences).)

This will prompt a fresh export the next time you sync, ignoring any previously exported content. This is also useful if you want to sync your Readwise account to a different Tana workspace.
