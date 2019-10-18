# Disable the AEM Link Checker

AEM checks the integrity of links and files in `author` via a link-checking tool.

Disable it for specific resources via the `x-cq-linkchecker` attibute. It accepts values `"valid"` or `"skip"`.

`x-cq-linkchecker="valid|skip"`

```
<a href="LOCATION_TARGET" x-cq-linkchecker="skip">A test link</a>
<script src="LOCATION_OF_SCRIPT_FILE" x-cq-linkchecker="skip"></script>
```

**Notes:**

-   The Link Checker should not be enabled on `publish` instances
-   It is also possible to disable link-checking globally via the AEM Web Console, etc.

**More information**

[https://helpx.adobe.com/experience-manager/kb/DisableLinkChecker.html]
