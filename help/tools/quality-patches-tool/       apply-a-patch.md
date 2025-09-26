---
title: Apply individual patches
description: Learn how to apply quality patches released with the [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
role: Admin, Developers
feature: Configuration, Install
type: Troubleshooting
---
# Apply individual patches

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) delivers optional quality fixes as individual patches to your installed Adobe Commerce application. 

To apply a patch, you need to have the tool installed in your Commerce environment. Refer to [Installing Quality Patches Tool](/install-quality-patches-tool.md) for steps specific to Adobe Commerce on-premises and on cloud infrastructures.

## Steps to apply quality patches

### For Adobe Commerce on-premises

1. Apply a single patch:
  
    1. Run the following command where ACSD-XXXX is the patch ID.

        ```
        ./vendor/bin/magento-patches apply ACSD-XXXX
        ```

    1. Clear the cache to see changes in your Adobe Commerce environment.

         ```
         ./bin/magento cache:clean
         ```

1. Apply multiple patches: 

    >[!WARNING]
    >
    >It is not recommended to use the [!DNL Quality Patches Tool] to apply large numbers of patches because it increases the complexity of your code and makes upgrading to a new version more difficult.

    1. Run the following command where patch IDs (ACSD-XXXX and ACSD-YYYY) are separated with a space.

        ```
        ./vendor/bin/magento-patches apply ACSD-XXXX ACSD-YYYY
        ```

    1. Clear the cache to see changes in your Adobe Commerce environment.

        ```
        ./bin/magento cache:clean
        ```

### For Adobe Commerce on Cloud infrastructure

1. Apply patches in your local environment:
   
    1. Add the `QUALITY_PATCHES` variable to the `.magento.env.yaml` file and list the required patches underneath.

       ```yaml
       stage:
         build:
           QUALITY_PATCHES:
             - ACSD-XXXXX
             - ACSD-YYYYY
        ```

    1. From the project root, apply the patches.

       ```bash
       php ./vendor/bin/ece-patches apply
       ```

       The `ece-patches apply` command applies patches in the following order:
       
       * Required patches
       * Optional quality patches
       * Custom patches from the `/m2-hotfixes` directory

    1. Clear the cache.

       ```bash
       php ./bin/magento cache:clean
       ```

1. Apply patches in a remote environment

    >[!WARNING]
    >
    >It is recommend to test all patches in Staging environment before deploying to the Production environment.

    1. Add the `QUALITY_PATCHES` variable to the `.magento.env.yaml` file and list the required patches underneath.

       ```yaml
       stage:
         build:
           QUALITY_PATCHES:
             - MCTEST-1002
             - MCTEST-1003
       ```

    1. Add, commit, and push the updated `.magento.env.yaml` file.

       ```bash
       git add .magento.env.yaml
       ```

       ```bash
       git commit -m "Apply patch"
       ```

       ```bash
       git push origin <branch-name>
       ```

## Steps to re-apply patches after an upgrade

When you upgrade to a new version of Adobe Commerce, you must re-apply the patches that are not included in the new version. The best practice is to apply patches one at a time.

To re-apply patches:

1. Update the [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Open the list of previously applied patches. Refer to [View applied patches]().

1. Apply the patches:

   ```bash
   ./vendor/bin/magento-patches apply ACSD-XXXX
   ```

1. Clean the cache:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >When you run the `status` command, the patches that were included in the new version are no longer displayed in the table of available patches.

## Apply latest patch fixes

Adobe Commerce periodically releases new individual patches. Update to the latest version of [!DNL Quality Patches Tool] to get new individual patches:

```bash
composer update magento/quality-patches
```

View the added patches:

```bash
./vendor/bin/magento-patches status
```

>[!TIP]
>
>Newly add patches display at the bottom of the table.

## Related reading

[Revert a quality patch](/revert-a-patch.md)
