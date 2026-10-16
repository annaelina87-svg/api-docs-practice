# Reference
## `POST /v2/invoices/{invoice_id}/send`   
Sends a finalized invoice to a specified email. The rate limit is 10 requests per minute.

Uses Bearer token authentication and JSON. 

 ### Path parameters 


| Name | Type | Required | Description |
|--------------|:-------------:|:---------------:|---------|
| `invoice_id` | string  | yes | The ID of the invoice. |


### Request parameters 


| Name | Type | Required | Description |
|--------------|:-------------:|:---------------:|---------|
| `recipient_email` | string  | yes | The email address the invoice is sent to. Should not contain more than 500 characters. |
| `message` | string | no | The message sent in the email. |
| `send_copy_to_self` | boolean | TBD | TBD |
 
#### Example request  

```json
POST /v2/invoices/{invoice_id}/send
Authorization: Bearer <token>
Content-Type: application/json

{
  "recipient_email": "client@example.com",
  "message": "Please find your invoice attached.",
  "send_copy_to_self": true
}
```

### Response fields 


| Name | Possible values | Description |
|--------------|:-------------:|:---------------:|
| `status` | TBD  | The status of the request. |
| `invoice_id` | number | The ID of the requested invoice. |
| `sent_at` | date & time | TBD |
| `delivery_id` | number | TBD |
 
#### Example response  


```HTML
{
  "status": "queued",
  "invoice_id": "inv_8f3a",
  "sent_at": "2026-03-14T09:30:00Z",
  "delivery_id": 48213
}
```

### Response codes 

| Code |  Description |
|:-------------:|:---------------:|
| 200 | Successful | 
| 404 | The requested invoice does not exist. | 
| 409 | The requested invoice is not finalized. | 
| 400 | The email provided is not valid. | 

