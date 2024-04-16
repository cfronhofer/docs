# How does the Readwise to Evernote export integration work?

## Setting up your Evernote export

You can connect your Evernote account from the [Readwise dashboard](https://readwise.io/dashboard) > [Export](https://readwise.io/export) > [Evernote preferences page](https://readwise.io/export/evernote/preferences).&#x20;

![](https://lh3.googleusercontent.com/OeUv-zmzDjGUY1gPwCP5sHx71idhbFKP6biTMAI-3ZYXrywdvsRUUOun1RfCl9\_dCVPflyKKzDcumgoceK5xutjLRSW4L0WYgLHTVv5sMu2hmg\_oIii\_G1LDDcmVk\_EYBpfvR40qSVcqFzVQ6W8w0BQ)

1. Export Automatically: Keep this on if you would like Evernote to sync daily. You can turn it off if you would prefer to only update Evernote when you manually trigger an export from this page.
2. Include Highlight Locations: Keep this on to include the location or page information of each highlight in the export.
3. Use Compact Layout: This will display the location information inline with the highlight text and won’t add any dividers between highlights.
4. Select Items to be Exported: Turning this option on will allow you to manually select which documents will be exported to Evernote. When this option is turned off, all documents in your account will sync when an export is triggered.&#x20;

## Where do my Readwise highlights go in Evernote?

The integration will create a “Readwise” notebook in your Evernote account and each document (e.g. book, article, etc.) will be imported as a note under that notebook. Each document’s note will contain all of its highlights and notes.

## Can I change the notebook destination of my Readwise highlights?

Unfortunately, there isn’t currently a way to change the destination of the Readwise export. However, once the integration has created the Readwise notebook, you can move that notebook into a notebook stack and the sync will still work as expected.

Note that you can rename the Readwise notebook and everything will still work. You can also move individual document notes into a different notebook, and new highlights made to the document will still sync to them when the integration is triggered.

## What happens when I add new highlights?

Any highlights you’ve made in existing documents since the last sync will be appended to the end of the existing note for that document in Evernote.

## How do notes work with the Evernote integration?

Any notes and tags attached to a highlight will export to Evernote with the highlight. However, if you edit the notes or tags of a highlight after it has already been exported to Evernote, you’ll need to re-export the documents to see those updates in your Evernote account.

## How can I refresh a document in Evernote?

If you’ve edited a document or highlight in Readwise and would like to re-export it to Evernote with the changes, you can do so via the following steps:

1. Go to the [Evernote export preferences page](https://readwise.io/export/evernote/preferences).
2. Toggle ON Select Items to be Exported (1).
3. Ensure that the document is selected to be exported (2), then click the refresh button to the far right (3).
4. Click Start export to Evernote at the top of the page.

![](https://lh5.googleusercontent.com/AEphMqKEts-cLUy9AI8xjgTp73vmu9takZkme9M0gneoWjsOE-SYL3xIvw4SCEKa\_4TwiiLo75KF2MAAUXVooEbFByRZXcg6GjvTGFOgkxMEaLivLLEnlkrvO2-Hv5DzMgCjrJVdw9C8elFvgr7QRnM)

This will create a duplicate note in Evernote with the updated content. You can delete the old version and any new exports will sync to the new note.

## How do I completely refresh my Readwise Evernote notebook of exported highlights?

If you would like to completely refresh all the Readwise content in your Evernote account, you can do so using these steps:

1. Delete the Readwise notebook in Evernote.
2. Empty the trash in your Evernote account.
3. On the Evernote export page in Readwise, click Start Export to Evernote.

All of your Readwise content should re-export to Evernote again in a new Readwise notebook.
