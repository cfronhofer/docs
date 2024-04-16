# It seems some of my Instapaper articles are missing. How do I make sure ALL my Instapaper articles i

If it looks like you're missing Instapaper or Pocket articles within Reader, first note that any articles that were archived inside Instapaper or Pocket will appear inside your Archive in Reader; the ten most recently saved items not archived will appear inside your Inbox in Reader; everything else will go in Later.

If you've checked those places and still don't find the articles you're looking for, it's possible you might be hitting an Instapaper API export bug which caps the number of items export at 500. To get around this, you can download a CSV export of your Instapaper articles ([Settings](https://www.instapaper.com/user) > **Export** > **Download .CSV file**) and then upload those on [read.readwise.io/import](http://read.readwise.io/import).

Note that some items are considered “private content” by Instapaper and are unavailable to third parties. This includes things like emails forwarded to your Instapaper account. You’ll be able to see these articles in the CSV export (the URLs will start with `instapaper-private://` ), but since the document is kept private by Instapaper, Reader won’t be able to import them.
