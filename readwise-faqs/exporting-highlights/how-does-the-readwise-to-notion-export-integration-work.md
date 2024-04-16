# How does the Readwise to Notion export integration work?

{% embed url="https://www.youtube.com/watch?v=jl7LD0K25A8" %}

To get started with Notion sync, select the Notion Export link from your [Readwise Dashboard](https://readwise.io/dashboard).

Once you configure the Readwise to Notion integration, Readwise will automatically synchronize all your highlighted documents to a database in Notion:

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

The first time Readwise syncs with Notion, a new table will be created in a private page of your selected Notion workspace. The process may take several minutes depending on how many books, articles, tweets, and highlights you have in your library. Feel free to close the export browser and move on to something else—the export will continue in the background. Also, once you're initially caught up, new highlights will automatically be synced to Notion periodically throughout the day.

By default, the Readwise table in Notion is separated into filtered views of Book, Article, Tweet, and Podcast pages, each of which contains all your highlights for that category of document. You can filter, sort, and search this table using all the power of Notion databases.

## **What happens when I take new highlights? Will those automatically sync with Notion?**

Yes! Whenever you import a new highlight into Readwise, it will be automatically exported to Notion without you needing to do anything. If the highlight is from a new book, article, or Twitter account, a new page in the Notion table will be made. If the highlight is from an existing book, article, or Twitter account, the highlight will be appended to the bottom of the existing page.

{% hint style="warning" %}
Certain services such as Amazon Kindle, Instapaper, and Pocket only synchronize with Readwise a few times a day. For this reason, the highlight may not immediately appear in either Readwise or Notion. If you need to sync sooner, you can force a manual resync from the [Add Highlights](http://readwise.io/sync) section of the [Readwise Dashboard](http://readwise.io/dashboard).
{% endhint %}

## Can I add new properties to the Readwise table in Notion?

Yes! You can add as many additional properties to the Notion table as you wish and those will not be overwritten by Readwise in subsequent syncs. Be careful not to change the names of the default properties shown below, however.

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="375"><figcaption></figcaption></figure>

## Can I move either the Readwise table or individual pages to another location in my Notion workspace?

Yes! You can move either the whole Readwise table or individual book, article, and Twitter pages within your Notion workspace and the Readwise integration will still find and properly update those.

If you'd like to move an individual page to another location and maintain the sync, you'll want to first make sure that the Readwise integration has access to the new location you're moving it to. You can do this by clicking into the "..." menu in the top right while viewing the intended destination page, going down to the Connections section and opening the "Connect to" menu, then searching for Readwise:

<div align="center">

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

</div>

## Can I rename the title of a book, article, or Twitter page in Notion?

Yes! You can rename either the whole table or individual book, article, and Twitter pages and the Readwise integration will still find and properly update those.

## Can I edit the text of a book, article, or Twitter page in Notion?

Yes! You can edit the text of a page as you wish and the Readwise integration will not overwrite any changes you make. New highlights will be appended to the bottom of the page.

## Can I make adjustments to the filters and views of the database?

Yes! By default, the Readwise table in Notion is separated into filtered views of Book, Article, and Tweet pages, each of which contains all your highlights for that entry. You can of course filter, sort, and search this table using all the power Notion brings to bear.

## Where does the Location link above each Kindle highlight take me?

If you have the Kindle app installed on your computer, clicking the Location link will launch the Kindle app and jump you to the highlight in the book. More on those links here: [Can I jump to a highlight directly in the Kindle app?](https://help.readwise.io/article/40-can-i-jump-to-a-highlight-directly-in-the-kindle-app)

## If I edit or format an existing highlight in Readwise, or make a new note or tag to an existing highlight, will that change be updated in Notion?

Not at the moment. Any edits, formatting, notes, or tags you had in Readwise before your first sync with Notion will appear in Notion, but new updates to existing highlights will not be reflected in already synced highlights. (We want to be careful not overwrite any manual edits you may have made within Notion.) That said, it's on our roadmap to figure out a solution here soon!

## How do I delete my Readwise table and start over?

1. Delete the Readwise page in Notion
2. Click the Trash section in Notion and delete permanently the Readwise page
3. Restart the Notion integration within Readwise

## How do I change the Notion workspace to export to?

All of your workspaces across different Notion accounts can be found in a dropdown menu in the [Notion preferences page](https://readwise.io/export/notion/preferences).&#x20;

If you don't see the dropdown menu, make sure you're logged into the Notion workspace you want to connect to and re-authorize your Notion connection here: [Notion login page](http://readwise.io/export/notion/login)

If you still don't see the dropdown menu, please try the steps below:

1. In Notion, select **Settings & Members** in the left-hand panel > **My Account** > **Log out of all devices**
2. Re-authorize your Notion connection with your selected workspace here: [Notion login page](http://readwise.io/export/notion/login)

## How do I disconnect my Notion account from Readwise? <a href="#how-do-i-disconnect-my-notion-account-from-readwise-fmc4u" id="how-do-i-disconnect-my-notion-account-from-readwise-fmc4u"></a>

You can disconnect your account from the [Export page](https://readwise.io/export) > select '...' > Remove connection:

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
