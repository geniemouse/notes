# Sharing _dialog_ fields & tabs across components

AKA: How to use `.infinity.json`.

By keeping shared configuration separate, we avoid cross-referencing components. Wherever a common part is used, it is very clear to the developer that it is a shared piece of content and that multiple components may be affected.

<!-- MarkdownTOC -->

1. [A place for shared settings](#a-place-for-shared-settings)
1. [Create a settings XML file](#create-a-settings-xml-file)
1. [How to reference shared settings](#how-to-reference-shared-settings)
1. [Original source articles](#original-source-articles)

<!-- /MarkdownTOC -->

## A place for shared settings

Create a commons directory (if one doesn't already exist), e.g. `/apps/example/components/commons/`.

The commons dorectory shouldn’t contain any _dialog_ or _cq\\\_editConfig.xml_ files; we don’t want the settings showing in the sidekick.

## Create a settings XML file

In the commons directory, create a `richTextSettings.xml`. It might look something like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" jcr:primaryType="nt:unstructured">
    <edit jcr:primaryType="nt:unstructured" features="[cut,copy,delete]" defaultPasteMode="plaintext"/>
    <paraformat jcr:primaryType="nt:unstructured" features="*">
        <formats jcr:primaryType="cq:WidgetCollection">
            <p jcr:primaryType="nt:unstructured" tag="p" description="Paragraph"/>
            <h1 jcr:primaryType="nt:unstructured" tag="h1" description="Heading 1"/>
            <h2 jcr:primaryType="nt:unstructured" tag="h2" description="Heading 2"/>
            <h3 jcr:primaryType="nt:unstructured" tag="h3" description="Heading 3"/>
            <h4 jcr:primaryType="nt:unstructured" tag="h4" description="Heading 4"/>
        </formats>
    </paraformat>
    <styles jcr:primaryType="nt:unstructured" features="*">
        <styles jcr:primaryType="cq:WidgetCollection">
            <successButton jcr:primaryType="nt:unstructured" cssName="btn btn-success" text="Success Button"/>
            <defaultButton jcr:primaryType="nt:unstructured" cssName="btn btn-default" text="Default Button"/>
            <infoButton jcr:primaryType="nt:unstructured" cssName="btn btn-info" text="Info Button"/>
            <primaryButton jcr:primaryType="nt:unstructured" cssName="btn btn-primary" text="Primary Button"/>
        </styles>
    </styles>
</jcr:root>
```

Note that the `jcr:nodeType` of the node defined here is just `nt:unstructured`. This can be different if you want to define a tab (`cq:Panel`) or a widget (`cq:Widget`).

## How to reference shared settings

This is how to reference it:

```
<?xml version="1.0"?>
<productDescription
    jcr:primaryType="cq:Widget"
    allowBlank="true"
    fieldLabel="Product Description"
    name="./productDescription"
    xtype="richtext">
        <rtePlugins
            jcr:primaryType="nt:unstructured"
            path="/apps/example/components/commons/richTextSettings.infinity.json"
            xtype="cqinclude"
        />
</productDescription>
```

## Original source articles

Blog article _**"Reusing Tabs or Fields in Multiple Dialogs"**_ from
[Adobe AEM the right way](https://adobeaemtherightway.wordpress.com/2015/07/28/guest-post-reusing-tabs-or-fields-in-multiple-dialogs/) by Tomek Niedźwiedź.

<small>(Previous version _**"Reusing tabs or fields from an existing dialog"**_ from [Adobe AEM the right way](https://adobeaemtherightway.wordpress.com/2014/07/31/reusing-tabs-or-fields-from-an-existing-dialog/) by Brad Meehan.)</small>
