---
group: release-notes
title: Magento Commerce 2.4.1 Release Notes
---

Magento Commerce 2.4.1 introduces enhancements to performance and security plus significant additions to the B2B feature set. Security enhancements include support for the `SameSite` attribute for cookies and the addition of CAPTCHA protection for payment-related and order-related API endpoints and the Place Order storefront page. B2B improvements focus on the order approval process, B2B shipping methods, expanded logging of Admin actions, and enhanced security on storefront.

This release includes all improvements to core quality that were included in Magento 2.4.0, over 150 new fixes to core code, and over 15 security enhancements. It includes the resolution of almost 300 GitHub issues by our community members. These community contributions range from minor clean-up of core code to significant enhancements in GraphQL.

All known issues identified in Magento 2.4.0 have been fixed in this release.

{:.bs-callout-info}

Quarterly releases may contain backward-incompatible changes (BIC). Magento 2.4.1 contains minor backward-incompatible changes. To review minor backward-incompatible changes, see [BIC reference]({{page.baseurl}}/release-notes/backward-incompatible-changes/reference.html). (Major backward-incompatible issues are described in [BIC highlights]({{page.baseurl}}/release-notes/backward-incompatible-changes/index.html). Not all releases introduce major BICs.)

## Security-only patch available

Merchants can now install time-sensitive security fixes without applying the hundreds of functional fixes and enhancements that a full quarterly release (for example, Magento 2.4.0-p1) provides. Patch 2.4.0.1 (Composer package 2.4.0-p1) is a security-only patch that provides fixes for vulnerabilities that have been identified in our previous quarterly release, Magento 2.4.0. All hot fixes that were applied to the 2.4.0 release are included in this security-only patch. (A *hot fix* provides a fix to a released version of Magento that addresses a specific problem or bug.)

For general information about security-only patches, see the Magento DevBlog post [Introducing the New Security-only Patch Release](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287). For instructions on downloading and applying security-only patches (including patch 2.3.5-p2), see [Install Magento using Composer]({{page.baseurl}}/install-gde/composer.html). Security-only patches include security bug fixes only, not the additional security enhancements that are included in the full patch.

## Other release information

Although code for these features is bundled with quarterly releases of the Magento core code, several of these projects (for example, B2B, Page Builder, and Progressive Web Applications (PWA) Studio) are also released independently. Bug fixes for these projects are documented in the separate, project-specific release information that is available in the documentation for each project.

## Highlights

Look for the following highlights in this release.

### Substantial security enhancements

This release includes over 15 security fixes and platform security improvements. All security fixes have been backported to Magento 2.4.0-p1 and Magento 2.3.6.

#### Over 15 security enhancements that help close remote code execution (RCE) and cross-site scripting (XSS) vulnerabilities

No confirmed attacks related to these issues have occurred to date. However, certain vulnerabilities can potentially be exploited to access customer information or take over administrator sessions. Most of these issues require that an attacker first obtains access to the Admin. As a result, we remind you to take all necessary steps to protect your Admin, including but not limited to these efforts: IP allowlisting, [two-factor authentication]({{page.baseurl}}/security/two-factor-authentication.html), use of a VPN, the use of a unique location rather than `/admin`, and good password hygiene. See _Security Updates Available for Magento_ for a discussion of these fixed issues.

#### Additional security enhancements

Security improvements for this release include:

*  **CAPTCHA** protection has been added to the following product areas:

   *  Place Order storefront page and REST and GraphQL endpoints <!--- MC-36067-->
   *  Payment-related REST and GraphQL endpoints.<!--- MC-36064-->

   CAPTCHA protection for these additional pages is disabled by default. It can be enabled on the Admin in the same way that other pages covered by CAPTCHA are. This protection has been added as an anti-brute force mechanism to protect stores against carding attacks.

*  **Support for the SameSite attribute for cookies**. To support the Google Chrome enforcement of the new cookie classification system, Magento classes that handle cookies have been updated to support the `SameSite` cookie attribute. This attribute is set to `Lax` by default but can be explicitly overridden. <!--- MC-35389-->

*  **Enhanced Magento Scan Tool**. Adobe has partnered with [Sanguine Security](https://sansec.io/), a leader in preventing digital skimming, to integrate their database of over 8700 threat signatures into the Magento Security Scan Tool. This partnership will enable merchants to get real-time insights into the security status of their site through proactive detection of malware and reduction of false positives. Merchants can register for the tool by visiting https://account.magento.com/scanner. For more information, see the [Secure Your Storefront With the Enhanced Magento Security Scan Tool](https://magento.com/blog/magento-news/secure-your-storefront-enhanced-magento-security-scan-tool) blog post.

{:.bs-callout-info}
Starting with the release of Magento Commerce 2.3.2, Magento will assign and publish indexed Common Vulnerabilities and Exposures (CVE) numbers with each security bug reported to us by external parties. This allows users of Magento Commerce to more easily identify unaddressed vulnerabilities in their deployment. You can learn more about CVE identifiers at [CVE](https://cve.mitre.org/).

### Infrastructure improvements

This release contains enhancements to core quality, which improve the quality of the Framework and these functional areas: Customer Account, Catalog, CMS, OMS, Import/Export, Promotions and Targeting, Cart and Checkout, B2B, and Staging and Preview.

*  **Site-Wide Analysis Tool (SWAT) integration with Magento Admin**. (SWAT) provides system insights and instrumentation for Commerce Cloud installations of Magento with 24/7 real-time performance monitoring, reports, and self-service recommendations. Merchants can use the new SWAT Admin role to securely access their SWAT Customer Detail pages through the Magento Admin. For more information, see [SWAT FAQ](https://support.magento.com/hc/en-us/articles/360048646671).<!--- SWAT-807-->

### Performance improvements

*  **Reduction in the size of network transfers between Redis and Magento**. Plugin list configuration is now generated during the execution of the `di:compile` command. This configuration information is written to generated metadata folders based on scope. Previously, this information was stored in cache. Resulting performance improvements include:

   *  Network cache size has decreased by 10 - 15%
   *  Execution time for many scenarios has been improved by 3%<!--- MC-31617-->

*  **Improved execution time** for `bin/magento` commands.

### Adobe Stock Integration

This release includes Adobe Stock Integration v2.1.0.

### New Media Gallery

The New Media Gallery is now enabled by default in the Admin. Merchants can now perform these actions on images in the Media Gallery:

*  Delete images in bulk
*  Optimize media storage by identifying duplicate images and images that are not used on the storefront
*  Filter images by the storefront area they are used in, including product and category content and CMS blocks
*  Work with image metadata
   *  View metadata from the images uploaded into Media Gallery
   *  Edit image metadata (title, description, and keywords)
   *  Search for images by their metadata

### Page Builder

Page Builder now supports full screen mode, which supports easier editing of content and provides a consistent experience editing content across the Admin. <!--- PB-543-->

### GraphQL

This release adds GraphQL coverage for the following features:

*  **Product reviews**. Customers and guests can write product reviews. Customers can retrieve their product review histories.<!--- MC-32349-->

*  **Gift options**. All customers and guests can add a gift message to their order. On {{site.data.var.ee}}  installations, they can also add gift wrapping, gift receipts, and printed cards to the order.<!--- MC-32345-->

*  **Reward points**. On {{site.data.var.ee}} installations, customers can apply or remove reward points to their carts. They can also view their reward point history.<!--- MC-23366-->

*  **Order history**. All customers can view details about their order histories, including invoices, shipping, and refunds.<!--- MC-20635-->

*  **Add to cart**. Customers can add the following product types to their cart:  Simple, Configurable, Bundled, Grouped, Virtual, Gift Card, and Downloadable. <!--- MC-21513-->

*  **Stored payment methods**. Logged-in customers can now store payment details (including Braintree credit card and Braintree with PayPal) in MyAccount. <!--- MC-32348 35945 35946-->

See the [GraphQL Developer Guide]({{page.baseurl}}/graphql/) for details on this and other enhancements.

### PWA Studio

PWA Studio v8.0.0 introduces new features and enhancements:

*  Updates to the Venia style guide that apply to design tokens, typography, colors, core components, and page layouts. <!--- PWA-519 419-->

*  Improvements to the Venia mini-cart experience <!--- PWA-236-->

*  Initial support for multiple locales and localized content on the Venia storefront <!--- PWA-295-->

*  Numerous improvements to the MyAccount experience of the Venia storefront <!--- PWA-247-->

See [Magento compatibility](https://magento.github.io/pwa-studio/technologies/magento-compatibility/) for a list of PWA Studio versions and their compatible Magento core versions. For information about enhancements and bug fixes, see [PWA Studio releases](https://github.com/magento/pwa-studio/releases).

### B2B

Magento 2.4.1 introduces B2B v1.3.0. This release includes improvements to order approvals, shipping methods, shopping cart, and logging of Admin actions.

#### Improvements to Order Approvals

B2B order approvals have been enhanced to improve usability and to allow for bulk actions on purchase orders.
Improvements to order approval and rejection include the following:

*  **New View Rule page for users without edit privileges**. B2B buyers can now view rules that apply to their company on the new View Rule page when they do not have permission to edit them. <!--- BUNDLE-104 -->

*  **Count alert icon on the Requires My Approval tab**. The Requires My Approval tab in the My Purchase Orders view now displays a counter that indicates the number of pending approval actions. <!--- BUNDLE-102 -->

*  **Bulk order approvals and rejections**. B2B managers and Company Administrators can now perform bulk rejection and approval of purchase orders. These changes allow approvers to approve or reject multiple purchase orders in a single action. <!--- BUNDLE-140 128 111 153 -->

*  Merchants can now search the **Applies to** and **Requires approval from** fields of the My Purchase Orders view and can select multiple user roles during rule creation. <!--- BUNDLE-105 106-->

*  Examples of how to configure Order Approval rules <!--- BUNDLE-103 -->

#### B2B shipping methods enhancements

B2B merchants can now control shipping methods that are offered to each Company. Merchants can configure the following from the Admin:<!--- BUNDLE-160 161 162 -->

*  A specific set of shipping methods for B2B Company accounts
*  The use of All or B2B-specific shipping methods for each Company account
*  A specific list of B2B shipping methods for each Company account

#### Shopping cart improvements

*  Merchants can now allow users to clear the contents of their shopping cart in a single action and can configure this ability independently on each website <!--- BUNDLE-108 -->

*  B2B buyers can now add individual items or the entire contents of their shopping cart directly to a requisition list. <!--- BUNDLE-145 144-->

#### New Admin features

*  B2B merchants can create orders from the Admin on behalf of customers using Payment on Account as the payment method. <!--- BUNDLE-166 178-->

*  Merchants can now directly view all quotes associated with a user from the customer’s detail page. <!--- BUNDLE-139 -->
*  Merchants can now filter the Company Customers table by Company. <!--- BUNDLE-137 -->

*  Admins can now filter customers in the Admin by Sales Rep. <!--- BUNDLE-110 -->

#### Enhanced security on storefront

To reduce creation of fraudulent or spam accounts, merchants can now enable Google reCAPTCHA on the New Company Request form on the storefront. <!--- BUNDLE-154 -->

#### Expanded logging of Admin actions

Admin actions taken in the Company modules are now logged in the Admin Actions Log. Actions are logged from all relevant company modules: `Company`, `NegotiableQuote`, `CompanyCredit`, `SharedCatalog`.  <!--- BUNDLE-180 181 182 183 -->

This release also includes multiple bug fixes. See [B2B Release Notes]({{page.baseurl}}/release-notes/b2b-release-notes.html).

### Magento Functional Testing Framework (MFTF)

MFTF 3.1.0 is now available. See [Magento Functional Testing Framework Changelog](https://github.com/magento/magento2-functional-testing-framework/blob/develop/CHANGELOG.md).

## Fixed issues

We have fixed hundreds of issues in the Magento 2.4.1 core code.

### Installation, upgrade, deployment

<!--- MC-36113-->

*  Installation of Magento with third-party extensions that have dependencies on APIs for the Store module in CLI commands no longer fails. Previously, Magento displayed this error message: `The default website isn't defined. Set the website and try again`. This was a known issue in Magento 2.4.0.

<!--- MC-33273-->

*  `bin/magento setup:di:compile` no longer throws a fatal error. Previously, Magento threw an error the first time you ran this command, but the second execution resulted in successful compilation.

<!--- MC-34429-->

*  Upgrade no longer fails when a plugin is declared on `Magento\Framework\Encryption\Encryptor`.

<!--- MC-36231-->

*  Magento now displays an informative error message when some themes are not deployed after running `setup:static-content:deploy`. Previously, when deployment completed successfully but not all packages were deployed, Magento did not display an error. When the `setup:static-content:deploy` command is executed with enabled parallel processing and each theme requires more time to be deployed than the specified maximum execution time, this command can finish successfully although themes are not deployed.

<!--- MC-35001-->

*  The **Use default** checkbox for Klarna payments (**Stores** > **Configuration** > **Sales** > **Payment methods** > **Klarna**) now remain checked as expected when website scope changes.

<!--- MC-17959-->

*  Running `/bin/magento config:show vendor_module/general/value` now returns `0` or an empty string as expected. Previously, it returned `Configuration for path: "vendor_module/general/value" doesn't exist`. [GitHub-23290](https://github.com/magento/magento2/issues/23290)

<!--- MC-33788-->

*  Upgrade no longer results in the sudden failure of the Galera cluster. Previously, the Galera cluster exited abruptly after re-indexing immediately after upgrade. During Magento upgrade, index tables are altered and the engine is changed from MEMORY to InnoDB. At this point, the content of these tables becomes out-of-sync between the nodes of the Galera cluster. [GitHub-25334](https://github.com/magento/magento2/issues/25334)

<!--- ENGCOM-7219-->

<!--- ENGCOM-7459-->

<!--- ENGCOM-7265-->

<!--- ENGCOM-7508-->

<!--- ENGCOM-7800-->

<!--- ENGCOM-7629-->

<!--- ENGCOM-7776-->

<!--- ENGCOM-7853-->

<!--- ENGCOM-7883-->

<!--- ENGCOM-8006-->

<!--- ENGCOM-8020-->

<!--- ENGCOM-7987-->

### AdminGWS

<!--- MC-36164-->

*  Magento no longer displays the **Add Attribute** button (**Stores** > **Attributes** ) or **Add Attribute Set** button (**Stores** > **Attributes** > **Customer** ) when the logged-in administrator lacks the appropriate permissions to create these entities. Previously, Magento threw a 404 error when a website administrator who did not have the appropriate permissions tried to create an **Attribute Set** or **Customer** attribute.

<!--- MC-36330-->

<!--- MC-36230-->

*  Magento no longer throws an error when an administrator with restricted roles for specific websites tries to create a subcategory from the Admin.

### Analytics

<!--- MC-33314-->

<!--- MC-34352-->

*  Magento successfully generates advance reporting data files and sends them as expected to Inventory on deployments with split databases. Previously, Magento did not generate or send the `quotes.csv` file to Inventory, and as a result, Inventory did not generate the expected reports.

### Bundle products

<!--- MC-36281-->

*  Magento no longer throws an exception when you try to create a product in a deployment in which MSI is installed but the `Magento_InventoryBundleProduct` module is disabled.

<!--- MC-34261-->

*  Magento now correctly calculates offline refunds for orders that contain bundle products.

<!--- MC-29908-->

<!--- ENGCOM-7499-->

<!--- ENGCOM-7655-->

<!--- ENGCOM-7985-->

### Cache

<!--- MC-36096-->

*  Local cache storage is now retained for the period of time set in **Stores** > **Configuration** > **General** > **Web** > **Default Cookie Settings**. Previously, the expiry date of cookies was hardcoded to one day, which put it out of sync with this setting. As a result, welcome messages did not retain returning customer information for the expected duration.

<!--- ENGCOM-7780-->

<!--- ENGCOM-7073-->

<!--- ENGCOM-8019-->

### Cart and checkout

<!--- MC-36252-->

<!--- MC-35329-->

*  The **Delete** button on the **Add to Shopping Cart by SKU** section of a customer’s **Manage Shopping Cart** page now works as expected when multiple rows are selected.

<!--- MC-34999-->

*  Magento no longer throws an error when you try to order a product by SKU when the digits you enter match a valid SKU but the case of these digits differ. Previously, when you entered an SKU on My **Account** > **Order by SKU** that did not exactly match a valid SKU, Magento threw an error.

<!--- MC-25042-->

*  A customer’s shipping address is now selected by default at checkout when the address is located in the country identified on the Allow Countries list and that list includes only that country. Previously, Magento did not select the address as default and displayed this error message: `Please specify a regionId in shipping address`.

<!--- MC-24043-->

*  Merchants can now enable **Apply to Shipping Amount** in the Action tab of **Marketing** > **Cart Price Rules** > **Add New Rule** when **Fixed amount discount for whole cart** is applied. [GitHub-24422](https://github.com/magento/magento2/issues/24422)

<!--- MC-23992-->

<!--- MC-33899-->

*  Magento now displays an add-to-cart success message when a customer adds an out-of-stock product to their cart. Previously, the product was added, but Magento did not display a success message.

<!--- MC-35989-->

*  Custom address attributes are now included as expected in the the form that displays for the payment step in the checkout workflow.

<!--- MC-36060-->

*  The **State/Province/Region** input box is now enabled as expected on **My account** > **Address Book** > **Add new address**.

<!--- ENGCOM-7746-->

<!--- ENGCOM-7752-->

<!--- ENGCOM-7585-->

<!--- ENGCOM-7457-->

<!--- ENGCOM-5629-->

<!--- ENGCOM-7949-->

<!--- ENGCOM-7968-->

<!--- ENGCOM-7976-->

<!--- ENGCOM-7976-->

<!--- ENGCOM-7976-->

<!--- ENGCOM-7976-->

<!--- ENGCOM-7976-->

<!--- ENGCOM-8019-->

<!--- ENGCOM-7825-->

<!--- ENGCOM-8004-->

<!--- ENGCOM-7950-->

<!--- MC-36418-->

*  Magento now displays a customer registration form when a guest user completes checkout.

<!--- MC-35607-->

### Catalog

<!--- MC-25062-->

<!--- ENGCOM-7292-->

<!--- ENGCOM-7563-->

<!--- ENGCOM-7513-->

<!--- ENGCOM-7420-->

<!--- ENGCOM-7976-->

<!--- MC-34314-->

*  Magento now uses the default option (**Configuration** > **Web** > **Default Layouts** > **Default Product Layout**) that you have selected for the `page_layout` attribute when creating a new product. Previously, your selected default value was not applied.

<!--- MC-34258-->

*  You can now successfully perform mass actions on Inventory product stock. Previously, when you tried to perform a mass action on inventory product stock, Magento displayed a blank page. If you performed this action with Magento in developer mode, Magento threw this error: `Notice: Undefined offset: 32000 in /Users/kodithuw/sites/m23inventory/inventory/InventoryCatalogAdminUi/view/adminhtml/templates/catalog/product/edit/action/inventory.phtml on line 24`

<!--- MC-32552-->

*  The total record count displayed when you click **Add Products** on the Products tab when adding products to a catalog category no longer changes based on product sort order.

### CMS content

<!--- MC-35971-->

*  The Hierarchy tab for a selected default store view now displays the selected parent page as expected.

<!--- ENGCOM-7600-->

<!--- ENGCOM-7602-->

<!--- MC-35480-->

### Configurable products

<!--- ENGCOM-7214-->
<!--- ENGCOM-7787-->
<!--- MC-33523-->

*  Pagination problems with the Configurable Product Edit Current Variations list have been corrected.

<!--- MC-33406-->

<!--- MC-29882-->

*  Magento now displays the correct price for configurable products with customizable options on the Admin Create Order page. As expected, the displayed price is a sum of the child product's price and the custom option's price. Previously, Magento displayed only the custom option price. [GitHub-25766](https://github.com/magento/magento2/issues/25766)

<!--- MC-33745-->

*  Order summary now displays the correct discount amount when a cart price rule has been applied. Previously, the rule did not correctly round amounts when calculating shipping discounts.

<!--- MC-33765-->

*  Admin user accounts created from an admin account with a restricted scope can now create a configurable product with attributes as expected. Previously, Magento threw this error: `Notice: Undefined index: value_index in 23develop/app/code/Magento/ConfigurableProduct/Helper/Product/Options/Factory.php on line 101`.

### Custom customer attributes

<!--- MC-36387-->

*  Corrected alignment issues for the explanatory text about passwords and the **Job Title** field on the Customer Edit Account Information page.

<!--- MC-33645-->

<!--- MC-34024-->

*  The checkout workflow no longer displays custom customer address attribute values when the customer has not entered any data.

### Customer

<!--- MC-33679-->

*  The region names in Admin customer addresses are now translated as expected.

<!--- ENGCOM-7793-->
<!--- MC-36226-->

*  The **State/Province** fields are now populated as expected on the Edit Address page (**My Account** > **Address book**).

<!--- MC-34655-->

*  Magento no longer throws an error when a customer clicks the **Submit** button multiple times on forms throughout the storefront for which invisible reCAPTCHA has been enabled. Previously, clicking this button multiple times resulted in an internal error similar to this: `Internal error: Make sure you are using reCaptcha V3 api keys`.

<!--- MC-33522-->
<!--- MC-33357-->
<!--- MC-33150-->
<!--- MC-35655-->

*  Magento no longer displays the **Delete customer** button on the **Customers** page when the logged-in administrator does not have permission to delete customers in deployments where B2B is installed.

### Customer segment

<!--- MC-33184-->
<!--- MC-36224-->

*  Customer segment conditions now work as expected in a split-database deployment. Previously, Magento threw an error when you tried to edit a customer segment by adding a condition: `SQLSTATE[42S02]: Base table or view not found`

### Directory

<!--- MC-32271-->

*  The format of the State/Province drop-down menu is now consistent across the Admin.

### Downloadable

<!--- MC-29905-->

<!--- MC-35026-->

*  The My Downloadable Products area now displays links to purchased downloadable products that are part of a grouped product as expected.

<!--- MC-34262-->

*  Clicking on a downloadable product's **Sample** button from the Admin product page now downloads a sample as expected. Previously, when you clicked **Sample**, Magento displayed this error: `The product that was requested doesn't exist. Verify the product and try again`.

<!--- ENGCOM-7757-->

<!--- ENGCOM-7796-->

### Dynamic block (formerly banner)

<!--- MC-33266-->

*  Table title now matches the data table (as expected) when you create a dynamic block and add a related catalog price rule.

<!--- MC-33286-->

### Email

<!--- MC-32789-->

*  Magento now sends email notifications about order changes to the correct customer email if the customer email was changed after the order was created.

<!--- MC-36015-->

*  Order update emails that are sent to customers now include the correct order status. Previously, if an order status changed from `processing` to another state, the order email did not reflect the status change.

<!--- MC-34107-->

*  Magento no longer displays misleading messages about existing accounts during guest checkout. Previously, when a guest navigated to the checkout page, then navigated back to the shipping page, Magento displayed this error: `You already have an account with us. Sign in or continue as guest`.

<!--- MC-33905-->

*  Custom email templates now load the same elements as native default email templates. Previously, some elements, including variable values, were missing.

<!--- MC-33700-->

<!--- ENGCOM-7576-->

<!--- ENGCOM-7177-->

<!--- ENGCOM-7506-->

<!--- ENGCOM-7815-->

<!--- MC-33232-->

### Frameworks

<!--- MC-35893-->

*  The **Time of day to send data** field of the Admin **Stores** > **Configuration** > GENERAL > **Advanced Reporting** page is now rendered correctly.

<!--- MC-34153-->

*  Shoppers can now change the number of orders that are displayed per page when the Orders list spans multiple pages. Previously, Magento displayed this message when you navigated to the last page of orders and attempted to change the number of orders displayed per page: `You have placed no orders`. This was a known issue for Magento 2.4.0.

<!--- MC-35020-->

*  You can now add products to a category when implementing Level 2 cache.

<!--- MC-29755-->

*  `X-Magento-Tags` headers no longer exceed the size permitted by the HTTP specification. Previously, category pages that contain many products returned an `X-Magento-Tag` header that resulted in a 503 error.

<!--- MC-34257-->

*  `sales_order_shipment_track_save_commit_after` is now triggered as expected when you use REST to create a shipment.

<!--- MC-33898-->

*  Magento now displays an informative error message when a `di compile` fails due to a nonexistent dependency. Previously, the message displayed did not identify the class in which the exception occurred.

<!--- MC-32929-->

*  Magento no longer throws the following fatal error when Redis uses all allowed memory: `report.CRITICAL: OOM command not allowed when used memory > 'maxmemory'.`

### General fixes

<!--- MC-36048-->

*  Sorting products on the Admin (**Stores** > **Attributes** > **Products**) now displays all products that meet your search criteria. Previously, Magento did not display records, and to sort the records, you needed to navigate to the first page of search results.

<!--- MC-36343-->

*  Unnecessary quotation marks and escaping around a URL in `tracking.phtml` have been removed.

<!--- MC-35998-->

*  The `var/log/system.log` now displays a more accurate message when a user tries to access non-existing resource files under the static directory when SCD OnDemand and production mode are enabled. Previously, Magento logged the same message that is logged when the error occurs in developer mode. Magento now logs a 404 error.

<!--- ENGCOM-7286-->

<!--- ENGCOM-7532-->

<!--- ENGCOM-7577-->

<!--- ENGCOM-7591-->

<!--- ENGCOM-7447-->

<!--- ENGCOM-7299-->

<!--- ENGCOM-7193-->

<!--- ENGCOM-7610-->

<!--- ENGCOM-7565-->

<!--- ENGCOM-7682-->

<!--- ENGCOM-7514-->

<!--- ENGCOM-7588-->

<!--- MC-33744-->

<!--- ENGCOM-7511-->

<!--- ENGCOM-7462-->

<!--- ENGCOM-7729-->

<!--- ENGCOM-7810-->

<!--- ENGCOM-7801-->

<!--- ENGCOM-7816-->

<!--- ENGCOM-7724-->

<!--- ENGCOM-7844-->

<!--- ENGCOM-7834-->

<!--- ENGCOM-7854-->

<!--- ENGCOM-7826-->

<!--- ENGCOM-7147-->

<!--- ENGCOM-7868-->

<!--- ENGCOM-7867-->

<!--- ENGCOM-7881-->

<!--- ENGCOM-7857-->

<!--- ENGCOM-7856-->

<!--- ENGCOM-7999-->

<!--- ENGCOM-7962-->

<!--- MC-35550-->

<!--- MC-35230-->

*  Password lifetime as set in **Stores** > **Configuration** > **Advanced** > **Admin** is now honored. Previously, if you clicked **Forgot password?** when prompted to reset your password, you could bypass the password reset.

<!--- MC-34369-->

*  Coupon codes are now applied only to the specified product. Previously, Magento applied the coupon code to all products in the cart. [GitHub-28246](https://github.com/magento/magento2/issues/28246)

### Gift cards

<!--- ENGCOM-7661-->

<!--- MC-36118-->

*  Gift Card Accounts now capture order numbers as expected. Previously, the **More information** field in the History tab for the selected gift account did not display order IDs.

<!--- MC-34519-->

*  Using a comma as a decimal separator now works as expected. Previously, the comma separator ignored decimal values.

<!--- MC-34469-->

*  Gift cards are now displayed as expected in the mini cart. Previously, Magento rendered HTML objects as text.

<!--- MC-33851-->

*  Credit memos now correctly reflect the grand total for orders that involved discounted products and that were paid for by a combination of git card and store credit.

### Google Tag Manager

<!--- MC-33729-->

*  Magento no longer throws a JavaScript error during checkout when the **Cookie Restriction Mode** setting and Google Tag Manager are enabled.

### Import/export

<!--- MC-35479-->

*  The `error_report.csv` file now downloads with content and is available inside the `var/import_history/` directory as expected. Previously, this file was not generated after import.

<!--- ENGCOM-7616-->

<!--- ENGCOM-7673-->

<!--- ENGCOM-7995-->

<!--- MC-33730-->

*  Magento now successfully imports customer addresses that contain a region for a country that does not have defined regions. Previously, Magento threw this error: `Please enter a valid region`.

<!--- MC-33277-->

*  Magento now loads the correct Entity Attributes set when a merchant selects an Entity Type when scheduling a new export.

<!--- MC-32956-->

*  The position of products in the `catalog_category_product` table now update as expected when an administrator creates a product in the Admin and assigns it to a category. Previously, the position of new products was always assigned a 0 value.

<!--- MC-34939-->

*  Customer data is now successfully exported from the Admin, and the export data grid displays customer data as expected. Previously, an error related to memory allocation occurred during export.

<!--- MC-34657-->

*  Imported `.cvs` files now capture related product information as expected. Previously, related product information was not consistently uploaded the first time the `.cvs` file was imported.

### Index

<!--- ENGCOM-7776-->

<!--- ENGCOM-7073-->

<!--- MC-39468-->

<!--- MC-30568-->

*  Shared indexers now show a status of **valid** after you run `bin/magento indexer:status` after re-indexing. Previously, shared indexers had an **invalid** status after a full re-index.

### Layered navigation

<!--- MC-25043-->

*  The layered navigation sidebar now shows Boolean attributes with both options (**yes**/**no**) and matching product counts. Previously, layered navigation did not return a **no** option for Boolean attributes in deployments using Elasticsearch.

<!--- ENGCOM-7493-->

### Newsletter

<!--- MC-34714-->

*  Exporting the Newsletter Subscribers list using the `EXCEL XML` option now results in all rows being exported as expected. Previously, exported data included only the page pagination value (`EXCEL XML` option), not all rows.

<!--- ENGCOM-7522-->

<!--- ENGCOM-7788-->

<!--- ENGCOM-7739-->

### Payment methods

<!--- MC-34363-->

*  Magento now displays a message that prompts you to enter mandatory credit card data when you click **Submit** for an Admin order without entering valid payment information. Previously, the Braintree card validator did not throw an error when payment input fields were invalid and the page became inactive.

<!--- MC-33494-->

*  You can now change the shipping method for an order you create from the Admin for a customer whose account has a stored credit card (Braintree). Previously, when you selected a different shipping method, the stored card was not selected, and Magento did not place the order.

#### PayPal

<!--- MC-33879-->

*  The Order Review page of the checkout workflow now displays the correct shipping amount for PayPal through Braintree orders for which the shipping method has been changed during checkout. Previously, when a customer changed the shipping method on the PayPal Order Review page of the checkout workflow, Magento did not update the order total with the correct method.

<!--- MC-34152-->

*  Merchants can now successfully cancel orders that were authorized using PayPal. Previously, Magento did not cancel the order and displayed this error:  `Declined: 10601-Authorization has expired`.

<!--- MC-33330-->

*  Magento no longer empties your cart when you cancel an order by closing the PayPal payment popup window after first completing another order.

### Performance

<!--- MC-31617-->

*  Plugin list configuration is now generated during the execution of the `di:compile` command. This configuration information is written to generated metadata folders based on scope. Previously, this information was stored in cache. Resulting performance improvements include:

   *  Network cache size has decreased by 10 - 15%
   *  Execution time for many scenarios has been improved by 3%.

<!--- ENGCOM-7290-->

<!--- MC-31617-->

<!--- MC-33107-->

### Return Merchandise Authorizations (RMA)

<!--- MC-35984-->

*  The Returns page now works as expected after you create a shipping label for a Return Merchandise Authorization (RMA). Previously, merchants could not interact with any page elements on the Returns page after creating a shipping label for an RMA. This was a known issue for 2.4.0, and MC-35984-2.4.0-CE-composer.patch addressed this issue for Magento 2.4.0.

<!--- MC-35826-->

*  Magento now displays either an informative error message or all available products when an administrator with restricted permissions tries to create a return for products that are no longer in the assigned website scope. Previously, Magento displayed a blank page.

### Sales

<!--- MC-35675-->

*  Magento no longer assigns a status of Complete after invoicing to an order that requires zero payment.

<!--- MC-35888-->

*  The New Shipment email generated by the REST API now contains the same shipping and customer information as shipments that are created manually from the Admin. Previously, this email did not contain the customer name, tracking information, products ordered, and other order information.

<!--- MC-35837-->

*  Guest user names are now visible as expected in invoice- and shipment-related emails when the emails are loaded or customized from the Admin.

<!--- MC-35707-->

*  The PDF invoice is now translated into the language of the store view where the order has been placed. Previously, the PDF invoice was translated in the language of the Admin.

<!--- MC-35858-->

*  You can now issue a refund as expected from the credit memo page. [GitHub-29014](https://github.com/magento/magento2/issues/29014)

<!--- MC-35353-->

*  Localised region names that are displayed on the storefront Order page are now correctly translated. Previously, the region name was not based on the specified locale unless it was edited in the Admin.

<!--- MC-35633-->

### Search

<!--- MC-31304-->

*  You can now search for products by attribute from the Admin Customer view using QuickSearch. Previously, an exception occurred on the catalog search result page.

<!--- MC-32518-->

*  Magento now displays configurable products on the category page as expected after you add a product attribute.

<!--- MC-33952-->

*  Elasticsearch results now include the correct values for each storeview’s attribute options. If a Dropdown or Multiple Select attribute has a different option value in the non-default store view than in the default storeview, Elasticsearch now indexes that value or returns the product with that value in the results. Previously, Elasticsearch did not index that value or return the product with that value in the results.

<!--- MC-35013-->

*  Searching by SKU now works as expected in advanced search with Elasticsearch 6. Previously, when you tried to search by SKU, Magento displayed this error message: `We can't find any items matching these search criteria. Modify your search`.

<!--- ENGCOM-7222-->

<!--- ENGCOM-7917-->

### Shipping

<!--- MC-35955-->

*  Customers can now successfully remove reward points on the order review page of the checkout workflow when checking out with multiple addresses. Previously, Magento threw a `404 Not Found` error when a customer clicked the **Remove** button to remove points for any address. This was a known issue in Magento 2.4.0.

<!--- MC-33737-->

*  Magento now displays shipping rates in the correct currency in the checkout workflow for orders specifying FedEx as the shipping method.

<!--- MC-33267-->

*  Multi-page PDFs of shipping labels for orders shipped by UPS now display the correct count.

<!--- MC-35514-->

*  Problems with the JavaScript components of the Create Packages window have been resolved. Previously, Magento did not display the **Create Shipping Label** checkbox on this window, and you could not create a shipping label for an existing order.

### Sitemap

<!--- ENGCOM-7924-->

<!--- MC-34617-->

*  Encoded values are now correctly escaped in the `sitemap.xml` file. Previously, when you included encoded characters in a product name or image title, the generated sitemap was invalid.

### Staging

<!--- MC-36458-->

*  The **Set Product as New** attribute label now appears as expected on a product’s detail and scheduled update pages.

<!--- MC-34484-->

*  You can now successfully preview the staging schedule for a CMS block. Previously, Magento threw a fatal error.

<!--- MC-33789-->

*  You can now access the CMS Preview page when editing a CMS page with a scheduled update and re-assigning it from the default store to another store. Previously, Magento threw a 404 error when you clicked on the preview link.

<!--- MC-33572-->

*  You can now use POST `/V1/products/special-price` to update a product’s special price without specifying `price_from` and `price_to` parameter values. Previously, the Special Price API only worked with schedule updates, and if these parameters were empty, Magento returned this error: `The Start Time for Future Update needs to be selected. Select and try again`.

### Store

<!--- MC-35853-->

*  Deleting a previously created store view no longer results in an error in deployments with a split database configuration. Previously, Magento threw an exception.

<!--- MC-32634-->

### Swatches

<!--- ENGCOM-7845-->

<!--- MC-33147-->

*  Magento now displays tier prices as expected for configurable product variations.

### Tax

<!--- MC-36049-->

*  Magento no longer displays a fixed product tax attribute on the storefront for a product after a merchant has unassigned it from the product’s attribute set.

### Theme

<!--- MC-34397-->

*  Themes that are added in User Agent Rules are now affected as expected when you run `bin/magento catalog:images:resize`. Previously, only themes that were assigned to stores were affected when `bin/magento catalog:images:resize` was run.

### UI

<!--- MC-36260-->

*  Fixed misalignment of the cursor in the Invoice Comments text area of the invoice associated with an order you have selected from Admin **Sales** > **Orders**.

<!--- MC-36044-->

*  The Create New Order page now displays **Add Products By SKU** and **Add Products** buttons as expected.

<!--- MC-35974-->

*  Magento now displays the Edit Review page properly when a Product Rating is available for the selected product.

<!--- MC-35475-->

*  Magento now correctly displays the Admin customer edit page on an iPhone running Safari.

<!--- MC-35370-->

*  Corrected unnecessary scrolling on the Create New Order page.

<!--- MC-35345-->

*  Directly clicking on the **Export Tax Rates** button of the Add New Tax Rule page ( **Stores**  >  **Tax Rules**) now downloads the `tax_rates.csv` file as expected. Previously, merchants had to click on the edge of the **Export Tax Rates** button. This was a known issue in Magento 2.4.0.

<!--- MC-35313-->

*  The **Add selections to my cart** button on the bottom of the shopping cart now works as expected. This was a known issue in Magento 2.4.0.

<!--- MC-35296-->

*  The **Refresh** button of the **Recently Viewed Products** section of the Customer's Activities page now works as expected. Previously, when you clicked **Refresh**, the product list was not refreshed, and the page scrolled.

<!--- MC-35412-->

*  Magento now correctly displays the calendar icon used for selecting a customer’s date of birth on the Conditions tab of **Customers** > **Segments** > **Add Segment**.

<!--- MC-35658-->

*  The checkout summary section of the checkout workflow no longer flickers when the customer scrolls through this page on Internet Explorer 11.x.

<!--- MC-34602-->

*  Magento now correctly displays the Order by SKU widget on the storefront Category page. Previously, the HTML code for this widget was not rendered, and Magento did not display the **Load a list of SKUs** link.

<!--- ENGCOM-7264-->

<!--- ENGCOM-7575-->

<!--- ENGCOM-7507-->

<!--- ENGCOM-7578-->

<!--- ENGCOM-7579-->

<!--- ENGCOM-7579-->

<!--- ENGCOM-7456-->

<!--- ENGCOM-7285-->

<!--- ENGCOM-7631-->

<!--- ENGCOM-7010-->

<!--- ENGCOM-7244-->

<!--- ENGCOM-7770-->

<!--- ENGCOM-7619-->

<!--- ENGCOM-7873-->

<!--- ENGCOM-7639-->

<!--- ENGCOM-7156-->

<!--- ENGCOM-7981-->

<!--- ENGCOM-7911-->

<!--- ENGCOM-8007-->

<!--- ENGCOM-7992-->

<!--- ENGCOM-7967-->

<!--- ENGCOM-8015-->

### URL rewrites

<!--- MC-34483-->

*  You can now successfully preview the staging schedule for a CMS block. Previously, Magento threw a fatal error.

<!--- MC-33028-->

*  Magento now preserves existing catalog URL rewrites as expected when a store view is assigned to a different store. Previously, Magento deleted the store-specific URL rewrites.

### Vault

<!--- MC-34674-->

*  Magento no longer saves credit card numbers when the **Save for later use** checkbox on the payment section of the checkout workflow is not selected.

### Visual Merchandiser

<!--- MC-35574-->

*  Magento now displays source stock instead of the default product stock when you sort products in Visual Merchandiser and Inventory is enabled.

### Web API framework

<!--- ENGCOM-7618-->

<!--- ENGCOM-7709-->

<!--- ENGCOM-7665-->

<!--- ENGCOM-7612-->

<!--- ENGCOM-7785-->

<!--- ENGCOM-7715-->

<!--- ENGCOM-7829-->

<!--- ENGCOM-7611-->

<!--- MC-36419-->

<!--- MC-36084-->

*  Invoices created using the REST API now include gift card information similar to invoices that were created using the Admin. Previously, using POST `\{host}/rest/default/V1/order/3/invoice` to invoice the order did not display the gift card code or gift card amount applied.

<!--- MC-35838-->

*  Merchants with multiple websites can now use the REST API to create and update products while preserving  image and image-role inheritance. Previously, when a merchant used the REST API to create and update products, and a product was updated for store view, the default image roles were loaded and saved for that store view. As a result, the store-view image roles stopped inheriting from the default scope after update.

<!--- MC-36419-->

*  An unscoped integration user account can now access a resource through the REST API when resource permissions allow access.

<!--- MC-35975-->

### Website Restrictions

<!--- MC-32366-->

*  Enabling Website Restriction no longer blocks Varnish ESI requests for customers logged in as guest. Previously, these guests could not access the home page main menu.

<!--- MC-32369-->

*  Magento now loads the product home page as expected when website restrictions are enabled.

### Wish list

<!--- MC-35810-->

*  You can now use the wish list search feature to find a product in a public wish list in deployments where support for multiple wish lists is enabled. Previously, after a customer used the wish list search to find a product, selecting it, and clicking **Add to cart**, Magento did not add the product to the cart and displayed this error: `Invalid Form Key. Please refresh the page`.

<!--- MC-35622-->

*  Customers can now change the quantity of a product in a wish list from the wish list itself. Previously, Magento did not update the product quantity and did not display a message.

<!--- MC-35618-->

*  Customers can now change the quantity of a grouped product in a wish list from the wish list itself. Previously, Magento did not update the product quantity or display a message.

<!--- MC-34408-->

*  The storefront Category page now displays the Wish List search widget as expected.

<!--- ENGCOM-7580-->

<!--- ENGCOM-7561-->

<!--- ENGCOM-7660-->

<!--- ENGCOM-7674-->

<!--- ENGCOM-7675-->

<!--- ENGCOM-7564-->

<!--- ENGCOM-7717-->

<!--- MC-36250-->

*  Administrators can now configure a configurable product that has been added by a customer to a wish list from a non-default store. Previously, when the customer had also added the configurable product from a non-default store, Magento threw an error.

## Community contributions

We are grateful to the wider Magento community and would like to acknowledge their contributions to this release. Check out the following ways you can learn about the community contributions to our current releases:

*  If a community member has provided a fix for this release, we identify the fix in the Fixed Issue section of these notes with the phrase, "*Fix provided by community member*".

*  The Magento Community Engineering team [Magento Contributors](https://magento.com/magento-contributors) maintains a list of top contributing individuals and partners by month, quarter, and year. From that Contributors page, you can follow links to their merged PRs on GitHub.

### Partner contributions

The following table highlights contributions made by Partners. This table lists the Partner who contributed the pull request, the external pull request, and the GitHub issue number associated with it (if available).

{% include release-notes/engcomm-2-4-1-partner.md %}

### Individual contributor contributions

The following table identifies contributions from our community members. This table lists the external pull requests, the GitHub issue number associated with it (if available), and the community member who contributed the pull request.

{% include release-notes/engcomm-2-4-1-issues.md %}

### System requirements

Our technology stack is built on PHP and MySQL. For more information, see [System Requirements]({{site.baseurl}}/system-requirements.html).

### Installation and upgrade instructions

You can install Magento Commerce 2.4.1 using Composer.

## Migration tool kits

The Data Migration Tool helps transfer existing Magento 1.x store data to Magento 2.x. This command-line interface includes verification, progress tracking, logging, and testing functions. For installation instructions, see [Install the Data Migration Tool]({{page.baseurl}}/migration/migration-tool-install.html). Consider exploring or contributing to the [Magento Data Migration repository](https://github.com/magento/data-migration-tool).

The [Code Migration Toolkit](https://github.com/magento/code-migration) helps transfer existing Magento 1.x store extensions and customizations to Magento 2.x. The command-line interface includes scripts for converting Magento 1.x modules and layouts.