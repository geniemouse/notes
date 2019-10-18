# Questions archive

Archived solutions to previous AEM questions that are worth keeping references to.

These may apply to certain (previous) versions of AEM.

<!-- MarkdownTOC -->

1. [Component questions](#component-questions)
    1. [Multiple `smartimage`s in single dialog tab](#multiple-smartimages-in-single-dialog-tab)
    1. [Checkbox value persistance](#checkbox-value-persistance)

<!-- /MarkdownTOC -->

## Component questions

### Multiple `smartimage`s in single dialog tab

_AEM 5.x/Classic UI_

https://stackoverflow.com/questions/18897531/can-multiple-smartimage-xtypes-appear-on-one-dialog-tab-in-aem

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:Dialog"
    height="{Long}600"
    title="dialog"
    xtype="dialog">
    <items
        jcr:primaryType="cq:Widget"
        xtype="tabpanel">
        <items jcr:primaryType="cq:WidgetCollection">
            <panel
                jcr:primaryType="cq:Panel"
                title="Panel with two Images">
                <items jcr:primaryType="cq:WidgetCollection">
                    <firstimage
                        jcr:primaryType="cq:Widget"
                        cropParameter="./firstimage/imageCrop"
                        ddGroups="[media]"
                        fieldLabel="first image field"
                        fileNameParameter="./firstimage/fileName"
                        fileReferenceParameter="./firstimage/fileReference"
                        height="{Long}200"
                        name="./firstimage/file"
                        rotateParameter="./firstimage/imageRotate"
                        title="First Image"
                        width="{Long}200"
                        xtype="html5smartimage"/>
                    <secondimage
                        jcr:primaryType="cq:Widget"
                        cropParameter="./secondimage/imageCrop"
                        ddGroups="[media]"
                        fieldLabel="second image field"
                        fileNameParameter="./secondimage/fileName"
                        fileReferenceParameter="./secondimage/fileReference"
                        height="{Long}200"
                        name="./secondimage/file"
                        rotateParameter="./secondimage/imageRotate"
                        title="secondimage"
                        width="{Long}200"
                        xtype="html5smartimage"/>
                </items>
            </panel>
        </items>
    </items>
</jcr:root>
```

### Checkbox value persistance

_AEM < 6.1/Classic UI_

https://stackoverflow.com/questions/25574605/checkbox-value-persist

Basic answer, use `xtype="selection"` with a `type="checkbox"`.

```
<facebook
    jcr:primaryType="cq:Widget"
    fieldLabel="Facebook"
    name="./facebook"
    type="checkbox"
    xtype="selection"/>
```
