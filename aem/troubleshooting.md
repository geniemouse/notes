# Troubleshooting

<!-- MarkdownTOC -->

1. [Conflicting Git/VLT line-endings](#conflicting-gitvlt-line-endings)
1. [`ClientLibs` not being written to `publish`](#clientlibs-not-being-written-to-publish)

<!-- /MarkdownTOC -->

## Conflicting Git/VLT line-endings

If an AEM developer team works across PC and Macs, there may be line-ending conflicts when commiting changes to Git. This issue may spill-over to VLT if the Git set-up is not resolved.

-   [Configuring Git to handle line-endings](https://help.github.com/en/articles/configuring-git-to-handle-line-endings) (GitHub)
-   [Mind the End of Your Line](https://adaptivepatchwork.com/2012/03/01/mind-the-end-of-your-line/) (blog article, 2012)

## `ClientLibs` not being written to `publish`

The web client must have permissions to access the `cq:ClientLibraryFolder` node.

-   Locate the node below `/etc/clientlibs` in the repository
-   Can also expose libraries from secured areas of the repository (see Embedding Code From Other Libraries, below).
