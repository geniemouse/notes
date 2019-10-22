# Component tips

<!-- MarkdownTOC -->

1. [Use categories to prefix component names in the Sidekick](#use-categories-to-prefix-component-names-in-the-sidekick)
1. [Hide any components that an Editor should not independently add to a page](#hide-any-components-that-an-editor-should-not-independently-add-to-a-page)

<!-- /MarkdownTOC -->

## Use categories to prefix component names in the Sidekick

Namespace a component's visible name with a catgeory that describes to the Content Editor what the component is intended for. Categories could inlcude:

-   Content
-   Layout
-   Navigation
-   Social
-   ..._etc_

I would suggest this approach even if also utilitsing the `componentGroup` settings.

Original suggestion found on Brad Meehan's blog:

-   ["Use categories to prefix component names" - Part one](https://adobeaemtherightway.wordpress.com/2014/09/08/usability-tip-use-categories-to-prefix-component-names/)
-   ["Use categories to prefix component names" - Part two](https://adobeaemtherightway.wordpress.com/2014/11/18/usability-tip-use-categories-to-prefix-component-names-part-2/)

## Hide any components that an Editor should not independently add to a page

Don't offer access to components in the Sdiekick if you don't want Content Editors to use them ;)

These might be special components that are _'baked-into'_ a specific template and/or require specialist set-up.

DESCRIPTION TBC.

This can also be done via group permissions and `componentGroup`, if access needs to be more fine-grained.
