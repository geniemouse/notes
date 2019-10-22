# Troubleshooting

<!-- MarkdownTOC -->

1. [`ClientLibs` not being written to `publish`](#clientlibs-not-being-written-to-publish)
1. [Components list not showing in _Sidekick_](#components-list-not-showing-in-sidekick)
1. [Conflicting Git/VLT line-endings](#conflicting-gitvlt-line-endings)
1. [\(CQ5.5\) Creating template-only content package](#cq55-creating-template-only-content-package)
1. [Image previews disappear](#image-previews-disappear)

<!-- /MarkdownTOC -->

## `ClientLibs` not being written to `publish`

The web client must have permissions to access the `cq:ClientLibraryFolder` node.

-   Locate the node below `/etc/clientlibs` in the repository
-   Can also expose libraries from secured areas of the repository (see Embedding Code From Other Libraries, below).

## Components list not showing in _Sidekick_

This issue described sometimes occurs when a new content package that has template content information saved in it is installed/re-installed.

-   Ensure that some component groups have been added to various template/page `parsys` areas
-   If above is true and the components still don't show:
    -   Open CRXDE Lite
    -   Expand the templates settings `/etc/designs/{SITE_NAME}/`
    -   Select the top template-level `jcr:content` node
    -   Check the meta data list for key `sling:resourceType`, it should have a value of `wcm/core/components/designer`; if it is missing, add it
    -   _Save All_

If a content package install/re-install is the cause of this issue, make sure the content package is re-built with the root-level template `jcr:content` `sling:resourceType` saved in place.

## Conflicting Git/VLT line-endings

If an AEM developer team works across PC and Macs, there may be line-ending conflicts when commiting changes to Git. This issue may spill-over to VLT if the Git set-up is not resolved.

-   [Configuring Git to handle line-endings](https://help.github.com/en/articles/configuring-git-to-handle-line-endings) (GitHub)
-   [Mind the End of Your Line](https://adaptivepatchwork.com/2012/03/01/mind-the-end-of-your-line/) (blog article, 2012)

## (CQ5.5) Creating template-only content package

In _CQ5.5_, there appears to be a bug when trying to install/re-install a template-only content package. In past versions of _CQ_, it was possible to build a package like this simply by creating a package (in the _CQ Package Manager_), selecting the folder `/etc/designs/{SITE_NAME}/jcr:content`. However, in _CQ5.5_ installing a template-only content package adds the content as expected, then deletes the whole `jcr:content` node in the very last line of the build log!

In order to get round this issue, create a package that point at `/etc/designs/{SITE_NAME}/`, then add `exclude` filters for everything else in the folder, e.g.:

| Filter-type | Value                                  |
| :---------- | :------------------------------------- |
| _exclude_   | `/etc/designs/{SITE_NAME}/css(/._)?`   |
| _exclude_   | `/etc/designs/{SITE_NAME}/fonts(/._)?` |
| _exclude_   | `/etc/designs/{SITE_NAME}/image(/._)?` |
| _exclude_   | `/etc/designs/{SITE_NAME}/js(/._)?`    |

## Image previews disappear

If a custom component has more than one image tab in its _dialog_, a bug occurs whereby previously added images disappear in the image preview panes (the image content reference remains intact). This is caused by the image `xml` attribute references not being unique within the component and the lack of hard-coded `sling:resourceType` references pointing to the foundation image component: `libs/foundation/components/image`.
