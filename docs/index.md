---
title: Ingenico mPOS SDK Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript: json
  - java: Android
  - swift: iOS



toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://www.ingenico.com/our-solutions/mobile-solutions'>Ingenico Mobile Solutions</a>

includes:
   - Payment Authorization
   - errors


search: true
---

# Introduction

The Ingenico WSAPI is a set of REST APIs designed to be consumed by API customers for interaction with our Mobile Commerce Manager. This allows customers availability to all of the features that we offer for accepting payments, as well as everything else required for end-end transaction processing

##Prerequisites
Ingenico uses API keys to allow access to the API. You can register a new API key at our [developer portal](http://example.com/developers).

<aside class="warning">Please replace <code>X-Roam-Key</code> in the header with your API Key.</aside>


> You will receive a session token by logging in

```javascript
X-Roam-Key: "APP6-54a59a59ea7-7440-4f8b-ae96-ffba2e801391"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"
```


###Headers
Parameter | Required | Description
--------- | ------- | -----------
X-Roam-Key | Yes | Application token that identifies the request origin. This key is unique to every client, as well as every environment. Please contact API Support (APIsupport.us@ingenico.com) to get this key. 
X-Roam-ApiVersion | Yes | Version of the API being used (e.g. 6.0.0)
X-Roam-ClientVersion | Yes | Client version which can be vary by application. This is set by developers (e.g. 1.0.0)
Content-Type | Yes | Content type e.g. application/json



#WSAPI Example: Authentication

## Log in
> Header

```javascript

X-Roam-Key: "APP6-54a59a59ea7-7440-4f8b-ae96-ffba2e801391"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"

```

> Request

```javascript
{
  "user_name":"myUserName",
  "password":"pwd123"
}

```


> The above command returns JSON structured like this:

```javascript
{
  "chain_id": "679",
  "store_id": "3",
  "terminal_id": "1",
  "organization_id": "8",
  "organization_type": "merchant",
  "processor": {
    "name": "Vantiv",
    "processor_profile": "vantiv_profile1",
    "date_modified": "20151113190112"
  },
  "session": {
    "expires": "20151222175141",
    "session_token": "MCM6-fd55c7-7429-447c-9918-c80162574cdb"
  },
  "user": {
    "user_name": "myUserName",
    "bill_organization": false,
    "is_admin": false,
    "is_sys_admin": false,
    "account_flags": {
      "change_email_required": false,
      "change_password_required": false,
      "change_security_questions_required": false,
      "accept_terms_and_conditions_required": false
    },
    "primary_email": "myEmail@ingenico.com",
    "security_questions": [
      {
        "answer": "testAnswer",
        "id": "13",
        "question": "What is the name of your favorite childhood friend?"
      },
      {
        "answer": "testAnswer",
        "id": "15",
        "question": "What school did you attend for sixth grade?"
      }
    ],
    "cell_phone": "1151151155",
    "first_name": "MyFirstName",
    "last_name": "MyLastName",
    "locale": "en-US",
    "middle_name_initial": "",
    "other_phone": "",
    "test_account": false,
    "title": "",
    "work_phone": "1001001000"
  },
  "configuration": {
    "account.locale.available_locales": "en_US, en_CA",
    "account.permissions.add_submerchant.merchant_portal": true,
    "account.permissions.allow_submerchants": true,
    "account.permissions.change_address": true,
    "account.permissions.change_name": true,
    "account.permissions.edit_email_receipt": true,
    "account.permissions.order_accessories.merchant_portal": true,
    "branding.theme": "default",
    "branding.theme.available_themes": "default",
    "component.access.inventory_management": true,
    "component.access.virtual_terminal": true,
    "processing.config.avs": true,
    "processing.config.avs.reverse_mismatch": false,
    "processing.config.capture_signature": "Optional",
    "processing.config.collect_geolocation": true,
    "processing.config.collect_optional_info": true,
    "processing.config.processor_profile": 1,
    "processing.config.currency": {
      "code": "USD",
      "iso": 840,
      "symbol": "$"
    },
    "processing.config.cvv": true,
    "processing.config.cvv.reverse_mismatch": false,
    "processing.config.discount": true,
    "processing.config.show_paper_receipt": true,
    "processing.config.small_ticket": "Off",
    "processing.config.small_ticket.contactless": "Off",
    "processing.config.small_ticket.contactless.max": 0,
    "processing.config.small_ticket.max": 0,
    "processing.config.tax": true,
    "processing.config.tax.default": 0,
    "processing.config.tender_types": [
      "Cash",
      "Card"
    ],
    "processing.config.tip": true,
    "processing.permissions.manual_entry": true,
    "processing.permissions.refund": true,
    "processing.permissions.refund.for_submerchant": true,
    "processing.permissions.refund.merchant_portal": true,
    "processing.permissions.refund.mobile": true,
    "processing.permissions.refund.smart_refund": true,
    "processing.permissions.void": true,
    "processing.receipt.show_tax": true,
    "security.session_timeout.mobile": 15,
    "security.account_locking.count_memory": "30",
    "security.account_locking.failed_attempts_limit": 3,
    "security.account_locking.lockout_duration": 2
  }
}

```

This call will log in to the system and return a session token, along with various user settings.



###HTTP Request

`POST http://example.com/WSAPI/Authentication`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
user_name | Yes | User name
password | Yes | Password

### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
chainID | String | xxx
store_id | String | xxx
terminal_id | String | xxx
organization_id | String | xxx
organization_type | OrganizationType | xxx
processor | Processor | xxx
session | Session | xxx
user | user | xxx
configuration |List | xxx

<aside class="success">
Remember — This will return your session token!
</aside>

## Refresh a Session

> Header

```javascript
X-Roam-Token: "MCM6-420ba742-ee06-401a-b1a6-0f6054a3e20d"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"
```

> Request

```json


```

> The above command returns JSON structured like this:

```javascript
{
  "chain_id": "679",
  "store_id": "3",
  "terminal_id": "1",
  "organization_type": "merchant",
  "session": {
    "expires": "20151222175141",
    "session_token": "MCM6-420ba742-ee06-401a-b1a6-0f6054a3e20d"
  },
  "user": {
    "user_name": "myUserName",
    "is_admin": false,
    "is_sys_admin": false,
    "test_account": false
  }
}

```
<aside class="notice">Please replace <code>X-Roam-Token</code> (in the header) with your session token returned from Login.</aside>


Keeps the logged in session alive. This API method refreshes a valid session and extends the session token expiry time. 


### HTTP Request

`PUT http://example.com/WSAPI/Authentication`

### Query Parameters

Parameter | Description
--------- | -----------
NA | NA

<aside class="success">HTTP Status code: 200 OK denotes success</aside>

## Logout

> Header

```javascript
X-Roam-Token: "MCM6-420ba742-ee06-401a-b1a6-0f6054a3e20d"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"
```

> Request

```json

```

> The above command returns this response:

```javascript
HTTP Status Code 200 OK

```

This call will log the user out of an active session, invalidating the existing session token.

### HTTP Request

`DELETE http://example.com/WSAPI/Authentication`

### URL Parameters

Parameter | Description
--------- | -----------
NA | NA

<aside class="success">HTTP Status code: 200 OK denotes success</aside>
