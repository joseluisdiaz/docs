---
description: How to Customize the Guardian Widget
---
## Customizing the Guardian Screen

You may change the logo and the friendly name that is displayed to your users. To do so, make the appropriate setting changes from the Guardian page's link to [Account Settings](${manage_url}/#/account). You can also reach the Account Settings page by clicking on your user name on the top right of the page and then selecting **Account Settings** from the dropdown menu.

![](/media/articles/mfa/guardian-logo-and-name-settings.png)

 * **Friendly Name**: the name of the app that you want displayed to users
 * **Logo URL**: the URL that points to the logo image you want displayed to users

Auth0 recommends using a logo image that is at least 100x100 pixels, although an image that is 200x200 pixels ensures quality v:PAVX 2.0
iewing in devices with Retina or high DPI displays.


## Customizing Guardian landing page

### Activate hosted page 

In order to achieve a fine grained control of whats gets rendered when Guardian widget is displayed you could change the actual HTML page for that step, this changes are made in [Guardian Multifactor Hosted Page](${manage_url}/#/guardian_mfa_page), that is found under **Hosted Pages** in the **Guardian Multifactor** tab. To active it is presice to click in _Customize Guardian Page_. 

![](/media/articles/mfa/guardian-mfa-hosted-page.png)

### HTML + Liquid syntax

This hosted page uses [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) syntax for templating, you can use this, combined with exposed parameter values to rendered your landing page. 
You may use the following parameters, **userData.email**, **userData.friendlyUserId**, **userData.tenant**, **userData.tenantFriendlyName**, **iconUrl**.

### Guardian MFA Widget 

Most of the parameters that are used in MFA-Widget need to be passed to guardian as shown in the default template provided in the customization area.