# How does Reader detect duplicate content?

Reader’s current de-duping logic will catch any documents that are saved multiple times with the same URL. If you re-save a URL, the document will be moved to the top of your Library and will feature a green dot in the upper left to indicate that you’ve saved it more than once.

However, the current logic isn’t able to detect duplicate _content_, so saving the same document from slightly different URLs will result in the creation of a second version. This often happens when a URL contains tracking information or other additional parameters (e.g. `https://site-name.com/article-title?utm_source=rss-feed` vs `https://site-name.com/article-title`), and this is the primary reason that articles saved from a Feed source won’t be recognized as duplicates of the same articles saved from the original website.
