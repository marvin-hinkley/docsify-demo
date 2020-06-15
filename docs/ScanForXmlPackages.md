
      ---
      title: ScanForXmlPackages
      ---

      ### Description:

This node returns a list of XML packages on your site.

### Full Syntax:

<ScanForXmlPackages PackageTypePrefix="entity|product|notification|feed|page|skin" SkinID="N"/>

### Notes:

*   **SkinID** \- Tells WSI which skin to look in for extant XML packages. This will return packages in the {root}/XmlPackages folder as well as the skin XmlPackages folder.
*   **PackageTypePrefix** \- Tells WSI which package types to return a list of. Valid values are 'entity', 'product', 'notification', 'feed', 'page', and 'skin'. If left blank, all packages will be returned.
*   If no SkinID is specified, WSI will use the site's default skin.

### Warnings:

None
      