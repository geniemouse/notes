# Remove component wrapping `div`

<!-- MarkdownTOC -->

1. [JSP component](#jsp-component)
    1. [Globally](#globally)

<!-- /MarkdownTOC -->

## JSP component

### Globally

Add following to `global.jsp`

```
if (WCMMode.fromRequest(request) != WCMMode.EDIT && WCMMode.fromRequest(request) != WCMMode.DESIGN) {
    IncludeOptions.getOptions(request, true).forceSameContext(Boolean.TRUE);
}
```
