---
title: Apply patches
description: Learn how to view patches compatible with your Adobe Commerce on cloud infrastructure project and the status.
feature: Cloud, Upgrade
role: Admin, Developer
type: Troubleshooting
exl-id: 923c1e43-45da-450f-bdfc-de84a901400d
---
# View available patches

With every release of a new QPT version, a set of quality patches are introduced to fix known issues or bugs in your Adobe Commerce implementation. Each patch is compatible with specific versions of Adobe Commerce.

See [[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) for a complete list of released patches and their supported Adobe Commerce versions.

To view patches that are compatible with your Adobe Commerce environment, follow the steps below.

## Steps to view available patches and status

For on cloud infrastructure, run the command: 

```bash
php ./vendor/bin/ece-patches status
```

For on-premises installation, run the command:

```
./vendor/bin/magento-patches status
```

<u>Sample response</u>:

```
You can find more detailed information about patches on https://support.magento.com/
╔════════════════╤═════════════════════════════════════════════════╤══════════╤═════════════╤═════════════════════════════════╗
║ Id             │ Title                                           │ Type     │ Status      │ Details                         ║
╠════════════════╪═════════════════════════════════════════════════╪══════════╪═════════════╪═════════════════════════════════╣
║ MAGECLOUD-5069 │ FPC is getting disabled during deployments      │ Required │ Applied     │ Affected components:            ║
║                │                                                 │          │             │  - magento/module-page-cache    ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MCLOUD-5650    │ Hold deployment config after reading from file  │ Required │ Applied     │ Affected components:            ║
║                │                                                 │          │             │  - magento/framework            ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MCLOUD-5684    │ Pagination Not working - product_list_limit=all │ Required │ Applied     │ Affected components:            ║
║                │                                                 │          │             │  - magento/module-elasticsearch ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MC-65837       │ Fix load balancer issue                         │Deprecated│ Applied     │ Recommended replacement: MC-1   ║
║                │                                                 │          │             │ Affected components:            ║
║                │                                                 │          │             │  - magento/framework            ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ BUNDLE-2554    │ Set Payment info bug                            │ Required │ Not applied │ Affected components:            ║
║                │                                                 │          │             │  - amzn/amazon-pay-module       ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MC-1           │ Fixes issue 1                                   │ Optional │ Applied     │ Affected components:            ║
║                │                                                 │          │             │  - magento/module-cms           ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MC-2           │ Fixes issue 2                                   │ Optional │ Not applied │ Affected components:            ║
║                │                                                 │          │             │  - magento/module-cms           ║
╟────────────────┼─────────────────────────────────────────────────┼──────────┼─────────────┼─────────────────────────────────╢
║ MC-3           │ Fixes issue 3                                   │ Optional │ Not applied │ Required patches:               ║
║                │                                                 │          │             │  - MC-2                         ║
║                │                                                 │          │             │ Affected components:            ║
║                │                                                 │          │             │  - magento/module-cms           ║
╚════════════════╧═════════════════════════════════════════════════╧══════════╧═════════════╧═════════════════════════════════╝
Magento 2 Enterprise Edition, version 2.3.5.0
```

The status table contains the following types of information:

* **Type**:
    * `Optional`—All patches from the Quality Patches Tool are optional for Adobe Commerce and Magento Open Source installations.
    * `Required`—All patches from the Cloud Patches for Commerce package are required for Cloud customers.
    * `Deprecated`—The individual patch is marked as deprecated and we recommend [reverting](/revert-a-patch.md) it if you have applied it. After you revert a deprecated patch, it will no longer be displayed in the status table.
    * `Custom`—All patches from the `m2-hotfixes` directory.

* **Status**:
    * `Applied`—The patch has been applied.
    * `Not applied`—The patch has not been applied.
    * `N/A`—The status of the patch cannot be defined due to conflicts.

* **Details**:
    * `Affected components`—The list of affected modules.
    * `Required patches`—The list of required patches (dependencies).
    * `Recommended replacement`—The patch that is a recommended replacement for a deprecated patch.

### Related reading

* [[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)
* [Release notes](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)
