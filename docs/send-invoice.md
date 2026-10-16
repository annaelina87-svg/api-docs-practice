<h1>Reference</h1>
<h3>POST/v2/invoices/{invoice_id}/send</h3>  
<body> Sends a finalized invoice to a specified email. Safe to retry. The rate limit is 10 requests per minute.

Uses Bearer token authentication and JSON. </body>

 <h4>Path parameters</h4>


| Name | Type | Is required? | Description |
|--------------|:-------------:|:---------------:|---------|
| invoice_id | string  | yes | The ID of the invoice. |


<h4>Request parameters</h4>


| Name | Type | Is required? | Description |
|--------------|:-------------:|:---------------:|---------|
| recepient_email | string  | yes | An email used for sending the invoice. |
| message | string | no | A message sent in the email. |
| send_copy_to_self | boolean | TBD | TBD |
 
<h5> Example request </h5> 



```js
POST /v2/invoices/{invoice_id}/send
Authorization: Bearer <token>
Content-Type: application/json

{
  "recipient_email": "client@example.com",
  "message": "Please find your invoice attached.",
  "send_copy_to_self": true
}
```
<h4> Response fields</h4>


| Name | Possible values | Description |
|--------------|:-------------:|:---------------:|
| status | TBD  | A status of the request. |
| invoice_id | number | ID of the requested invoice. |
| sent_at | date & time | TBD |
| delivery_id | number | TBD |
 
<h5> Example response </h5> 



```js
{
  "status": "queued",
  "invoice_id": "inv_8f3a",
  "sent_at": "2026-03-14T09:30:00Z",
  "delivery_id": 48213
}
``` 409
<h4> Response codes </h4>

| Code |  Description |
|:-------------:|:---------------:|
| 200 | Successful | 
| 404 | The requested invoice does not exist. | 
| 409 | The requested invoice is not finalized. | 
| 400 | The email provided is not valid. | 

