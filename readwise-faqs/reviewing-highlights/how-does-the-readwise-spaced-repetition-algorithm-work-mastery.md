# How does the Readwise spaced repetition algorithm work (Mastery)?

The Readwise spaced repetition algorithm (Mastery) is admittedly a bit of a black box compared to powerful spaced repetition software (SRS) such as Anki or SuperMemo. This is because we're trying to create a spaced repetition alternative that is extremely user-friendly, compared to the existing offerings that have notoriously steep learning curves.

That said, here are the details behind the Readwise spaced repetition algorithm:

* We use a decaying algorithm based on a recall probability half-life rather than a date-based algorithm as found in Anki.
* The initial half-life of a Mastery `later` is 14 days. `Soon` is 7 days. `Someday` is 28 days.
* Once a highlight recall probability decays to 50% or lower, it becomes a candidate to be resurfaced in the latter half of your Daily Review.

If you have a lot of Mastery flashcards that are candidates to be resurfaced (that is, their probability of recall is calculated to be less than 50%), then those with the lowest recall probability will be resurfaced in your Daily Review.

You can see all your Mastery flashcards, their half-lives, and their recall probabilities here: [readwise.io/mastery](https://readwise.io/mastery).
