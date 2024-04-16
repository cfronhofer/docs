# How do I create a custom filtered view?

Reader comes with a few default filtered views—like “Recently added” and “Quick reads”—but you can also make your own to better fit your personal needs or preferences.

### Filter by tag or feed source

On your [Manage feeds](https://read.readwise.io/feed/sources) and [Manage tags](https://read.readwise.io/tags) pages, you can use the Views column to assign tags and feeds to specific views.

<figure><img src="https://s3.amazonaws.com/readwiseio/2023/12/add-tags-to-view_web.gif" alt="Add tags to views"><figcaption></figcaption></figure>

### Filter by author

In the Info tab of any document, you can click the name of the author to bring up a filtered view of all the documents by that author in your library. You can then name and save the view for easier future access.

<figure><img src="https://s3.amazonaws.com/readwiseio/2023/12/save-author-view_web.gif" alt="Save author as view"><figcaption></figcaption></figure>

### Filter by query

You can create filtered views within Reader that will automatically group various sources together based on the query. To do so, click into `Manage filtered views`, then click the `Add filtered view` button in the top right.

Filtered view queries can use a variety of different properties (you can view a full list in our [Reader Filtering Guide](https://www.notion.so/Reader-Filtering-Guide-d4b249df2eaa492283099ec2a3551640?pvs=21)), including tags and source domains. For example, if you had a tag called "football" and a blog feed from [footballnews.com](http://footballnews.com/), you could use the following query to group them together in a single saved view:

`tag:football OR (feed:true AND domain:footballnews)`

This would include any articles, videos, or other documents saved to your library which you've tagged "football," as well as any new documents that come into your feed from [footballnews.com](http://footballnews.com/).
