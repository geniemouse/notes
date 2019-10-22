# Get the template-type from page properties

Call on the value of `cq:template` in the page properties.

**Example**

```
Boolean isHomeTemplate = currentPage.getProperties().get("cq:template", "").contains("page_home");
```

## Don't use `currentPage.getTemplate()`

It used to be possible to call on `currentPage.getTemplate()` (pre-CQ5.5).

On CQ5.5+, this causes pages not to render in _Publish_ environment.

**Example**

```
Boolean isSearchTemplate = currentPage.getTemplate().getPath().contains("page_search");
```

From CQ5.5 onwards on _Publish_, the above approach fails on a permissions basis. `currentPage.getTemplate()` is not for use on non-_Author_ environments as this would breach security. Do not change permissions access to this object on _Publish_.
