---
title: Revert a quality patch with [!DNL Quality Patches Tool] 
description: Learn how to revert previously applied quality patches with [!DNL Quality Patches Tool]. 
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
---
# Revert a quality patch with [!DNL Quality Patches Tool]

You can revert all previously applied patches or selective patches to safely roll back changes if they cause issues, are no longer needed, or conflicts with your Adobe Commerce version.

## Steps to revert quality patches

### For Adobe Commerce on-premises

1. To revert a single patch:
   
   1. Run the following command where `ACSD-XXXX` is the patch ID:

      ```bash
      ./vendor/bin/magento-patches revert ACSD-XXXX
      ```

    1. Clear the cache to see changes in your Adobe Commerce application.

       ```bash
       ./bin/magento cache:clean
       ```

1. To revert multiple patches at once:
  
   1. Run the following command with patch IDs separated by a space:

      ```bash
      ./vendor/bin/magento-patches revert ACSD-XXXX ACSD-YYYY
      ```

    1. Clear the cache.

       ```bash
       ./bin/magento cache:clean
       ```

1. To revert all applied patches:

   1. Run the following command:

      ```bash
      ./vendor/bin/magento-patches revert --all
      ```

    1. Clear the cache.

       ```bash
       ./bin/magento cache:clean
       ```

### For Adobe Commerce on Cloud infrastructure

Use the `ece-patches` CLI to revert all applied patches:

```bash
php ./vendor/bin/ece-patches revert
```
