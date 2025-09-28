---
title: '[!DNL Quality Patches Tool]: A self-service tool for quality patches'
description: '[!DNL Quality Patches Tool] allows you to apply, revert, and view general information about quality patches available for your installed version of Adobe Commerce (both on-premises and on cloud infrastructure).'
feature: Tools and External Services
role: Admin, Developer
exl-id: a83d3834-841d-4b90-b40a-fda985a85452
---
# [!DNL Quality Patches Tool]: A self-service tool for quality patches

[!DNL Quality Patches Tool(QPT)] is a self-service command line tool that allows you to apply, revert, and view general information about quality patches for Adobe Commerce (both on-premises and on cloud infrastructure).

These patches fix known issues and bugs to improve the stability, security, and performance of your Adobe Commerce implementation. 

>[!NOTE]
>
>You should use the tool to pull in necessary quality fixes as needed on a case-by-case basis only and not as a long-term approach to maintaining Adobe Commerce and Magento Open Source code. Upgrading to the latest version of Adobe Commerce or Magento Open Source is still the best method for resolving quality issues and should be prioritized.

## When to use [!DNL Quality Patches Tool]

The [!DNL Quality Patches Tool] (QPT) is recommended when you need to apply a targeted fix to a known issue in Adobe Commerce without modifying core files.

<details><summary><b>Use the QPT when</b></summary>

* A patch is available that matches the specific error or issue you are experiencing.
* You need to apply a small, isolated fix without introducing larger system changes.
* You require the option to revert a patch if it causes unexpected behavior.
* You want to manage optional fixes separately from mandatory Cloud patches.
  
  >[!NOTE]
  >
  >The Cloud Patches for Commerce package delivers required patches with critical fixes. Whereas, Quality Patches deliver optional, low-impact quality fixes as individual patches that do not contain backward incompatible changes. Refer to [Apply cloud patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) in the Commerce on Cloud guide for more information.
</details>

<details><summary><b>Avoid using the QPT when</b></summary>

* Multiple patches are required, which can complicate future upgrades.
* You are in a cloud environment and need critical fixes, which should come via Cloud Patches for Commerce, not Quality Patches. 
* A patch has dependencies or compatibility issues with your version or customizations.
* You are deploying directly to production without first testing in a staging environment.

</details>

## Related reading

* [Installing [!DNL Quality Patches Tool]](https://github.com/nayanika237/commerce-operations.en/blob/main/help/tools/quality-patches-tool/%20%20%20%20%20%20%20%20install-quality-patches-tool.md)
* [[!DNL Quality Patches Tool] release notes](https://github.com/nayanika237/commerce-operations.en/blob/main/help/tools/quality-patches-tool/release-notes.md)
