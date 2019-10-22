# Content format URLs

Useful for getting _URL_s together for \_AJAX_ calls. Can be used to get at specific content/component nodes in the linked page.

This _URL_ structure availability may require further _CQ_ setup. Check the Adobe docs about this.

## Examples

| Format-type | URL                                                                               |
| :---------- | :-------------------------------------------------------------------------------- |
| HTML        | `http://localhost:4503/content/{SITE_NAME}/{PAGE_NAME}/_jcr_content/content.html` |
| JSON        | `http://localhost:4503/content/{SITE_NAME}/{PAGE_NAME}/_jcr_content/content.json` |
| XML         | `http://localhost:4503/content/{SITE_NAME}/{PAGE_NAME}/_jcr_content/content.xml`  |

**Note:** This also works for specific content nodes.

## Child-pages/feed

Change the extension of a page from `.html` to `.feed` and it will get all the sub-pages under that page e.g. `http://localhost:4502/content/{SITE_NAME}/en/components-demo.feed?wcmmode=disabled`

