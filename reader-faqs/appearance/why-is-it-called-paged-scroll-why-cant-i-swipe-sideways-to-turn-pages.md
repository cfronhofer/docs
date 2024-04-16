# Why is it called "paged scroll"? Why can't I swipe sideways to turn pages?

Although sideways swiping is the standard gesture for a lot of other reading apps, we couldn't implement pagination that way without reworking the entire UX of our mobile reading experience because those gestures are already reserved to open the Info panel and the table of contents. Additionally, the sideways swiping paradigm makes for an extraordinarily clunky highlighting experience, and we value highlighting too much to cripple it with pagination.

Ultimately, "paged scroll" turned out to be the innovation that solved both of those issues. By keeping the content vertical, pagination can be briefly disabled to allow for a smooth experience highlighting across pages. It also means that the swiping gestures don't interfere with the pre-existing sidebars. Plus, we were still able to implement tap zones to trigger a page turn, which ends up feeling very similar to a standard pagination experience.
