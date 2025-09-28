---
title: 'Install [!DNL Quality Patches Tool]'
description: 'Learn how to install the [!DNL Quality Patches Tool] to self-serve bug fixes in your Adobe Commerce implementation.'
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
exl-id: a83d3834-841d-4b90-b40a-fda985a85452
---
# Install [!DNL Quality Patches Tool (QPT)]

Adobe Commerce periodically releases new individual patches. Install [!DNL Quality Patches Tool] or update to the latest version to get new individual patches. 

See [[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) for a complete list of released patches and their supported Adobe Commerce versions.

## Installing [!DNL Quality Patches Tool]

### Pre-requisites

* Request administrator access to your Adobe Commerce project.  
* Install [Git](https://git-scm.com/downloads) and [Patch](https://man7.org/linux/man-pages/man1/patch.1.html), if not already available on your system.   
* For on-premises installations, set up [Composer authentication keys](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) to download packages from repo.magento.com.  
* For cloud users, confirm that the lastest [ece-tools](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools-package) package is installed. The minimum required version of ECE-Tools is 2002.1.2. 

### For Adobe Commerce on-premises 

1. Install the QPT package using [Composer](https://getcomposer.org/).

    ```bash
    composer require magento/quality-patches
    ```

1. Verify the supported commands:

    ```bash
    vendor/bin/magento-patches --help
    ```

### For Adobe Commerce on cloud infrastructures

QPT is included with the `ece-tools` package. No additional installation is required.

Verify that QPT is available:

```
php ./vendor/bin/ece-patches --help
```

### Related reading

* [View individual patches](https://github.com/nayanika237/commerce-operations.en/blob/main/help/tools/quality-patches-tool/%20%20%20%20%20%20%20%20view-all-patches.md)
* [Apply individual patches](https://github.com/nayanika237/commerce-operations.en/blob/main/help/tools/quality-patches-tool/%20%20%20%20%20%20%20apply-a-patch.md)
