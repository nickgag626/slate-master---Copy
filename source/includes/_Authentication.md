#Authentication
Authenticate your account by including your Application Token in the request field `X-Roam-Key`. If the credentials and token are valid, the API will return a response with the necessary session token information. This session tken can be used for accessing other APIs available within our library. 

> You will receive a session token by logging in

Ingenico uses API keys to allow access to the API. You can register a new API key at our [developer portal](http://example.com/developers).

<aside class="warning">Please replace <code>X-Roam-Key</code> in the header with your API Key.</aside>


## Log in (POST)
> URL

```javascript
[domain]/wsapi/Authentication/

```
First, you must log in to your account using your Application Token and assigned credentials. As stated earlier, this will return your session token along with other various user settings.



###Headers
> Header

```javascript

X-Roam-Key: "APP6-54a59a59ea7-7440-4f8b-ae96-ffba2e801391"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"

```
Parameter | Required | Description
--------- | ------- | -----------
X-Roam-Key | Yes | Application token that identifies the request origin. This key is unique to every client, as well as every environment. Please contact API Support (APIsupport.us@ingenico.com) to get this key. 
X-Roam-ApiVersion | Yes | Version of the API being used (e.g. 6.0.0)
X-Roam-ClientVersion | Yes | Client version which can be vary by application. This is set by developers (e.g. 1.0.0)
Content-Type | Yes | Content type e.g. application/json


> Request

```javascript
{
  "user_name":"myUserName",
  "password":"pwd123"
}

```



### Input Parameters
Pass the following values in the request body to successfully log in. 

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
user_name | String | Yes | User's unique identifier
password | String | Yes | User's password

### Response Parameters
If the request is successful, you should receive a request with the following objects defined. 

> Response:

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

Parameter | Type | Required | Description
--------- | ------- | ----------- | -----------
chainID | String | Yes | Gateway identifier for specifying processor together with store_id.
store_id | String | Yes | Gateway identifier for specifying processor together with chain_id
terminal_id | String | Yes | MCM identifier for device.
organization_id | String | Yes | The ID of the user's parent organization.
organization_type | Organization Type | Yes | The type of the user's parent organization.
processor | Processor | No | Processor Information including name, profile name, etc.
session | Session | Yes | Session info including token and expiration information.
user | user | Yes | Information for the authenticated user.
configuration |List | Yes | Last login timestamp

<aside class="success">
Remember — This will return your session token!
</aside>

## Refresh a Session (PUT)
> URL

```javascript
[domain]/wsapi/Authentication/

```
This call is used to keep a logged-in session alive. This API method will refresh a valid session and extend the Session Token expiration time. 


###Headers
> Header

```javascript

X-Roam-Key: "APP6-54a59a59ea7-7440-4f8b-ae96-ffba2e801391"
X-Roam-ApiVersion: "6.0.0"
X-Roam-ClientVersion: "1.0.0"
Content-Type: "application/json"

```
<aside class="notice">Please replace <code>X-Roam-Key</code> (in the header) with your session token returned from Login.</aside>

Parameter | Required | Description
--------- | ------- | -----------
X-Roam-Key | Yes | Application token that identifies the request origin. This key is unique to every client, as well as every environment. Please contact API Support (APIsupport.us@ingenico.com) to get this key. 
X-Roam-ApiVersion | Yes | Version of the API being used (e.g. 6.0.0)
X-Roam-ClientVersion | Yes | Client version which can be vary by application. This is set by developers (e.g. 1.0.0)
Content-Type | Yes | Content type e.g. application/json

> Request

```json


```
### Input Parameters
A request body is not needed to refresh a session. 

Parameter | Type | Required | Description
--------- | ------- | ------- | -----------
N/A | |  | 



> Response:

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

###Response Parameters
If your request is successful, you will receive a response with the following objects defined:

Parameter | Type | Required | Description
--------- | ------- | ----------- | -----------
chainID | String | Yes | Gateway identifier for specifying processor together with store_id.
store_id | String | Yes | Gateway identifier for specifying processor together with chain_id
terminal_id | String | Yes | MCM identifier for device.
organization_type | Organization Type | Yes | The type of the user's parent organization.
user | user | Yes | Information for the authenticated user.


<aside class="success">HTTP Status code: 200 OK denotes success</aside>

## Logout (DELETE)
> URL

```javascript
[domain]/wsapi/Authentication/

```
This call is used to log the user out of an active session, invalidating the existing session token. 
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


### URL Parameters

Parameter | Description
--------- | -----------
NA | NA

<aside class="success">HTTP Status code: 200 OK denotes success</aside>