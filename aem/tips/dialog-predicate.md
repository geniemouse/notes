# `predicate` property `dialog`

**Note:** This may no longer be valid for AEM 6.1+.

The `predicate` property in a `dialog.xml` (or similar), tells the component which path types to display on an Sling resource tree.

Options:

-   Empty string (or property left out), yields full tree
-   `"folder"`
-   `"hierarchy"`
-   `"hierarchyNotFile"`
-   `"nosystem"`
-   `"siteadmin"`

If you need multiple _predicates_, pass the values as an array of strings.

Example:

```
<path
    jcr:primaryType="cq:Widget"
    fieldLabel="List results"
    name="./path"
    predicate="nosystem"
    rootPath="/api/v1/ListResults"
    xtype="pathfield"/>
```
