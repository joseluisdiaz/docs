---
description: Describes how to create an enrollment ticket from api
---

## Create an enrollment ticket

If you don't want that auth0 sent an email containing the link to enroll device new device for a particular user, you could use the following API [Create an enrollment ticket](/api/management/v2#!/Guardian/post_ticket).

To use this api, it is necessary to know the `user_id` for the user that is about to be enrolled, to do this you may use [List or search users](/api/management/v2#!/Users/#Get_users).

The response of this api will contain two properties, `ticket_id` and` ticket_url`. If you want, you can mail the content of `ticket_url` this link will start the enrollment process for `user_id`.

On the other hand, it is possible to use `ticket_id` to initialize [MFA Widget](/multifactor-authentication/administrator/customizing-widget) or [Custom Guardian Widget](https://github.com/auth0/auth0-guardian.js/tree/master/example) in your own application, no need to use auth0 hosted pages.

A concrete example:
```html
<!DOCTYPE html>
<html>
<head>
  <title>2nd Factor Authentication</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <style type="text/css">

    html, body { padding: 0; margin: 0; }

    .table {
      display: table;
      position: absolute;
      height: 100%;
      width: 100%;
      background-color: #2b2b33;
    }

    .cell {
      display: table-cell;
      vertical-align: middle;
    }

    .content {
      padding: 25px 0px 25px 0px;
      margin-left: auto;
      margin-right: auto;
      width: 280px; /* login widget width */
    }

  </style>
</head>

<body>

  <div class="table">
    <div class="cell">
      <div class="content">
        <!-- WIDGET -->
        <div class="js-mfa-container mfa-container" id="container"></div>
      </div>
    </div>
  </div>

  <script src="//cdn.auth0.com/js/mfa-widget/mfa-widget-1.2.0.min.js"></script>

  <script>
    (function() {
      return new Auth0MFAWidget({
        container: "container",

        mfaServerUrl: "${account.guardianNamespace}",
        ticket: "[TICKET_ID_FROM_API]",

        userData: {
          userId: ,
          email: "[USER_EMAIL]",
          friendlyUserId: "[USER_EMAIL]",
          tenant: "${account.tenant}"
        },
      });
    })();
  </script>
</body>
</html>

</html>
```

## Further reading

* [Restricting user-initiated enrollments](/multifactor-authentication/administrator/guardian-enrollment-email#restricting-user-initiated-enrollments)

